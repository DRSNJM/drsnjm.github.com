---
layout: post
title: "Designing the Scoring Engine"
date: 2012-10-30 18:03
comments: true
categories: blog design
author: Chris Powers
---

In [a previous post](/blog/2012/09/17/preferences-and-constraints/), I 
discussed the differences between filtering on constraints and scoring on 
preferences. As of the last timebox, filtering on game length was implemented 
(that is, using the interface, a user could return games of only certain 
lengths). For this timebox, I completed the filtering step on the only other 
constraint that needs to be filtered on, the number of players.

That is the easy part. Scoring games can get very tricky. At the highest 
level, it's very intuitive; you simply compare the user preferences to the 
game attributes and sum up scores for each match. The most pertinent question 
is, what will the numerical score values be based on? Will they be 
normalized? To answer the question of normalization, there is no need to 
normalize the scores for each match. The only place the scores will be used 
is in the ordering of the games presented to the user. In other words, the 
scores only need be relative.

What defines a match? If we only considered matches as the user's preference 
being exactly the same as the game's attribute, and all else won't earn you 
any score, then our job as programmers would be fairly easy. However, the 
fact of that matter is that many games may have *partial* matches; they match 
to some degree. For example, if a user indicates that they prefer a light 
game, we may want to give some "full" score to all light games, but maybe 75% 
of the points if the game is medium light, 45% if medium, and 10% if medium 
heavy. Unforunately, this implies that the scoring functions need to be 
written for each attribute individually, as the degree to which an attribute 
matches a preference is dependant upon the attribute.

The final question is, where do we get the scores? This brings us back to the 
original goal of this project: to emulate an expert in the field of board 
game recommendations. We don't need to come up with the scores ourselves; we 
need to get experts to tell use what the scores on the attributes ought to be.
 In the future, this will be important information to extract from our experts.

The last thing to consider is that we will be adding explanations on scores 
for display on the results page. This means that as each match is made, a 
corresponding string must be written or generated that describes what was 
matched and how much it affected the score. We can simply maintain a running 
list of explanations alongside the score to pass back from the game engine.