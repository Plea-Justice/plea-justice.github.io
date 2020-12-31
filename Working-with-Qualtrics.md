---
layout: page
title: Working with Qualtrics
permalink: /simulation/working-with-qualtrics
nav_order: 4
---

# Working with Qualtrics

Certain simulation parameters may be manipulated within Qualtrics. These parameters may set or be randomly assigned in Qualtrics' embedded data and then sent to the simulation via a [query string](https://www.qualtrics.com/support/survey-platform/survey-module/survey-flow/standard-elements/passing-information-through-query-strings/) with the simulation's URL.

The simulation will also send data back to Qualtrics in this way. For instance, the features a participant has selected for his or her avatar and answers to prompts within the simulation may be passed back to Qualtrics in the query string.

## Controlling the Simulation

To assign simulation options, such to assign a participant to a particular condition, assign the option in a Qualtrics embedded data variable.

{:refdef: style="text-align: center;"}
![Assign embedded data](/img/qualtrics_querystring_data.png)
{:refdef}

At the custom end block in which the participant is redirected to the simulation, add embedded data to the URL query.

{:refdef: style="text-align: center;"}
![Assign embedded data](/img/qualtrics_querystring_endofsurvey.png)
`http://pleajustice.org/simulation.html?condition=${e://Field/condition}`
{:refdef}

The following table lists the variables that may be manipulated via the simulation URL.

| URL Query Parameter | Possible Values | Explanation |
|-|-|-|
| condition | Whole number. | The experimental condition assigned to the participant. |
| name | word less than 20 characters. | The participant's first name, gathered within Qualtrics. |

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
| id | Whole number. | ID randomly assigned to the participant to connect data accross survey responses. |
| email | Valid email address. | Email address of the participant passed through the simulation. |
| modcounter | 1 | determines if the survey is on the first or second randomized scenario |
