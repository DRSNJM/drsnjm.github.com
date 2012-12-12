---
layout: page
date: 2012-09-01 11:53
comments: false
sharing: true
footer: true
author: Ryan McGowan, Chris Powers
---
# The Board Ultimatum

First things first, this project is finished and completely usable!

[See our finished product here!](http://board-ultimatum.herokuapp.com/recommend)
(may take a minute to load)

## Description

The Board Ultimatum is an interactive site where a user can enter their
preferences in the form of either game attributes that they like/dislike, or by
inputting a game they already enjoy, and start receiving board game
recommendations based on their input. In addition, if the user is an expert in
the area of board games, he or she may rate the quality of recommendations
between games and the system will incorporate this knowledge into future
recommendations.

## Motivation &amp; Goals

The motivation behind the project was simple: we want to eliminate guesswork
from board game selection. Often times board game players, experienced and
inexperienced alike, struggle to determine the next game to play when
confronted with a huge selection. We wanted to play the role of a
knowledgeable player who could ask them questions about games or aspects of
games they preferred in order to give relevant results.

We built this system with the intention that it would give recommendations that
were as good as recommendations from board game experts and enthusiasts. All
aspects of approach and design move towards this goal.

Some more specific goals include:

*   Build a web interface using the recommendation engine to allow users to 
	decide what to play next. A user can search for types of games based on
	a variety of attributes.
*   Create a system behind the website to act as a recommendation engine. The
    system will take as input attributes of board games and return an ordered
    list of games that match this input.
*	Create a second system that takes as input a single game and presents an
	ordered list of games that are similar to the game. The input/output system
	changes over time as users rate and select different games.

See our post, [Problem Domain and Motivation](/blog/2012/09/18/problem-domain-and-motivations/).

## Approach

Because our goal was to emulate a board game expert, our approach to the system
was to capture knowledge from experts through interviews and incorporate this =
knowledge in the system.

You can [view the experts we interviewed here.](http://localhost:4000/experts)

You can [view the interviews we conducted with the experts here.](http://localhost:4000/interviews)

You may wonder why we took the approach of using two separate systems to make
recommendations. As credit to the usefulness of interviews, it's because we
realized that experts will make recommendations based on games that a person
likes just as much as aspects of games that a person likes.

## Design

#### Overall design

The overall design of the system is summed up nicely by this flowchart:

![System Design](/images/diagrams/system-design.png)

To read more about our system design, see [all of our design posts.](/blog/categories/design/)

Here's a couple of the most significant design posts:

*   [Variety in Recommendation Queries](/blog/2012/09/11/variety-in-recommendation-queries/)
*   [Preferences and Constraints](/blog/2012/09/17/preferences-and-constraints/)
*   [Designing the Scoring Engine](/blog/2012/10/30/designing-the-scoring-engine/)

#### Webapp

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

#### Facts and rules

In general, our experts provide us with rules and decisions as well as helped
specify what types of facts we should gather and use in our system.

Our facts concerning games were the attributes of games pulled off of BGG
(see Database of games under Key Components below). In the similar games
engine, extra facts on expert recommendations were gathered through our expert
game-rating interface.

Rules differed between the systems. In the similar games engine, rules were
innate to the neural network recommendations generated based on the expert's
rules. In the attribute recommendation engine, rules were based on scoring
mechanics. Scores were applied by comparing user preferences to each game and
adding or deducting points based on how their preferences matched up to the
game. These values change depending on the attribute, but are summed to
represent the quality of the recommendation of that game as a whole.

## Key Components

See some posts on the key components of the system:

#### Database of games

Data was used from our non-human expert on board games,
[BoardGameGeek (BGG)](http://boardgamegeek.com/).
BGG has a massive collection of information on games and an API we used to pull
down this information. We imported data on the top 1000 games off of BGG into a
MongoDB database.

#### Neural network of game recommendations

*   [Data Analysis and Neural Nets](/blog/2012/10/31/data-analysis-and-neural-nets/)

#### Game preference scoring

*   [Designing the Scoring Engine](/blog/2012/10/30/designing-the-scoring-engine/)

#### Front end design and implementation

*   [Attribute Search Interface Design](/blog/2012/10/06/interface-design/)
*   [Attribute Search Interface Implementation](/blog/2012/10/16/interface-implementation/)

## Journal

[See our full blog for the content we've journaled on over the project.](/blog)

[See our meeting notes for the lowdown on what we did at each major meeting.](/meetings)

[See our commit history on github to see who contributed what code.](https://github.com/DRSNJM/board-ultimatum/commits)

## Source Code and Documentation

All of our source and documentation is available on
[github](https://github.com/DRSNJM). For direct links to our repositories see
the sidebar.

A [quick introduction to our setup
instructions](/blog/2012/12/12/development-setup/) is also available.

#### Board Ultimatum Docs

*	[Web App Docs](http://drsnjm.github.com/board-ultimatum)
