# DataClean
DataCleaning project

This repo includes scipts and cook book  used to solve project requierement, which must cover the next topics:
 
* Merges the training and the test sets to create one data set.
* Extracts only the measurements on the mean and standard deviation for each measurement. 
* Uses descriptive activity names to name the activities in the data set
* Appropriately labels the data set with descriptive variable names. 
* From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
* Final tidy data will be located in the data directory: req5.txt

Only one script was built to cover the four requierments, it is script run_analyiys.R

Script requires no parameters but request that data is placed in directory data.

To run script, you must first have the input data extracted from zip file located in a subdirectory called "data" located at the same directory level as your R working directory is.
To execute follow the next step:

1. Source the script: source('run_analysis.R')
2. Execute the script: run_analysis()
3. You'll may receive a message about the "data.table" package 
4. After script is done the tidy data set will be located in ./data/req5.txt
