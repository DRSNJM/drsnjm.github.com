---
layout: post
title: "Developing a Board Game Recommendation Engine"
date: 2012-09-09 19:34
comments: true
categories: blog
author: Chris Powers
---

Surprise! None of us on the team have developed a recommendation engine before! This whole experience is entirely new to us. We're not following any guidebook or teacher directions on how to throw this system together. What this means for us as developers, is that we have to work hard, early on, to ensure that the design of our engine is sensical and efficient. The system components and their interactions must be airtight, or else we risk wasting energy on code that won't make the final cut. It's essential that the engine solves a problem that we can identify, and that the system is built from start to finish to solve this problem.

What is the purpose of a board game recommendation engine? It's easy to think, *to recommend board games*, and skip over this train of thought. For any board game enthusiast with a sizeable collection, choosing a game to play is a challenge. Even with a type of game in mind, with known time constraints and number of players, the person will still often be unsure of what his set of options are. Add into this mix the preferences of several other potential players, and suddenly the group's eagerness to jump into a game is pacified by the difficulty of the decision of what to play. It is this very scenario to which we hope to provide a solution. So what is the purpose of a board game recommendation engine? In our case, it is to take whatever factors a board game enthusiast considers when selecting a game to play, quantify them, and allow the user to send them as input into our recommendation engine. The output will be a list of board games that match the preferences and constraints that the user provided as input, in order of expected relevance to the query.

That begets the question of what preferences and constraints the user may input into the system in order to receive recommendations. That question alone is hugely significant and difficult, so it will be discussed in a future post.