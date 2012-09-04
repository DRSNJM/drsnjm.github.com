---
layout: post
title: "Proposal: Writing Level Classification System"
date: 2012-09-03 23:18
comments: true
categories: blog proposal
author: David Albert
---

An additional problem that had the potential to provide an interesting 
challenge was that of evaluating the relative reading level of a sample of text.

## 1. The Problem

While many databases exist that rate the reading level on various scales, 
whether it is by grade level or on some other numeric scale, there is a lack of
tools to dynamically evaluate the complexity of an arbitary piece of text that
could be sourced from an article, website, book, or many others. An application
could be developed that would allow a user to paste a sample of a text into an
input field, and then return a numeric rating or educational level corresponding
to that text. This way, educators would have a reliable method for determining
whether a piece of writing was appropriate in terms of difficulty for that age
level. 

The system would need to take in several criteria as input, such as the level of
difficulty of the vocabulary used and the complexity of the sentence structures
found in the text. These values could then be input into a rule-based system to 
determine the final level of that text. 

To expand the project, additional machine learning and AI concepts could be 
used. Natural Language Processing would be necessary to acurately handle and 
evaluate the sentence structure of the text among other issues. Categorization 
methods such as clustering could used to compare texts to others with known,
established values, or a machine learning system such as a neural network could
be trained against a large database of texts with known values.

## 2. Expert Sources

As a team we discussed, and even briefly described this project to a few of 
our family and friends who are experts in this area, including elementary and 
high school teachers, as well as those with degrees in English. Additional 
experts who would be necessary to the completion of the project would likely 
come from an Ohio State department such as Education or Linguistics. 

## 3. Our Motivation

As a group, this project was initially appealing because it provided a flexible
and daunting challenge. The problem has a somewhat subjectively defined 
solution, and yet, if it were to work successfully it could provide a very
useful tool for educators. Additionally, it allows a very convenient segue into
other AI areas of interest such as Natural Language Processing and text 
categorization. 

## 4. Details

Upon researching the project further, it became apparent that a large portion of
what would make this project challenging was finding accurate and reliable 
knowledge bases, beyond our experts, to help define the behavior of the system.
It would be necessary to have access to large amounts of texts, possibly by 
scraping sites like Google Books in conjunction with an existing database such
as that found at [AR BookFinder](http://www.arbookfind.com/). Additional 
challenges arise from the subjectivity of rating a concept like reading level; 
our experts would need to provide tangible feedback on the "correctness" of a 
nebulous concept. 