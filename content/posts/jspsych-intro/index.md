---
title: "Using jspsych to Create Psychology Experiments"
date: 2023-10-24T12:14:02-05:00
author: Wenxuan Zhao
tags: ['']
summary: In this post, I will synthesize my learning of the `jspsych` (and its plugins), a javascript framework for designing and implementing psychology experiments online, into step-by-step procedures.
draft: true
cover:
    image: 
    alt: 
    relative: true
---
In this post, I will synthesize my learning of the `jspsych` (and its plugins), a javascript framework for designing and implementing psychology experiments online, into step-by-step procedures. 

A sample [experiment](/jspsych/sampleExperiment.html) from [here](https://www.jspsych.org/).

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

Most of the welcome and instruction to a experiment can be described in static HTML that includes `p`, `div`, `img`, and `strong` tags. 

Also, we want participants to navigate themselves through the experiment process by for example, clicking anykey to proceed when they finish reading the prompt. 

Therefore, we can use the `plugin-html-keyboard-response` to define variables of type `jsPsychHtmlKeyboardResponse` to output html formatted stimulus and get keyboard response after they finished reading. 

Both can be treated as "trials" that should be pushed into timeline after we defined them. 

# Step 2: Create Experiment Trials

In principle, just as we could define the Welcome and the Instruction page using two variables that each creates a trial, we could create each trial using one variable. For example, for trials that uses an image stimuli, we could create a variable of type `jsPsychImageKeyboardResponse` (after we include the plugin for it), and push it to the main timeline. 

In practice, that leads to lots of code repetition, for similar trials with a slight change of parameter/stimulus require defining different variables; also, complex trials (i.e. a task, or a procedure) cannot be defined using a single variable. For example, a task 

To solve the first problem, we could use Timeline variables, and create an object that describes a *prototypical* trial.

# Step 2.5: During the Experiment

# Step 3: Post Experiment

# Step 4: Data Collection and Analysis





