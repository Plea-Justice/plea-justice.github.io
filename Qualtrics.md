---
layout: page
title:  Connecting to Qualtrics
permalink: /qualtrics
nav_order: 3
---

# Working with Qualtrics
{: .no_toc}

Certain simulation parameters may be manipulated within Qualtrics. These parameters may set or be randomly assigned in Qualtrics' embedded data and then sent to the simulation via a [query string](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/) with the simulation's URL.

The simulation will also send data back to Qualtrics in this way. For instance, the features a participant has selected for his or her avatar and answers to prompts within the simulation may be passed back to Qualtrics in the query string.

Most studies will proceed in the following order:

`Qualtrics Survey → Simulation → Qualtrics Survey`

In this case, we can either route participants through two separate Qualtrics surveys or have them come back to the same survey multiple times.

A more complex study might have participants view more than one scenario, repeatedly redirecting between Qualtrics and a simulation.

`Qualtrics Survey → Simulation #1 → Qualtrics Survey → Simulation #2 → Qualtrics Survey`

Here we will demonstrate the first case and assume a single Qualtrics survey which participants will come back to multiple times.

1. TOC
{: toc}

## The Qualtrics Survey Flow

The participant will view the Qualtrics survey twice. Make sure _Prevent Ballot Box Stuffing_ is disabled in your Survey Options so that participants may view the survey more than once.

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

You must pass at least the randomly assigned experimental condition number as a parameter to the simulation. It is reccommended that you also pass a variable to track the number of times the participant has viewed your Qualtrics survey and a variable to identify that user in your analysis. To pass parameters into the simulation from Qualtrics, pass them in the [URL query string](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/).

Assign the participant's condition number to an embedded data variable in your Qualtrics survey.

| ![Assign embedded data](/img/qualtrics_querystring_data.png) |

At the custom end block in which the participant is redirected to the simulation, add embedded data to the end of the URL query.

| ![Assign embedded data](/img/qualtrics_querystring_endofsurvey.png) |
| e.g. add `?condition=${e://Field/condition}` to the URL |

Further parameters may follow the condition number serparated by the `&` symbol.

Any other parameters added to the URL may be used in piped text. All parameters will be passed unmodified through the simulation and back to the Qualtrics in case you wish to record them or use them in your branching logic.

## Using Piped Text in the Scenario Script

Any variables passed into the simulation via its query string can be inserted into the script much like Qualtrics piped text feature. The most common use for this feature is to reference the participant's name from within the simulation.

Advanced, multi-simulation studies may also use this feature to implement complex manipulations.

For instance, to insert the participant's name into the scrip of a dialogue scene, pass the name to the simulation in its URL. You will need to have collected the participant's name elsewhere in your survey (such as in the informed consent) and assigned it to a variable.

| ![Pass the Participant's Name](/img/console/qualtrics_queryname.png) |

Then, insert the parameter into the script of a scene in your scenario using the syntax `@Name;` or the `@` symbol followed by the name of your variable and then a semicolon.

| ![Insert Piped Text](/img/console/scene_dialogue.png) |

For more advanced manipulations, use Qualtrics' branching logic to set your piped text.

## Recieving Data in Qualtrics

The simulation will pass any variables received in its URL query string back to Qualtrics in the same fashion. Additional data, such as the choices made by the participant, will also be passed back and may be recieved in Qualtrics. The following table lists examples of the additional data that the Qualtrics survey might recieve from the simulation.

| URL Query Parameter | Possible Values | Explanation |
| ------------- | ------------- | ------------- |
| skinA | Hex color code. | The avatar skin color selected by the participant. |
| hairA | Hex color code. | The avatar hair color selected by the participant. |
| eyeA | Hex color code. | The avatar eye color selected by the participant. |
| outfitA | Hex color code. | The avatar outfit color selected by the participant. |
| figure | Whole number. | The avatar figure selected by the participant. |
| hair | Whole number. | The avatar hair style selected by the participant. |
| eyes | Whole number. | The avatar eye style selected by the participant. |

Any choice buttons the participant has selected will also be passed back to Qualtrics. These choices will be passed in the format `[Scene Name]` = `[Selection]` where the scene name is the name of the scene in which the participant was given the choice and the selection is the text on the button selected by the participant.

{:refdef: style="text-align: center;"}
![Assign embedded data](/img/qualtrics_capturedecisions.png)
{:refdef}

## Passthrough Data

The data received by the simulation and the data returned back to Qualtrics does not necessarily need to include only simulation variables. additional embedded data added to the simulation URL parameters will be passed back to Qualtrics. This allows data to be linked between multiple responses or multiple surveys. The following table lists examples of variables that may be passed through, though what is passed through is not at all restricted to this list.

| URL Query Parameter | Possible Values | Explanation |
| ------------- | ------------- | ------------- |
| linkid | Whole number. | ID randomly assigned to the participant to connect data accross survey responses. |
| email | Valid email address. | Email address of the participant passed through the simulation. |
| views | Whole number. | determines if the survey is on the first or second randomized scenario |
