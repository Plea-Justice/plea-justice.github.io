---
layout: page
title: Data Cleaner
permalink: /simulation/docs/data-cleaner
parent: Simulation
---
## Cleaning Exported Qualtrics Data

Jump to [Detailed Directions to Run Cleaner on Pleabargains Data]() to see a more detailed explanation on running the data cleaning

The survey flow is broken up to multiple parts for each participant due to the animation redirecting the participant to-and-from the Qualtrics website. The data of the survey is exported as a .csv file, where data for each participant is split into multiple rows, sharing a parameter (a key, in a key-value association) called LinkID across these rows. The script combines the rows with the same LinkID together so that each participant occupies only 1 row.

### Brief Directions to Run Cleaner on Pleabargains Data
1. Download the script and put it in the same folder as the csv file
2. Edit the script’s contents such that the following variables are assigned ...
	a. ... the desired file names you want:
		* `file_name_in` (input file; the data csv file)
		* `file_name_out` (output file)
		* `file_name_out_deleted` (an optional output file for test rows containing LinkID:123456)
	b. ... the name of the variable that refers to the participants unique ID:
		* `ID_beginning` (ID at the beginning of the survey flow)
		* `ID_end` (ID at the end of the survey flow)
	c. ... the correct corresponding value (0 or 1)
		* `Is_WithinParticipants` (change to 0 if csv has 3 header rows, 1 if it has 2 header rows)
3. Open the Command Prompt / Terminal and navigate to the folder containing the script.
4. Run the file by typing “python cleanData.py”
5. Look in the same folder for the output files.
Repeat the editing step (step 2) for each time you need to clean more data.

### Script details

The script will attempt to clean exported .csv files generated from Qualtrics by combining multiple rows of the same LinkID together by way of updating key:value pairs in a ordered dictionary data structure. There will be instances where data is present in **more than one** of these rows with the same LinkID. In these cases, data in the first row is written into the output file, and data from the same column of further row will not be written to the output file.

| Column Name | Interaction |
| ----- | ----- |
| “*LinkID*” | The script will find the LinkID across rows and attempt to merge data between the two rows. Data from the first row will be written to the output file; this includes redundant values of the same column but also data where the values of the same column are different. Below are columns where there are exceptions to this behavior. |
| “*email*” | The script will combine values from the rows and remove the comma because data from this row is typically a single comma or the full email address. The resulting string will be written to the output file. |
| “*Duration (in seconds)*” | The script will add all values from all the rows together and write the total to the output file. |
| *ID_1* or *ID_2* | The script will check these values if they are “123456” and save the whole LinkID to a separate data structure dedicated to test entires. If this data structure is populated, then a second output file will be created, populated with entries where this variable’s value is “123456”. |


### Detailed Directions to Run Cleaner on Pleabargains Data

(will add soon!)

[ordered-objects]: https://docs.python.org/2/library/collections.html#ordereddict-objects
[python-dictionaries]: https://www.w3schools.com/python/python_dictionaries.asp
