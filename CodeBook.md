#Codebook for DataClean Project

##Data for this project is taken from data collected from samples using Samsung Galaxy S Smartphone

##Requirements:
* In order to execute the run_analysis() method you must accomplish the following:
* Access to https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip file
* Downlod .zip file to R server
* Unzip file into data directory
* data.table package must be installed
* run_analysis.R script must be located in the same directory as the data directory is located (must be siblings)
* You must source run_analysys.R script from your R session; Please review that your working directory contains the script and the data directory
* Execute run_analysys() method


##Files Description:

* getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip := Source file for the analysis
* ./data/Dataset/test/X_test.txt := Test measurements
* ./data/Dataset/test/y_test.txt := Test lables
* ./data/Dataset/test/subject_test.txt := Test subjects
* ./data/Dataset/train/X_test.txt := Train measurements
* ./data/Dataset/train/y_test.txt := Train lables
* ./data/Dataset/train/subject_test.txt := Train subjects
* ./data/Dataset/features.txt   := Measurement names
* ./data/Dataset/activity_labels.txt := Activity descriptive names
* ./data/req5.txt   := Tidy Dataset requested by this project
* ./run_analysis.R  := R script to create requested data set



##run_analysys() Script Description

The following describes steps used to produce the data requested by the project

1. Read data from source: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 
  1. Use download.file method to requested data from web and downloaded to server
  2. Unzip files and leave data to be usede
2.Load Library(data.table) to use read.table methods requiered to load data
3. Use read.table function to load test and train data into separate dts each  as follows:
     1. data_test ./data/Dataset/test/X_test.txt
     2. label_test ./data/Dataset/test/label_test.txt
     3. suubject_test ./data/Dataset/test/subject_test.txt
     4. data_train ./data/Dataset/test/X_train.txt
     5. label_train ./data/Dataset/test/label_train.txt
     6. subject_train ./data/Dataset/test/subject_train.txt
4.  Merge each test and train data set into a single one
    1.  Use rbind on each couple to merge does files
5.  Start by assigning descriptive names to the variables 
    1. Desciptions are located in the ./data/Dataset/features.txt file
    2. use colnames() funciton to assing previously read 
6.  From the complete set of variables, selects only those that represents Mean and Std values
   1. Use grep function to selects only variables requested
   2. Create a new DT using only the selected variables
7. Use descriptive activity names for the data set
   1. Activities are located in the ./data/Dataset/activity_labels.txt file
   2. Activity_lables file, maps activity numebers to activity names. This map will be used to replace numbers in the dataset
   3. Replace numbers with activity_names in the dataset
   4. Add Subject Column and Activity_name to the working dt
8. Create a second data set from the previous DT 
   1. DS must have average each variable for each subject and activity in the data set
   2. Write DS to a file using write.file method
  
   
