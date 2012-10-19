---
layout: post
title: "Similarity Engine Design and Machine Learning Tools"
date: 2012-10-19 14:50
comments: true
categories: blog
author: David Albert
---

My reponsibilities for Timebox #3 have primarily revolved around the machine learning extension to our project. After the expert interviews and discussion with potential users that took place during this timebox, it was decided that a search that provides recommended games based on some individual game that a user had enjoyed playing would be very useful and should be surfaced as a main feaure of the application, giving greater weight to this portion of the project. Elaborating on my [previous post on the topic](/blog/2012/09/21/similarity-engine/), I will be discussing some of the design and implementation decisions we have made.

## Creating a Training Set

One of the challenges of developing a machine learning system, in our case, is having a reliable and sufficiently large training set to use to train the machine implementations we decide to use. This responsibility will fall on our experts and other experienced members of CABS. The number of games in our current input space is currently at 1000, and may be expanded in the future. Since his experts have to be able to rate games in terms of each other, we decided that an interface that randomly selects a set of ~16 games, and then asks which of those games the user is familiar with, would result in much more efficient training. These selections would then be passed to the game comparison screen, described previously, in which the users selects on a sliding scale how much they would recommend the second game based on someone enjoying the first. 

Some of the issues that arise from this system include the potential for multiple experts to rate the same pair of games. It is because of this, and also the fact that we dont want experts to be presented the same game pair more than once, that it is necessary to keep track of which training patterns belong to which expert. When it comes time to actually train the system, any duplicates will be averaged together to create the final training set. 

## Input Data

Another step in implementing the system is to produce a set of input data that can be fed through the network. Currently, a record for a single game in the database looks like the following:

    {
      "_id" : ObjectId("507ddc8538ef1f102b000001"),
      "bgg_id" : 12002,
      "name" : "Jambo",
      "thumbnail" : "http://cf.geekdo-images.com/images/pic1244694_t.jpg",
      "image" : "http://cf.geekdo-images.com/images/pic1244694.jpg",
      "min_players" : 2,
      "max_players" : 2,
      "min_age" : 12,
      "length" : 45,
      "year_published" : 2004,
      "rating_average" : 7.13898,
      "rating_bayes_average" : 7.01279,
      "rating_std_dev" : 1.19381,
      "rating_median" : 0,
      "weight_average" : 2.0779,
      "weight_num" : 693,
      "rank" : 233,
      "tags" : [
        {
          "bgg_id" : 1002,
          "subtype" : "category",
          "value" : "Card Game"
        }
        
        ...

      },
      "suggested_age" : {
        "2" : 0,
        "3" : 0,
        "4" : 0,
        "5" : 0,
        "6" : 1,
        "8" : 2,
        "10" : 14,
        "12" : 8,
        "14" : 2,
        "16" : 0,
        "18" : 0,
        "21 and up" : 0
      }
    }

However, in order to appropriate input for a machine learning implementation, the input must be a vector of numerical values, so I have begun to write a map function to perform this conversion, which can be seen [here](https://github.com/DRSNJM/board-ultimatum/blob/nnet/src/board_ultimatum/engine/vector-convert.clj). The output for the game then looks like the following:

    [0.0075 0.25 0.25 0.6666666666666666 0.233 0.3465]

One interesting issue with our set of data is the possibility of having a very large input vector. Ryan and I have discussed this issue and have been researching techniques such as [principal component analysis](http://en.wikipedia.org/wiki/Principal_component_analysis), among others, as a possible solution to reduce the number of dimensions of our input. The primary concern is training performance, however, I have not yet had the chance to do any sort of dummy training to get an idea of what the limitations are going to be. 

## Machine Learning

Initially we had discussed using [Weka](http://www.cs.waikato.ac.nz/ml/weka/) as our machine learning library, however, after looking into the documentation, it seemed that the neural nets and other features were primarily geared towards being used as classifiers. The domain for our problem falls more into function approximation, as we want to be able to return and train with values in a continuous range, rather than a discrete one. 

After looking at my options, I decided to go with [Encog](http://www.heatonresearch.com/encog). Encog has a repuation for being mature and rather optimized in terms of performance. It also has a well-documented Clojure wrapper, [Enclog](https://github.com/jimpil/enclog). Encog offers a variety of network types as well as training algorithms that I will need to experiment with to determine what approach is most appropriate for our input data. 

## Returning the Results 

In order to quickly return the values generated by the network, we went ahead and set up a [Redis](http://redis.io/) instance that is hooked to our Heroku account. We will be using the [sorted sets](http://redis.io/commands#sorted_set) data structure to hold the results. The sorted set in redis takes input in the following format:

    key score member

In our situation, the data we will be inputting will look like the following:

    GameID-A similiarty-value GameID-B

This way, we will be able to very efficiently query what games, given some game A, have a similarity-value in a certain range. The [zrevrange function](http://redis.io/commands/zrevrange) will most likely be the most appropriate for making these queries. Once the Game ID's have been retrieved, the normal game database can then be queried to provide full details on each game. 