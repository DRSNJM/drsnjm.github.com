---
layout: post
title: "Meeting 11: Feature Selection &amp; Interface Design"
date: 2012-10-05 12:30
comments: true
categories: meetings
author: Ryan McGowan
---

## Goals

*   Determine interface design for game recommendation and expert training.
*   Determine how to convert game attributes into a vector for machine learning.
    Decide what features do we select.
*   Create consensus on terminology used for the machine learning component.

## Discussion

At this point, there are two interfaces that need to be designed.

#### Recommendation Interface

The first interface is the users normal route to interact with our system. It is
the recommendation interface. It takes in some user specified attributes and
returns a list of recommendations.

Since many attributes that a user may specify will not be used in every query we
do not want to clutter up the page with input fields. This sends the wrong
message about fields being optional (or at least makes it harder to indicate),
it is ugly and it is distracting resulting in an interface the user will not
enjoy using. This we want a way to allow the user to opt into filling out parts
of the form (or select sub-forms).  Chris came up with two ideas for this. Both
ideas simply provide a graphical way for the user to indicate which attributes
they want to specify.

1.  Accordion -- Display each attribute as a section in the accordion. Allow the
    user to open multiple sections.  An option section indicates that the user
    will be filling in its fields.
2.  Sidebar Buttons -- Instead of unrolling sections, the user would hit buttons
    in the sidebar describe the attributes he or she wants to filter on.  Each
    button would be stateful (i.e. buttons toggle between a pressed and
    unpressed state). When pressed, a form appears in the main column of the
    page for that attribute. Multilple pressed buttons means multiple forms.

In general, the team gravitated toward the sidebar idea.  It makes the
distinction between used and unused forms clearer.

#### Expert Interface

The second interface will be used to train SiGMa (Similar Game Machine) which is
this projects machine learning component.  We spent a while discussing the
proper terminology to describe the data we are looking for.  We decided that the
term *similar* is not exactly what we want. Instead we are trying to find a
relationship like *"given game A how good of a recommendation is game B"*.  Our
interface will reflect this, but there are no plans to change the name of the
library.

The original interface proposed putting two games in front of the expert and a
slider. The expert would then manipulate the slider to describe how *similar*
the two games are. Besides changing the terminology used here from "how similar
are these two games" to "how good of a recommendation is game *A* if someone
likes game *B*" we also want to change the layout.  Alex made the point that an
expert might not know one of the two games we are asking them to prepare.
Providing a skip feature would work, but it might mean the expert does a lot of
skipping if they know 100 games out of the 1000 we are using in the system it
could take awhile to find a pair of games that they know both of.


## Results

*   Decided on two discussed interface designs.

## Outgoing Responsibilities

*   David is to work on creating a tracer-bullet implementation of the first
    interface.
*   Chris is to work on creating a tracer-bullet implementation of the second
    interface.

## Attendance

-   Ryan McGowan (scribe)
-   Chris Powers
-   David Albert
-   Alex Burkhart

## Location

Thompson Café.
