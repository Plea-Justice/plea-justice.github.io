---
layout: page
title: Configuring a Study
permalink: /introduction
nav_order: 2
---

# Getting Started with the Configuration Console
{: .no_toc }

The researcher console is an online system from which you can design and run simulation studies. This document covers the basics of using the console and publishing a simulation.

1. TOC
{:toc}

## Create an Account

To access the researcher console, navigate to [researcher.pleajustice.org](https://researcher.pleajustice.org) and click "Create an Account".

| ![Account Creation](/img/console/login_createaccount.png) |

## Obtain Animated Assets

Before creating a scenario, you will need to gather a set of images and animated clips from which you will later compose a storyline.

Assets may be copied in to your account from the library of assets shared by other users. To access these assets, navigate to the _Assets_ tab in the navigation bar and click _Shared Assets Library_.

| ![Assets Screen](/img/console/assets_empty.png) | ![Shared Assets](/img/console/assets_shared.png) |

This will open a screen from which you may view all of the assets that have been shared publicly by other users. To copy them to your account, click the ![Copy Button](/img/console/button_copy.png) copy button.

| ![My Assets](/img/console/assets.png) |

The assets are now available to your account. You may now select them for use when you create a new scenario.

## Create a Scenario

A scenario represents a single simulated storyline. You may run an experiment in which participants experience a single scenario or multiple. Each scenario is composed of columns representing the different versions of the storyline participants will experience in each experimental condition.

To create a scenario, navigate to _Scenarios_ tab in the navigation bar and click _Create New Scenario_. You will be prompted to provide a name and description for the scenario.

| ![Scenarios Screen](/img/console/scenarios_empty.png) | ![New Scenario](/img/console/scenarios_newscenario.png) |

If you have requested permission from an administrator, you may also have the option to share this scenario with others. If you share your scenario, keep in mind that others may copy it and will continue to possess their copy even if you later retract access.

Click the scenario name to open the editor. You will notice a single empty column representing the timeline of scenes in your first experimental condition.

| ![Blank Scenario](/img/console/scenario_blank.png) |

At the top left, click _Options_ and open the _Assets_ tab. The left column displays the list of assets available in your asset library. The right column will be empty; it lists assets that are used by this scenario. Assets will need to be selected on this screen before they can be used.

Select the checkbox on each of the assets you would like to include, then click the ![Right Arrow Button](/img/console/button_rightarrow.png) right arrow button to move them to the _Selected for Use_ column.

| ![Scenarios Screen](/img/console/scenario_optionsnoassets.png) | ![New Scenario](/img/console/scenario_optionsassets.png) |

Now that you have selected a set of assets from your library, click the _Settings_ tab. This tab allows you to edit properties such as the name and description of the scenario. It also allows you to add the _Survey URL_. This is the distribution URL of the Qualtrics Survey participants will be sent to when they complete the simulation. Paste your Qualtrics link here so that participants who complete the simulation will be sent back to the survey.

| ![Blank Scenario](/img/console/scenario_options.png) |

When you are done, click _Update Settings_ to return to the scenario editor. Click _Save_ in the top left or hit `ctrl` + `s` to save your changes.

## Add Scenes

The scenario editor presents a scenario as a set of vertical timelines labeled by experimental condition. Participants in condition one will be presented the version of the story in column one, those in condition two will be presented the version of the story in column two, and so on.

For now, we will set up the basic story with one experimental condition; additional conditions can be added later.

In the first frame of the story, click the ![Plus](/img/console/button_plus.png) plus button to add a scene. If you have not already, provide a label for your first scene.

| ![Scene](/img/console/scene.png) |

You will notice a row of buttons at the top of the scene corresponding to the possible scene types: _Clip_, _Dialogue_, or _Question_. Each will include dropdowns for you to select assets to show the participant along with other fields depending on the type.

<table>
  <tr>
    <td width="33%"><img src="/img/console/scene_clip.png" /></td>
    <td width="33%"><img src="/img/console/scene_dialogue.png" /></td>
    <td width="33%"><img src="/img/console/scene_question.png" /></td>
  </tr>
  <tr>
    <td>A <i>Clip</i> plays a premade animated movie clip.</td>
    <td>
      A <i>Dialogue</i> shows a single <i>Actor</i> speaking. What the actor
      says can be modified.
    </td>
    <td>
      A <i>Question</i> can collect information from the participant. Buttons
      will appear on the screen and the participant's response will be sent back
      to Qualtrics.
    </td>
  </tr>
</table>

While _Clip_ scenes do not have any customizable text, _Dialogue_ and _Question_ scenes include a textbox labeled _Script_. Any text entered in this box will be presented to the participant from within the simulation as an orange box at the bottom of the screen.

| ![Dialogue Box](/img/console/dialogue_box.png) |

The _Question_ type has additional fields labeled _Embedded Data Variable Name to Export_, which is necessary to send the participant's response back to Qualtrics, and _Possible Responses_, which is the list of multiple choice responses that will be available to the participant. Note that the order of this list is important; responses will be recorded as a number corresponding to the option selected (e.g. `choice=1` corresponds to `"Yes"` as in the example above).

## Add Experimental Conditions

After creating a story with our timeline of scenes in Condition 1, we can add more experimental conditions to our simulation study. Click _Add Condition_ in the toolbar to duplicate the existing timeline.

| ![One Condition](/img/console/scenario_onecondition.png) | ![Two Conditions](/img/console/scenario_twoconditions.png) |

This new condition will be identical to the first. We may manipulate variables by making changes to this new condition so that it is slightly different than the first. For instance, we can manipulate a variable such as sentence length by varying the _Script_ in a dialogue scene across conditions.

| ![Manipulation of Sentence Length](/img/console/scenario_manipulation.png) |
| Note the script is different in these two conditions. In one condition, the participant sees "6 months". In the other, they see "18 months". |

## Copy, Swap, and Bind

While some of your scenes may include maniupulations, the vast majority will remain the same across conditions. Several utilities in the toolbar can make this easier.

### Copy
{: .no_toc }

_Copy_ allows us to copy one scene to one or more others. Click _Copy_ in the toolbar, then click the scene you wish to copy followed by each scene you would like to replace. Click _Done_ to complete the copy operation.

| ![Copy](/img/console/scenario_copy.gif) |

### Swap
{: .no_toc }

_Swap_ allows us to swap the order of any two scenes in the same experimental condition (column). This is useful for counterbalancing.

To swap scenes vertically, click _Swap_ in the toolbar, then click the two scenes you wish to switch the order of.

| ![Swap](/img/console/scenario_swap.gif) |

### Bind
{: .no_toc }

_Bind_ is an advanced feature that allows us to guarantee certain scenes are identical across conditions (since it can be easy to accidentally introduce unwanted differences). A scene that is bound will remain identical to its parent, and will even be updated if the parent changes.

To bind scenes, click _Bind_ in the toolbar, then click the parent scene you followed by each scene you wish to bind to it. Click _Done_ to complete the bind operation.

| ![Swap](/img/console/scenario_bind.gif) |

Click the ![Unlink Button](/img/console/button_unlink.png) unlink button in the top right of a bound scene to unbind it.

Notice the counter present at the right of each frame label. This lists the number of scenes which are unbound. When no scenes are bound, this will be equal to the number of experimental conditions. When all scenes are bound, this box will not be present. The bind counter offers a quick way to check which scenes manipulate variables.

| ![Counter](/img/console/scenario_counter.png) | ![No Counter](/img/console/scenario_nocounter.png) |
| Two unbound scenes. | Zero unbound scenes; no manipulation. |