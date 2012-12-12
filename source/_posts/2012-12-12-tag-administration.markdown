---
layout: post
title: "Tag Administration"
date: 2012-12-12 17:39
comments: true
author: Alex Burkhart
categories: blog
---

## Purpose

In all the Board Game Geek data, there are a lot of different Mechanics and
Categories. Within the system they are treated identically, collectively
called Tags. Each Tag has a name along with a detailed description.

We wanted to be able to quickly modify the metadata related to the Tags quickly
and easily. We already had a webserver setup, so a simple web interface seemed
a natural way to accomplish this.

## Features

With the Tag Administration page, we were able to edit the titles and
descriptions of each tag as we see fit. We pulled all the descriptions in from
Board Game Geek with a script automatically and were able to quickly edit them
here.

We also wanted to be able to modify the weight for each Tag within the query
scoring system. I added a "Postive Influence" and "Negative Influence" field to
each Tag. By modifying the Postive Influence, an administrator is able to
change the maximum score assigned to an attribute by the query engine.
Similarly, the Negative Influence adjusts the maximum penalty when an attribute
is marked thumbs down by the user.

Lastly, we had plans to break up the giant wall of tri-state checkboxes on the
query page by grouping related Tags. A common example of this was to group all
"Theme" tags together. The administration page gave us a simple way to change
the grouping.

![Preview](/images/tag_administration.png)

You can see the final version of the Tag Administration Page 
[here](http://board-ultimatum.herokuapp.com/tags).

