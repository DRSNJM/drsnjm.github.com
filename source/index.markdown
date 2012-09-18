---
layout: page
date: 2012-09-01 11:53
comments: false
sharing: true
footer: true
author: Ryan McGowan, Chris Powers
---
# The DRSNJM

The Dinosaur Riding Scrum Ninja Jedi Masters (DRSNJM) is a team of computer
scientists studying at the Ohio State University. The team is actively building
a board game recommendation system, designed and constructed from the ground up
to emulate the expertise of a board game enthusiast using artificial
intelligence fundamentals. The system is a major capstone project at the
university that will be a fully functional and product.

---

# The Board Ultimatum

## Description

The Board Ultimatum will be a usable site, where a user can register an account
and start receiving board game recommendations based on their input and
preferences. The user will tell the system what it's looking for out of a game,
and the system will return games as results that match the user's selections.
The user can rate games, and the system will gain knowledge on what type of
games the user likes, and factor this information into the results.

## Goals

*   Build a web interface using the recommendation engine to allow users to
    decide what to play next. A user can login, search for types of games, and
    rate results.
*   Create a library behind the website to act as a recommendation engine. The
    library will take as input attributes of board games and return an ordered
    list of games that match this input. The input/output system changes over
    time as users rate and select different games.

## Design &amp; Implementation

The board ultimatum system consists of two main components, the web application
and the engine. The web app contains the engine, in fact the engine is a
dependency to it.

### The Web App

The web application itself is mostly a front-end to the engine. It takes data
input from a user, uses the engine to derive a list of games the user might
want, and delivers the list back to the user.  The front-end is split into the
following parts:

*   A web server -- Capture and format HTTP requests and responses on our host.
*   A routing to view framework -- Using [Noir](http://www.webnoir.org/) to
    declartivly create pages.
*   An API built on top of that framework -- Handle AJAX requests for
    interactive user experience.
*   An HTML generation scheme
*   Static resources -- (e.g. SASS &rarr; CSS, cljs &rarr; Javascript)


### The Engine

The engine is almost synonymous with the expert system. Not only will it contain
our rules and at least part of our facts, it will also include the code to make
inferences and decisions from them. However, the engine will also include the
explanation component and a machine learning component.


#### Facts, Decisions, Inferencing and Rules

In general, our experts provide us with rules and decisions as well as specify
what types of facts we should gather and use in our system.

Many facts will be stored in a persistent store after being gathered from
[BoardGameGeek](http://boardgamegeek.com/)'s open API which contains a multitude
of metadata.  This data includes play time, player number range and other
helpful information ([see an example
game](http://boardgamegeek.com/boardgame/25613/through-the-ages-a-story-of-civilization)).

These facts are connected by rules and decisions primarily gathered from
experts.  Sometimes these rules may be common sense (e.g. `IF NOT
between(num_players(X), min_players, max_players) THEN NOT X`) or they may be
more complex decisions (e.g. acceptable deviation in complexity is higher for
experts and beginners than it is for intermediate board gamers).


#### Components

*   Game Attribute Matching Machine (*GAMMa*) -- Rules, facts, decisions and
    inferencing engine goodness.
*   Reasoning/Explanation Framework (*Referree*) -- Keep track of how choices
    are made.
*   Similar Game Machine (*SiGMa*)-- Given a particular game list some similar
    ones.

For more information on our design see [our design blog posts](/blog/categories/design/).

## Source Code and Documentation

All of our source and documentation is available on
[github](https://github.com/DRSNJM). For direct links to our repositories see
the sidebar. Links to documentation can be found below:

#### Board Ultimatum Docs

*	[Web App](http://drsnjm.github.com/board-ultimatum)
*	[Engine](http://drsnjm.github.com/board-ultimatum-engine)
