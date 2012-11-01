---
layout: post
title: "Data Analysis and Neural Nets"
date: 2012-10-31 18:17
comments: true
categories: blog
author: David Albert
---

## Data Conversion and Analysis

The first task that I took on during this timebox was converting the data from the board game database into numerical vectors representing each game. The source code for this script can be found [here](https://github.com/DRSNJM/board-ultimatum/blob/nnet/src/board_ultimatum/engine/vector-convert.clj). There are many categories and mechanics included in this vector - its value is 1.0 if the game contains that tag and 0.0 if it does not. 

As you can tell by examining the code, the resulting vector has 100+ dimensions. For the sake of performance, I decided that this raw input was impractical for a neural net application. To solve this problem, I turned to PCA (Principal Component Analysis). PCA uses orthagonal transforms to maximize the variability of the data. By projecting my set of 1000 100+ dimensional vectors onto the first 10 principal components, I was able to reduce the dimensionality of the vectors down to ten components. The following is a graph of the data on the first two principal components. 

![PC Analysis](http://i.imgur.com/XEnty.png)

It is worthwhile to note that the outliers in the bottom right are party games that can accomodate 50+ people and are fairly unique in that regard. 

Once the data is converted, it is stored in the Mongo database.

The library I used to perform this analysis is [Incanter](http://incanter.org/) which contains much of the functionality found in R, if you are familiar with stats packages. 

## Neural Net and Engine output

The next step was to run the data through the neural net. Since the expert interface is not accessible to public users at this point, an untrained network is used. The network I used is arbitrary at this point as far as hidden layers and propogation algorithms are concerned, since there is no training data. I ran each combination of games through the network with the input as the following: [GameA Game B]. The results were then stored in another Mongo collection.

One problem that I encountered was the amount of storage that the output takes. This problem was mitigated by only storing the 50 games with the best score for each game, reducing the size by a factor of 20. All 1000 values would be calculated, then trimmed down. This would ensure that the database would never have more than ~50000 records, versus 1000000.