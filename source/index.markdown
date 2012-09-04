---
layout: page
date: 2012-09-01 11:53
comments: false
sharing: true
footer: true
---
# The DRSNJM

The Dinosaur Riding Scrum Ninja Jedi Masters (DRSNJM) is a team of computer scientists studying at the Ohio State University. The team is actively building a board game recommendation system, designed and constructed from the ground up to emulate the expertise of a board game enthusiast using artificial intelligence fundamentals. The system is a major capstone project at the university, but will be fully functional and useable to any 3rd party user.

---

# The Board Ultimatum

## Description

The Board Ultimatum will be a useable site, where a user can register an account and start receiving board game recommendations based on their input and preferences. The user will tell the system what it's looking for out of a game, and the system will return games as results that match the user's selections. The user can rate games, and the system will gain knowledge on what type of games the user likes, and factor this information into the results.

## Goals

*   Build a web interface using the recommendation engine to allow users to decide what to play next. A user can login, search for types of games, and rate results.
*   Create a library behind the website to act as a recommendation engine. The library will take as input attributes of board games and return an ordered list of games that match this input. The input/output system changes over time as users rate and select different games.

## Implementation

Stay tuned for implementation details once the project is underway!

## Source Code and Documentation

All of our source and documentation is open and available on [our github](https://github.com/DRSNJM).

### [board-ultimatum](https://github.com/DRSNJM/board-ultimatum)

The noir webapp (front-end) to our board game recommendation system.

*	[Read the docs](http://drsnjm.github.com/board-ultimatum)

### [board-ultimatum.engine](https://github.com/DRSNJM/board-ultimatum-engine)

The board game recommendation engine.

*	[Read the docs](http://drsnjm.github.com/board-ultimatum-engine)
