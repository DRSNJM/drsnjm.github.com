---
layout: post
title: "Expert Interface"
date: 2012-12-12 15:29
comments: true
author: Ryan McGowan
categories: blog
---

## Purpose

Data for the similarity engine (neural network) did not come out of thin air. It
needed to be collected from our experts. The purpose of expert authentication
and the expert interface is to easily allow our experts to contribute to the
training of the neural network. The end goal is for an expert to rate each game
as similar to another one. With 1,000 games there ate 500,000 pairs (1,000
choose 2). Getting 500,000 ratings at our scale is difficult thus the neural
network is needed to expand on the ratings we have.

## Issues & Design

Our initial design was very simple. A random pair of games is selected. If the
expert is familiar with both games, they rate how similar they are. Otherwise,
he or she skips that pair. Unfortunately, most experts are not familiar with a
significant proportion of the games in our database. That means, under normal
conditions the expert would be skipping a lot.

To address this the interface was turned into a wizard with the following steps:

1.  Game Selection -- 12 random games are selected from the database. The expert
    selectis which one they are familiar.
2.  Pair Rating -- For all pair combinations of games selected on page 1 obtain
    a rating from the expert.

An expert is far more likely to be familiar with 2 or more games out of a
randomly selected twelve. Thus, less skipping is involved.

## Features

*   Do not display games the expert has not seen before.
*   Limit the number of combinations shown.
*   Do not show combinations the expert has already rated.

#### [Source Code](https://github.com/DRSNJM/board-ultimatum/blob/master/src/board_ultimatum/views/expert.clj)
