#Codebook for DataClean Project

##Data for this project is taken from data collected from samples using Samsung Galaxy S Smartphone

##Requirements:
* In order to execute the run_analysis() method you must accomplish the following:
* Access to https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip file
* Downlod .zip file to your R server
* Unzip file into data directory
* data.table package must be previously installed, the script will loaded it for you
* run_analysis.R script must be located in the same directory as the "data" directory is located (must be siblings)
* You must source run_analysis.R script from your R session; Please review that your working directory contains the script and the data directory
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



##Script Description (run_analysis.R):

The following describes steps used to produce the data requested by the project

1.  Read data from source: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 
  1. Use download.file method to requested data from web and downloaded to server
  2. Unzip files and leave data to be usede
2.  Load Library(data.table) to use read.table methods requiered to load data
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
8.  Create a second data set from the previous DT 
    1. DS must have average each variable for each subject and activity in the data set
    2. Write DS to a file using write.file method
  
   
##Variables Description (req5.txt contents)
1.activity_name := Activity long name as described activity_labls file  
2.subject       := Subject identifier
3.  	tBodyAcc-mean()-X	:= Mean by activity and subject of tBodyAcc-mean()-X
4.  	tBodyAcc-mean()-Y	:= Mean by activity and subject of tBodyAcc-mean()-Y
5.  	tBodyAcc-mean()-Z	:= Mean by activity and subject of tBodyAcc-mean()-Z
6.  	tGravityAcc-mean()-X	:= Mean by activity and subject of tGravityAcc-mean()-X
7.  	tGravityAcc-mean()-Y	:= Mean by activity and subject of tGravityAcc-mean()-Y
8.  	tGravityAcc-mean()-Z	:= Mean by activity and subject of tGravityAcc-mean()-Z
9.  	tBodyAccJerk-mean()-X	:= Mean by activity and subject of tBodyAccJerk-mean()-X
10.  	tBodyAccJerk-mean()-Y	:= Mean by activity and subject of tBodyAccJerk-mean()-Y
11.  	tBodyAccJerk-mean()-Z	:= Mean by activity and subject of tBodyAccJerk-mean()-Z
12.  	tBodyGyro-mean()-X	:= Mean by activity and subject of tBodyGyro-mean()-X
13.  	tBodyGyro-mean()-Y	:= Mean by activity and subject of tBodyGyro-mean()-Y
14.  	tBodyGyro-mean()-Z	:= Mean by activity and subject of tBodyGyro-mean()-Z
15.  	tBodyGyroJerk-mean()-X	:= Mean by activity and subject of tBodyGyroJerk-mean()-X
16.  	tBodyGyroJerk-mean()-Y	:= Mean by activity and subject of tBodyGyroJerk-mean()-Y
17.  	tBodyGyroJerk-mean()-Z	:= Mean by activity and subject of tBodyGyroJerk-mean()-Z
18.  	tBodyAccMag-mean()	:= Mean by activity and subject of tBodyAccMag-mean()
19.  	tGravityAccMag-mean()	:= Mean by activity and subject of tGravityAccMag-mean()
20.  	tBodyAccJerkMag-mean()	:= Mean by activity and subject of tBodyAccJerkMag-mean()
21.  	tBodyGyroMag-mean()	:= Mean by activity and subject of tBodyGyroMag-mean()
22.  	tBodyGyroJerkMag-mean()	:= Mean by activity and subject of tBodyGyroJerkMag-mean()
23.  	fBodyAcc-mean()-X	:= Mean by activity and subject of fBodyAcc-mean()-X
24.  	fBodyAcc-mean()-Y	:= Mean by activity and subject of fBodyAcc-mean()-Y
25.  	fBodyAcc-mean()-Z	:= Mean by activity and subject of fBodyAcc-mean()-Z
26.  	fBodyAcc-meanFreq()-X	:= Mean by activity and subject of fBodyAcc-meanFreq()-X
27.  	fBodyAcc-meanFreq()-Y	:= Mean by activity and subject of fBodyAcc-meanFreq()-Y
28.  	fBodyAcc-meanFreq()-Z	:= Mean by activity and subject of fBodyAcc-meanFreq()-Z
29.  	fBodyAccJerk-mean()-X	:= Mean by activity and subject of fBodyAccJerk-mean()-X
30.  	fBodyAccJerk-mean()-Y	:= Mean by activity and subject of fBodyAccJerk-mean()-Y
31.  	fBodyAccJerk-mean()-Z	:= Mean by activity and subject of fBodyAccJerk-mean()-Z
32.  	fBodyAccJerk-meanFreq()-X	:= Mean by activity and subject of fBodyAccJerk-meanFreq()-X
33.  	fBodyAccJerk-meanFreq()-Y	:= Mean by activity and subject of fBodyAccJerk-meanFreq()-Y
34.  	fBodyAccJerk-meanFreq()-Z	:= Mean by activity and subject of fBodyAccJerk-meanFreq()-Z
35.  	fBodyGyro-mean()-X	:= Mean by activity and subject of fBodyGyro-mean()-X
36.  	fBodyGyro-mean()-Y	:= Mean by activity and subject of fBodyGyro-mean()-Y
37.  	fBodyGyro-mean()-Z	:= Mean by activity and subject of fBodyGyro-mean()-Z
38.  	fBodyGyro-meanFreq()-X	:= Mean by activity and subject of fBodyGyro-meanFreq()-X
39.  	fBodyGyro-meanFreq()-Y	:= Mean by activity and subject of fBodyGyro-meanFreq()-Y
40.  	fBodyGyro-meanFreq()-Z	:= Mean by activity and subject of fBodyGyro-meanFreq()-Z
41.  	fBodyAccMag-mean()	:= Mean by activity and subject of fBodyAccMag-mean()
42.  	fBodyAccMag-meanFreq()	:= Mean by activity and subject of fBodyAccMag-meanFreq()
43.  	fBodyBodyAccJerkMag-mean()	:= Mean by activity and subject of fBodyBodyAccJerkMag-mean()
44.  	fBodyBodyAccJerkMag-meanFreq()	:= Mean by activity and subject of fBodyBodyAccJerkMag-meanFreq()
45.  	fBodyBodyGyroMag-mean()	:= Mean by activity and subject of fBodyBodyGyroMag-mean()
46.  	fBodyBodyGyroMag-meanFreq()	:= Mean by activity and subject of fBodyBodyGyroMag-meanFreq()
47.  	fBodyBodyGyroJerkMag-mean()	:= Mean by activity and subject of fBodyBodyGyroJerkMag-mean()
48.  	fBodyBodyGyroJerkMag-meanFreq()	:= Mean by activity and subject of fBodyBodyGyroJerkMag-meanFreq()
49.  	angle(tBodyAccMean,gravity)	:= Mean by activity and subject of angle(tBodyAccMean,gravity)
50.  	angle(tBodyAccJerkMean),gravityMean)	:= Mean by activity and subject of angle(tBodyAccJerkMean),gravityMean)
51.  	angle(tBodyGyroMean,gravityMean)	:= Mean by activity and subject of angle(tBodyGyroMean,gravityMean)
52.  	angle(tBodyGyroJerkMean,gravityMean)	:= Mean by activity and subject of angle(tBodyGyroJerkMean,gravityMean)
53.  	angle(X,gravityMean)	:= Mean by activity and subject of angle(X,gravityMean)
54.  	angle(Y,gravityMean)	:= Mean by activity and subject of angle(Y,gravityMean)
55.  	angle(Z,gravityMean)	:= Mean by activity and subject of angle(Z,gravityMean)




