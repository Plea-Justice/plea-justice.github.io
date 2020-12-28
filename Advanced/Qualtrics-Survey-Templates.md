---
layout: page
title: Qualtrics Survey Templates
permalink: /simulation/qualtrics-survey-templates
nav_order: 1
parent: Simulation
---
# Different Template Types

Currently there are two basic templates for researchers to use:

1. Single Scenario
2. Double Scenario

Both templates will require similar configuration from the researcher looking to use the software, however the double scenario is considerably more complicated and bug-prone. There is an alternate solution, such as a separate randomization page, to avoid needing to use the Double Scenario template altogether.

# Researcher's Setup Tasks

The survey flow is somewhat unintuitive. However, groups have been added throughout to make each working part of the flow as clear as possible. Here is what a researcher will need to do to fully set up the survey flow for use with their study:

### Create Questions.
>Researchers can create questions as usual using the tools given by Qualtrics.

### Adding Questions to Survey Flow.
>The survey flow is has groups to signify where to place demographics/pre-simulation questions, general post-simulation questions, and post-simulation questions specific to those who accepted or rejected the plea deal.

<img src="/img/survey1.png" align="center" alt="Pre-Simulation Question Block">
<img src="/img/survey2.png" align="center" alt="Post-Simulation Question Block">

### Editing the Experimental Condition Randomizer.
>Researchers must edit the block that generates the experimental condition for each participant to match the number of experimental conditions created in the script editor UI.<br>
>Here, the block is randomizing a number between 1 and 3.

<img src="/img/survey3.png" align="center" alt="Experimental Condition Generator">

### Updating the Simulation URL
>Researchers must replace the highlighted text with the domain that is hosting the simulation.<br>

<img src="/img/survey4.png" align="center" alt="Simulation URL Pre-Edit">

>Here is an example where the simulation is hosted at *live.pleajustice.org/study1*

<img src="/img/survey5.png" align="center" alt="Simulation URL Post-Edit">