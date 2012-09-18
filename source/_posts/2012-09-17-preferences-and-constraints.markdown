---
layout: post
title: "Preferences and Constraints"
date: 2012-09-17 17:42
comments: true
categories: blog design
author: Chris Powers
---

The types of input that the user will be providing through the webpage 
interface can be broken down into two categories: preferences and constraints. 
Preferences match the user's desired characterics of a game, whereas 
constraints match rigid conditions of the game.

Preferences include things like:

*	Mechanics
*	Systems
*	Themes
*	Turn system
*	Skill vs. luck base
*	Cooperative vs. competative

Constraints include things like:

*	Number of players
*	Time to play

In fact, that constraints list may be comprehensive.

Constraints are easy; there's no such thing as a mostly matched constraint. 
All they need is a straightforward filter. Simply remove games that don't 
match these constraints from consideration. There's potential for efficiency 
increase if filtering is done properly before the recommendation engine parses 
the preferences. Preferences, on the other hand, are accurate to some degree, 
rather than being a boolean match. We may display a game that matches *most* 
of the mechanics, or is *close enough* to the user's skill vs. luck base, 
even though it wasn't exactly what they were searching for.

The other significant aspect of preferences is that they can (and should) 
incorporate some weighting system on the inputs. A user may not care what 
the themes of the game are, and they may only partially care what the turn 
system is like. A true expert could take such things into consideration, and, 
therefore, so should our expert system.