---
layout: post
title: "Variety in Recommendation Queries"
date: 2012-09-11 20:03
comments: true
categories: blog design
author: Chris Powers
---

**Note:** This post was heavily inspired from the system design that Ryan, Alex, and I [talked about earlier](/blog/2012/09/07/meeting-7/).

Our team has always understood that we would need some contained system that 
gives game recommendations based on preferences (i.e. the recommendation 
system core), but this is only half the work. There's more to do in storing 
the data, and providing webpage interfaces for sending queries to the core 
and displaying results. While this bare-bones system should be sufficient to 
meet our initial requirements, there's still more to add to the system, as we 
discovered at our meeting. In particular, there's a this system doesn't 
provide a feature that an expert could provide to a user: variety. Many avid 
players are interested in trying something new, even if it is further away 
from their preferences. We want to provide an option to the user to request 
variety in the search.

Unfortunately, variety is a loosely defined preference in a board game query. 
The user can select that they want a strategy game or a 4 person game, and we 
know exactly what they mean. If the user selects that they want *variety*, 
then suddenly we have a huge problem. This isn't some attribute of a game that 
we just match. It's the desire to get games that *don't* match their selected 
attributes, but still will be likely fun by their standards.

The simple solution would be to just not provide this feature. But where's the 
fun and variety in that?

The other solution we talked through is to allow experts to map similar games. 
Rather than attempt to model variety ourselves, we can simply return games 
that are similar to the games the user will like, but that the user didn't 
actually search for with his input. This would involve providing a new 
interface to experts on the website so that they can map games to each other.

I drew up some flowcharts on the proposed system. When the system is 
finalized, we'll have some proper flowcharts:

![Overall system chart](/images/diagrams/Board%20Ultimatum%20Flow.jpeg)
The overall I/O of the system with the two proposed engines.
![Query process](images/diagrams/Query%20Flow.jpeg)
The flow of a recommendation query from inception to display.

Essentially, instead of returning games matched by attributes immediately, 
some of these results are then passed into the similar games engine and then 
the mixture of results are returned to the user. The filtering in the second 
chart exists to remove attributes that aren't directly relevent to user 
preferences for recommendations; that is, they are closer to constraints than 
preferences (e.g. number of players, time to play).