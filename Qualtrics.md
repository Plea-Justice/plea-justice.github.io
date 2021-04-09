---
layout: page
title:  Connecting to Qualtrics
permalink: /qualtrics
nav_order: 3
---

# Working with Qualtrics
{: .no_toc}

Participants are redirected from Qualtrics to the simulation via a custom end survey block in the survey flow. All data is passed between the simulation and Qualtrics in the URL as [query parameters](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/).

During a study, participants will be redirected from Qualtrics to the simulation and back to Qualtrics; sometimes multiple times. Most studies will proceed in the following order:

`Qualtrics Survey → Simulation → Qualtrics Survey`

In this case, we can either route participants through two separate Qualtrics surveys or have them come back to the same survey multiple times. A more complex study might have participants view more than one scenario, repeatedly redirecting between Qualtrics and a simulation.

`Qualtrics Survey → Simulation #1 → Qualtrics Survey → Simulation #2 → Qualtrics Survey`

Here we will demonstrate the first case and assume a single Qualtrics survey which participants will come back to multiple times.

1. TOC
{: toc}

## The Qualtrics Survey Flow

The participant will view the Qualtrics survey twice. Make sure _Prevent Ballot Box Stuffing_ is disabled in your Survey Options so that participants may view the survey more than once. Also disable _Save and Continue_ so that participants can be directed to the appropriate part of the survey when they return.

Design a flow similar to the following, using an embedded data variable to track whether the participant has freshly opened the survey or if they have just viewed the simulation and are returning to complete follow-up questions.

| ![Copy Survey Flow](/img/console/qualtrics_surveyflow.png) |

## Sending Participants from Qualtrics to the Simulation

Publish your scenario and open the _Active Simulation Link_ in the publish dropdown.

You will be presented with two links. The first link will take participants through the avatar customization screen before presenting the simulation. The second link will skip customization and go directly to the simulation.

| ![Copy Simulation Link](/img/console/scenario_publish.gif) |

Copy whichever link is appropriate for your study. In most cases, this will be the first link. The second link may be appropriate if participants leave the simulation and then come back to view a second scenario, having already completed avatar customization the first time.

In your Qualtrics survey, click _Customize_ on the survey end block that will send participants to the simulation. Override the default options and select _Redirect to a URL_. Paste the link into the box.

| ![Redirect to Simulation](/img/console/qualtrics_redirect.gif) |

## Controlling the Simulation

You must pass at least the randomly assigned experimental condition number as a parameter to the simulation. It is reccommended that you also pass a variable to track the number of times the participant has viewed your Qualtrics survey and a [variable to identify that participant](https://www.qualtrics.com/support/survey-platform/common-use-cases-rc/assigning-randomized-ids-to-respondents/#PipedText) and consolidate their data before analysis. To pass parameters into the simulation from Qualtrics, pass them in the [URL query string](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/).

Assign the participant's condition number to an embedded data variable in your Qualtrics survey.

| ![Assign embedded data](/img/qualtrics_querystring_data.png) |

At the custom end block in which the participant is redirected to the simulation, add to the URL a `?` followed by the variable name, `=` and then the value. To insert embedded data as a value, such as the condition number we assigned, use Qualtrics' [piped text](https://www.qualtrics.com/support/survey-platform/survey-module/editing-questions/piped-text/piped-text-overview/#PipingFromAnEmbeddedDataField) syntax.

| ![Assign embedded data](/img/qualtrics_querystring_endofsurvey.png) |
| e.g. add `?condition=${e://Field/condition}` to the URL |

Further parameters after the first should be separated by `&` instead of `?`, such as in `?condition=${e://Field/condition}&Name=${e://Field/Name}`.

All parameters passed into the simulation will also be passed unmodified back to the Qualtrics in case you wish to record them or use them in your branching logic.

## Using Piped Text in the Scenario Script

Any variables passed into the simulation via its query string can be inserted into the script in a manner similar to Qualtrics' piped text. The most common use for this feature is to reference the participant's name from within the simulation.

Advanced, multi-simulation studies may also use this feature to implement complex manipulations.

For instance, to insert the participant's name into the scrip of a dialogue scene, pass the name to the simulation in its URL. You will need to have collected the participant's name elsewhere in your survey (such as in the informed consent) and assigned it to a variable.

| ![Pass the Participant's Name](/img/console/qualtrics_queryname.png) |

Then, insert the parameter into the script of a scene in your scenario using the syntax `@Name;` or the `@` symbol followed by the name of your variable and then a semicolon.

| ![Insert Piped Text](/img/console/scene_dialogue.png) |

For more advanced manipulations, use Qualtrics' branching logic to set your piped text.

## Recieving and Recording Data in Qualtrics

Data collected within the simulation will be passed back to Qualtrics its URL in the same fashion it is passed to the simulation. This includes data such as the features selected by the participant in the avatar customizer as well as the choices they select in any question scenes.

The following table lists avatar features that can be recieved.

| URL Query Parameter | Possible Values | Explanation |
| ------------- | ------------- | ------------- |
| skin | Hex color code. | The avatar skin color selected by the participant. |
| hair | Hex color code. | The avatar hair color selected by the participant. |
| eye | Hex color code. | The avatar eye color selected by the participant. |
| outfit | Hex color code. | The avatar outfit color selected by the participant. |
| figure | Whole number. | The avatar figure selected by the participant. |
| hairstyle | Whole number. | The avatar hair style selected by the participant. |
| eyes | Whole number. | The avatar eye style selected by the participant. |

To recieve and embedded data variable in Qualtrics, you must delcare an empty variable with the desired name at the top of your survey flow. For instance, to recieve all of the participants' customizations:

| ![Capture Query String](/img/console/qualtrics_capturequery.png) |

Any choices the participant has selected in question scenes will also be passed back to Qualtrics. To record them, declare an empty variable at the top of your survey flow corresponding to the variable name you have listed in the question scene.

| ![Assign embedded data](/img/console/qualtrics_capturedecisions.png) |


## Reading the Data

Since all data from the simulation is routed to and then stored in Qualtrics,
there are no additional data files to collect. The `*.csv` downloaded from
Qualtrics will have a column for any data collected from the URL and stored as
embedded data.

One quirk of having the participant leave Qualtrics to complete a task before
returning to a survey is that each participant will have more than one row in
the dataset across which their survey responses are spread.

As recommended above, it may be necessary to assign a random ID to each
participant on their first survey view, pass that to the simulation, and collect
the ID when they return to the survey so that the two records in the Qualtrics
dataset have a matching field on which they can be joined.

An [R script](https://github.com/Plea-Justice/scripts/tree/main/link-qualtrics-responses)
is provided to demonstrate how to merge the responses into one row per
participant. A similar script is also
[available in Python](https://github.com/Plea-Justice/scripts/tree/main/clean-data).