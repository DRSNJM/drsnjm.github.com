---
layout: post
title: "Attribute Search Interface Implementation"
date: 2012-10-16 13:35
comments: true
categories: design blog
author: Chris Powers
---

The most fundamental aspects of the query interface have been implemented.
Though there may be more attributes added in the future, we decided to add a
select few attributes that we believed encapsulated differing types of input we
receive from the user. In particular, we expect the user to select discrete
values for some attributes, such as number of players and time to play (in
discrete intervals), and tri-state objects that can encapsulate the user liking,
disliking, or not caring about a particular attribute. Prototypes were built to
represent these input types, and are currently present on the interface:

![Fundamental interface](/images/diagrams/fundamental-interface.jpeg)

These input types maintain hidden values in the background in order to formally
send them to the server.
