---
layout: post
title: "Design Thoughts Upon Interview with Ray"
date: 2012-09-14 17:18
comments: true
categories: blog design
author: Chris Powers
---

**Note:** This post deals with content discussed in [the first
 interview](/blog/2012/09/11/interview-1-raymond-chandler/) with Raymond 
 Chandler.
 
 Ray offered insight into the design behind board games with his expertise. 
 This isn't the same type of expertise we intend to model with the board game 
 recommendation engine (we're not building an engine that creates board games, 
 just one that *recommends* them for play), but in some respects, it's still 
 relevant to our problem domain. (It's also important to note that Ray is an 
 a zealous board game player, and so he is still a highly useful expert.)
 
 The interview writeup goes into greater detail on his explanations of board 
 game design, but he gave some good possible game attributes and other input 
 that we hadn't considered, such as the "ramp" and "tempo" of a game, and the 
 average player skill of those in the group. We discussed the possibility of a 
 "[similar games engine](/blog/2012/09/11/variety-in-recommendation-queries/)" 
 to add variety to search results with Ray. Ray didn't like the idea of 
 directly linking games, as it was demanding on experts and poorly scalable. 
 He recommended as an alternative that we link attributes across games so that 
 newly added games would be immediately integrated in the system.
 
 While what he recommended made sense, the notion of linking arbitrary 
 attributes is rather complex. An example of his proposal is to link 
 dice-rolling to card-playing systems as similar. When a new card-playing game 
 is added, no new links will need to be established; the engine will know that 
 the games are similar because of this link. If all we're to do is link 
 gameplay mechanics, then that is a reasonable approach. However, it may be 
 more effective to link arbitrary game attributes in some manner, such as 
 linking dice rolling mechanics to luck-based gameplay (in the luck vs. 
 skill attribute). The problem is that linking attributes is such a manner is 
 rather complex, especially when the only reason we began down this road was 
 to add variety to recommendations; a nice feature, but an unnecessary one.
 
 I think this thought shouldn't be accepted or rejected so quickly. It will 
 require discussion with the team at the next meeting, and potentially further 
 exploring this option in the next interview with Ray.