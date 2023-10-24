---
title: "Using jspsych to Create Psychology Experiments"
date: 2023-10-24T12:14:02-05:00
author: Wenxuan Zhao
tags: ['']
summary: 
draft: true
cover:
    image: 
    alt: 
    relative: true
---
In this post, I will synthesize my learning of the `jspsych` (and its plugins), a javascript framework for designing and implementing psychology experiments online, into step-by-step procedures.

# Step 1: Init (Pre-trials)
In `index.html`, in the `head` tag, name the experiment using the `title` tag and include the jsych, jsych stylesheet, and plugins would be used using the `script` tags. 

Then, after the `body` tag, include a `script` tag that initialize jspsych. 

`var jsPsych = initJsPsych();`

Also, we need to initialize the timeline variable which would include all the trials in order (First In First Out). 

`var timeline = [];`

## Preloading Media

By preloading media we ask the participant's browser to download the media ahead of needing it, so that when we do need to display or play it there is no lag from needing to download it.

To do that, we can use the *preload* plugin by including the script in the `head`. Then we can create a variable to store the preloaded media, which is of type `jsPsychPreload`. 

It is technically a trial, so we need to push the variable into the `timeline` variable we created. 

## Welcome and Instruction



# Step 2: Experiment Trials

## Instruction "Trials" using

