---
layout: page
title: Data Cleaner
permalink: /simulation/data-cleaner
nav_order: 3
parent: Simulation
---
# Cleaning Exported Qualtrics Data

Here are the [Brief Instructions](#brief-directions-to-run-cleaner-on-pleabargains-data) for a quick walkthrough on cleaning the data. Jump to the [Detailed Directions](#detailed-directions-to-run-cleaner-on-pleabargains-data) section to see a more detailed explanation on running the data cleaning program.

***

The data cleaner is a program, also known as a *script*, written to parse through CSV files exported from Qualtrics surveys that are directly associated to the *plea bargain simulation software*.

The survey flow can be broken up to multiple parts such that Qualtrics can redirect the participant to the animation, and the animation can redirect the participant back to Qualtrics. Because of this, the survey data for a particular participant is broken up into multiple parts. The data cleaner is for experiments that require a redirect from Qualtrics, to the simulation, and back to Qualtrics again. The figure shown below is an example of what the design of an experiment flow may look like.

<p align="center">
    <img src="/img/data_cleaner1.png" align="center" alt="diagram of the experiment flow. Qualtrics entities are highlighted as blue">
    <caption style="caption-side:bottom">The participant is redirected to each stage of the experiment as they complete the tasks of each element. Highlighted in blue are where Qualtrics response are recorded. For this example, two rows would be created since the experiment redirects to Qualtrics twice.</caption>
</p>

The survey data is exported as a .csv file, where data entries for each participant is split into multiple rows, sharing a parameter (a key, in a key-value association) called LinkID across these rows. The script combines the rows with the same LinkID together so that each participant occupies only 1 row.


## Brief Directions to Run Cleaner on Pleabargains Data

1.  [Download the script]() and put it in the same folder as the csv file.
2.  Edit the script’s contents such that the following variables are assigned ...
    1.  **...** the desired file names you want:

         **file_name_in** (input file; the data csv file)

         **file_name_out** (output file)

         **file_name_out_deleted** (an optional output file for test rows containing LinkID:123456)

    2.  **...** the name of the variable that refers to the participants unique ID:

         **ID_beginning** (ID at the beginning of the survey flow)

         **ID_end** (an optional ID at the end of the survey flow)

    3.  **...** the correct corresponding value (0 or 1)

         <b>Is_WithinParticipants</b> (change to 0 if csv has 3 header rows, 1 if it has 2 header rows)

3.  Open the Command Prompt / Terminal and navigate to the folder containing the script.
4.  Run the file by typing `python cleanData.py`
5.  Look in the same folder for the output file(s); the output of the program should be a file that merges rows with the same LinkID, alongside other adjustments. An optional second output may be created.

Repeat the editing step (step 2) for each time you need to clean more data.

***

## Script Details

The program The script will attempt to clean exported .csv files generated from Qualtrics by combining multiple rows of the same LinkID together by way of updating key:value pairs in a [ordered](ordered-objects) [dictionary](python-dictionaries) data structure. Data entries typically will have more than one row with the same LinkID. In these cases, data in the **first row** is saved to be written into the output file, and data from the same column of a row with a matching LinkID will not be written to the output file, thus not overwriting existing elements.

| Column Name | Interaction |
| ----- | ----- |
| “*LinkID*” | The script will find the LinkID across rows and attempt to merge data between the two rows. Data from the first row will be written to the output file; this includes redundant values of the same column but also data where the values of the same column are different. Below are columns where there are exceptions to this behavior. |
| “*Duration (in seconds)*” | The script will add all values from all the rows together and write the total to the output file. |
| *ID_1* or *ID_2* | The script will check these values if they are “123456” and save the whole LinkID to a separate data structure dedicated to test entires. If this data structure is populated, then a second output file will be created, populated with entries where this variable’s value is “123456”. |
| “*email*” | The script will combine values from the rows and remove the comma because data from this row is typically a single comma or the full email address. The resulting string will be written to the output file. |

***

## Detailed Directions to Run Cleaner on Pleabargains Data

### Configuring the program

1.  First download the script and make sure it is in the same folder as the csv file.
    Modify the script so that it cleans data from the correct file
2.  Right click on the script.
3.  Find an entry or similar to “open with” or “edit with”.
4.  Find the respective application you would like to open with. Notepad, Text Editor suffices. Atom, and sublime text can be used as well, as they have keyword highlighting.
    <p align="center">
        <img src="/img/data_cleaner2.png" align="center" alt="written declarations of variables in the program">
    </p>
5.  With an example shown above, modify the variables such that they are accurate to the desired input/output as well as the properties of the experiment described in Materials: Properties.
6.  Once the edits have been made to the 3 variables, save the file and exit.  


### Running the program

Once you have the file and configured the file accordingly. Follow these steps to run the python script. See [Downloading and Configuring Python](#downloading-and-configuring-python) to see steps on downloading and installing python or checking what version you have.

1.  Open Terminal (Linux, Mac) or Command Line (Windows)
2.  Navigate to the folder that contains the data cleaner file and CSV data file using “cd” and “ls”(linux/mac) / “dir”(windows).
    1.  In Terminal/Command Line, type: `cd <full path name of the folder>`

    examples* include:

| OS | Example in terminal |
| ----- | ----- |
| Windows | `cd C:\users\` |
| Linux, Mac | `cd /home/johndoe/Downloads/` |

3.  To run the script once you’re in the respective directory, Type: `python cleanData.py`

    **Note**: Type `python3` instead of `python` If you downloaded Python 3 with Python 2 pre-existing on your system.

    1.  See [Downloading and Configuring Python](#downloading-and-configuring-python):step 3 if this step gives you an error

4.  Output files will be generated in the same folder based on the names of **file_name_out** and **file_name_out_deleted**.

**Note**: If your file has spaces, you can either encapsulate the whole name of the folder in “quotes” or precede each space character with a “\” backslash character ensuring the space character is read.

### Downloading and Configuring Python

Make sure you have python version 3.8.1 (this was the version the script was written in. Be wary other versions may not support some features). Here is how to check what version of python you have:

1.  Open Terminal (Linux, Mac) or Command Line (Windows) <img src="/img/data_cleaner3.png" align="right" alt="checking the version of Python installed">
2.  Type: `python --version`
3.  [Download python if you find that you don’t have version 3 of python here](download-python). Click the link, find the Download Python button, scroll down to Files, and download the respective version to your operating system.
    * [This link contains information on configuring the Environment Variable on Windows and other configuration details](environment-variable).

[ordered-objects]: https://docs.python.org/2/library/collections.html#ordereddict-objects
[python-dictionaries]: https://www.w3schools.com/python/python_dictionaries.asp

[download-python]: https://www.python.org/downloads/
[environment-variable]: https://en.wikibooks.org/wiki/Python_Programming/Getting_Python
