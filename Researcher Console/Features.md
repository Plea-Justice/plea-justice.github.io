---
layout: page
title: Features
permalink: /console/features
nav_order: 2
parent: Researcher Console
---

# Features

The main features and pages of the Researcher Console are shown here as numbered example images and corresponding descriptions. You can use these anchor links below to jump to a particular element of the Researcher Console.

Jump to:
* [Navigation Pane and Scenario Selection Page](#navigation-pane-and-scenario-selection-page)
* [Assets Page](#assets-page)
* [Scenario Navigation Bar](#scenario-navigation-bar)
* [Scenario Workspace](#scenario-workspace)
* [Preview Scenario Screen](#preview-scenario-screen)

***

### Navigation Pane and Scenario Selection Page

Upon creating an account and logging in, the user of the researcher console is directed to this `Scenario selection page` shown below, where they can manage different Pleajustice simulation projects.

{:refdef: style="text-align: center;"}
[![a numbered image of the researcher console's scenario page](/img/console/numbered_scenario.png)](/img/console/numbered_scenario.png)
{:refdef}

1.  The top, shaded row is the navigation pane shown on all Researcher Console pages. The left side is used to swap between the [Assets](#assets-page) and [Scenarios](#scenario-navigation-bar) pages.
2.  The right side of the row contains buttons to access the <u>admin console</u> (internal use only), <u>logging out</u>, and the <b><u>help menu</u></b>. The help menu shows additional information on the current view the user is on.
3.  The <u>Add</u> button creates a new, blank scenerio while the <u>Duplicate</u> button allows the user to select an existing scenario to duplicate.
4.  Here are where individual scenarios are organized. Each separate pane contains a <u>scenario title</u>, <u>description of project</u>, <u>time last edited</u>, and a <u>time created</u>. From this page, users can <u>modify the scenario</u> by clicking on the title, <u>delete the scenario</u> by clicking on the red X, or <u>edit the displayed properties</u> by clicking on the pencil button. Shown in the example image above are two scenarios named "`mockup scenario 1`" and "`sandbox`".

***

### Assets Page

Assets used for the simulation can be managed on this page. Users will likely have access to all assets featured in the original Pleajustice pilot studies, but will also have the option to upload their own customized assets.

<!--- insert chart for existing assets and clips --->
{:refdef: style="text-align: center;"}
[![a numbered image of the researcher console's assets page](/img/console/numbered_assets.png)](/img/console/numbered_assets.png)
{:refdef}

1.  An <u>Add</u> button is highlighted green at the top of the page for users to upload their own assets, apart from the ones that are preloaded.
2.  The <u>Filter Asset Type</u> feature shows only assets of a particular type. Users would select a type of asset from the dropdown menu on the top-right of the screen and assets of the selected type would populate the screen.
3.  This <u>file upload pane</u> that appears when users click the Add button to add an asset. Users would choose a file to upload from their computer, and then select what asset type the file is (Actor, Background, Cache, Clip, Foreground).
4.  An example of an uploaded asset is shown above, with the <u>asset's name</u> (which is the file's original name when uploaded), a <u>preview of the file</u>, <u>uploaded date</u>, <u>asset type</u>, and a button to <u>delete the asset</u>.

***

### Scenario Navigation Bar

When editing a Scenario, the features on the toolbar floating on the top of the row can be used to modify the Scenario, conditions, [scenes](#scenario-workspace), and other configuration options. The name of the project "`sandbox`" is located in the top right of the image, shown in the example below.

{:refdef: style="text-align: center;"}
[![a numbered image of the researcher console's Scenario nav bar](/img/console/numbered_nav.png)](/img/console/numbered_nav.png)
{:refdef}

1.  This area contains features that are in regards to the properties of the overall project.
    1.  The <u>scene count</u> shows the total number of scenes.
    2.  The <u>Save</u> button saves all changes and configurations made.
    3.  The <u>Options</u> button opens a menu to change the details of the Scenario, such as the *Survey URL*, or the *Scenario Name* and *Description* displayed in the [Scenario Selection Page](#navigation-pane-and-scenario-selection-page).
    4.  The button containing arrows is a <u>Expand/Collapse All Scenes</u> button, affecting all scenes.
2.  The <u>Add Condition</u> button creates another condition by replicating the right-most column.
3.  This area contains features that are in regards to individual scenes.
    1.  The <u>Swap</u> button allows the user to swap two scenes within the same Condition by first selecting one scene, and then selecting the scene the user would like to swap it with.
    2.  The <u>Copy</u> button allows the user to copy a scene by first selecting a scene to be copied and then selecting as many scenes as the user would like to replace.  
    3.  The <u>Bind</u> button allows the user to bind the properties of scenes in the same row to forcibly match that of a single scene, by first selecting the scene the user would like replicated and then selecting other scenes <i>to bind to</i>.
4.  This area contains features that are in regards to finishing and wrapping up the project.
    1.  The console is responsive to <u>unsaved changes</u> so the user is notified if there are any.
    2.  The <u>Preview</u> button generates a workable preview URL of the simulation, that replicates the conditions and their respective scenes. The URL will show the [Preview Scenario Screen](#preview-scenario-screen)
    3.  The <u>Publish</u> button pulls a dropdown menu with a `Manual Download` and a `Publish Live` option. These features need to be manually enabled; please consult with the administrator of the Pleabargains project.

    * <u>Manual Download</u> allows you to download all files associated with the scenario's simulation as a ZIP. Once downloaded, the files can be deployed onto a server independent of the Researcher Console.
    * After verifying the user's login credential, clicking <u>Publish Live</u> will create another entry in the dropdown menu called, `Active Live Link`. Qualtrics has a [*End of Survey* feature](/simulation/working-with-qualtrics#controlling-the-simulation) to allow a survey redirect to a link once the survey is completed.

***

### Scenario Workspace

When editing a scenario, the user is given a workspace to modify conditions (represented as columns) and scenes (represented as individual panes within the row, or frames). The example shown here is simply one condition, one scene frame, and one scene. A blank scene (represented as a scene with a `+` button and no configurable details) can also used as padding to align scenes across frames, not shown in the example.

1.  The top row shows all conditions of the scenario, where users can <u>Delete conditions</u> and <u>Add & Remove Tags</u> that are relevant to each particular conditions.
2.  This is the <u>Scene Frame Name</u> and <u>Unique Scene Count</u>. In this example:
[![a numbered image of the researcher console's frame](/img/console/numbered_frame.png)](/img/console/numbered_frame.png){: style="float: right"}
    1. `Courtroom1` is the name of the scene frame (the particular row).
    2. There are `2` unique scenes indicated within this row (only one scene is shown in the example).
3.  This is the <u>Scene Frame Count</u>, where the example indicates this is the first scene frame.
4.  Located on the left side of the scene frame are a few buttons that manage the scene frame.
    1. The uppermost button is a <u>Collapse/Expand</u> button. The scene frame is currently expanded, but would only show the scene frame name and unique scene count when collapsed.
    2. The middle arrow buttons are <u>Swap Scene Frame</u> buttons. The current example shows only a downward facing arrow, to swap with the scene frame under it (since its the first frame).
    3. The lowermost button is the <u>Delete Scene Frame</u> button, which deletes the whole row.
5.  Users can select what type of scene by selecting <u>Dialogue</u>, <u>Clip</u>, or <u>Question</u>. A blank scene can also be used by selecting the Red X and clearing the scene type.
6.  This space contains fields that the user can select and fill in depending on the scene type selected.
    1. <u>Dialogue</u> scene types have the dropdown fields <em>Actor</em>, <em>Foreground</em>, and <em>Background</em> that will display the different asset types that are available. Additionally, a text field <em>Script</em> is available in order to render text on the screen during the simulation.
    2. <u>Clip</u> scene types only have a single dropdown field for <em>Clip</em> asset types.
    3. <u>Question</u> scene types have the dropdown fields <em>Background</em> and <em>Script</em> like the Dialogue scene type, but also have an additional field <em>Buttons</em> meant to give the user of the simulation a way to answer prompts on the screen via multiple-choice buttons rendered on the screen.

***

### Preview Scenario Screen

Clicking the <u>👁 ️Preview</u> button from the [scenario editing page](#scenario-navigation-bar) will direct the user to the screen below. This feature allows the user to demo their own scenarios

{:refdef: style="text-align: center;"}
[![a numbered image of the researcher console's preview page](/img/console/numbered_preview.png)](/img/console/numbered_preview.png)
{:refdef}

1.  A test name can be input to refer to the participant's name in the dialogue within the simulation.
2.  The user can run the simulation using one of the particular conditions made. Clicking the `Randomly Assign` button will shuffle the number in the text field to a random available condition.
3.  These are optional fields that the user can check off to append or supplement the simulation.
    1. The <u>Avatar Customization</u> option would allow the user of the preview to customize the colors and visual attributes of their avatar. This way, scenes that reference the participant's avatar will adapt to the corresponding configurations made in the customizer. If disabled, these references will simply use default values in place of the personalized avatar values.
    2. The <u>Fast Mode</u> option would *play clips* and *render dialogue* at a much faster speed, typically used for testing purposes.
