---
title: "Biased Average Position Estimates in Line and Bar Graphs: Underestimation, Overestimation, and Perceptual Pull"
date: 2023-11-04T18:35:11-05:00
author: Wenxuan Zhao
tags: ['APAD']
summary: 
draft: true
cover:
    image: 
    alt: 
    relative: true
---
## Introduction
Preceptual psychology reveals that preception of visual information can be systematically influenced by/biased based on **context** and **recent history**. This is also true in data visualization. 

Position in past literature is believed to be the most precise channel to encode information. In this paper, they will show systematica biases in perception of data using positional encodings.

## Perceptual Biases
- lower-levels biases: size, features that include hue, brightness, orientation, and position perception 
- biases mechanisms: context (background, neighbor, categorical boundary, salient points), adaptation
    - Positions are encoded somewhat categorically (similar to color), so that changes to a category boundary are easier to detect, compared to equally distant changes that do not cross a category boundary
    - he position memory of a briefly presented object can be biased by context or nearby salient points in the display. Memory for the position of an object can be biased toward the average position of an associated group of objects.

## Cognitive Biases
- higher level biases: estimation, decision, judgement
- biases mechanisms: recent history: *priming*, and context
    - anchoring effect: uncertain target estimates can be strongly biased by other provided values, even if they are objectively irrelevant.
    - Such higher-level cognitive influences may also affect pattern perception in data visualizations
        - slope estimate
        - judgments of class separability
        - eg. viewers who saw a high-intensity title recall a steeper slope than those who saw a low-intensity title 

## Contributions 
Previous work on investigating perceptual biases has focused on biases within visualizations in a higher-level, cognitive context. 
    - how do semantics of titles, axes, or other visualization elements, or priming influence perception. 

This paper focus on potential biases found in lower-level perception of data — can people accurately perceive purely graphical information?
    - possible biases within **average position estimations**

## Study Overview

### Stimuli and procedure
The stimuli could appear at top and/or bottom. 3 means of height for both top and bottom: low, medium, high
    - determined in pilot trial by two-alternative forced choice. Following conventions from psychophysics, an ideal distance between means would have participants accurately discriminating them in at least 75% of all trials: 12 pixels for line, 5 pixels for bar in a 140 pixel display frame with average viweing distance of 47 cm.

Three experiments:
1. One line or one set of bars 
    - noisy vs uniform


