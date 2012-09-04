---
layout: post
title: "Proposal: Board Game Recommendation System"
date: 2012-09-03 21:01
comments: true
categories: blog, proposal
author: Alex Burkhart, Ryan McGowan
---

During our meetings one of our favorite topics has been a board game
recommendation system. The goal would be to have board game experts
use their vast knowledge of which games are worth playing to point new
and old players to games that fit their immediate requirements. 

## 1. The Problem

The [Columbus Area Boarding Society](http://buckeyeboardgamers.org/)
(CABS) has over 1000 board games. We aim to save them from the
paralysis of choice such a large collection brings. At any given hour
of a meeting, dozens of players will mill around in front of the
library's game cabinets and waste time not playing games.

Each group of people has various restrictions on what they will
eventually pick. Major requirements are often the Number of Players
and the Length of Gameplay. A group of 3 people is not interested in
playing a game for 12. Likewise, a group with an hour to kill is not
interested in anything taking 4 hours.

Other requirements are more varied. Genre, categorization, game
mechanics, publishing date, suggested age, or community
awards. Veteran board gamers will take all these things into
consideration in varying amounts when choosing a new game. This
analysis is very much an art, not a science. We aim to automate their
expertise build a system to take any or all of these factors into
consideration for everyone, not just experienced players.


## 2. Expert Sources

Unfortunately, even experts can make mistakes. A single expert might
not have all the knowledge necessary to make a good recommendation. We
will use our local experts at CABS to test and refine the system. With
their experience at our disposal, we can find the correct calibration
settings for how much weight we should give to qualities described
above. Pooling their collective expertise we will be able to cover a
wide range of games and their appropriate pairings.

We also have [BoardGameGeek.com](http://boardgamegeek.com) (BGG),
the single largest website covering the board gaming community. BGG
has a [free API](http://boardgamegeek.com/wiki/page/BGG_XML_API2) we
can access to download the extensive board game data. Using this, we
can import thousands of games worth of data into our database,
allowing us to focus our time on tweaking our recommendation system as
tightly as possible.


## 3. Our Motivation

We are going to integrate with the CABS library system so that we can
allow members to use our system on a day to day basis. This will
provide real value to a local community organization and its
members. We hope to be able to use the data collected from actual
usage to further tweak the system into a mind-reading, board game
recommending machine.

## 4. Details

This is a large project with a very large amount of room to expand and
become better. We will complete portions of the system each iteration
and continue to refine the recommendations it makes.

### Recommend Anything

We setup a simple interface and recommend random games from the interface.

### Recommend on Player Number and Time

### Weight by BGG Rank

### Associate Related Games by Expert Review

### Weight by BGG Categorization/Mechanics

