This is the **CodeBook** for the course project of the Getting and Cleaning Data course, which is a part of the Data Science speacialization offered by JHU via Coursera.


## Downloading the dataset
The dataset has been downloaded from [here](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip)


**The ```run_analysis.R``` script is used to convert the downloaded data into tidy data.**
The information for the same is given below.


## Variables' information
- ```features <- features.txt``` : 561 rows, 2 columns.
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
- ```activities <- activity_labels.txt``` : 6 rows, 2 columns.
List of activities performed when the corresponding measurements were taken and its codes (labels).
- ```subject_train <- test/subject_train.txt``` : 7352 rows, 1 column.
contains train data of 21/30 volunteer subjects being observed.
- ```subject_test <- test/subject_test.txt``` : 2947 rows, 1 column.
contains test data of 9/30 volunteer test subjects being observed.
- ```x_train <- test/X_train.txt``` : 7352 rows, 561 columns.
contains recorded features train data.
- ```x_test <- test/X_test.txt``` : 2947 rows, 561 columns.
contains recorded features test data
- ```y_train <- test/y_train.txt``` : 7352 rows, 1 columns.
contains train data of activities’code labels
- ```y_test <- test/y_test.txt``` : 2947 rows, 1 columns.
contains test data of activities’code labels.


## Merging training and testing datasets into one
- ```x_all``` (10299 rows, 561 columns) is created by merging ```x_train``` and ```x_test``` using the ```rbind()``` function.
- ```y_all``` (10299 rows, 1 column) is created by merging ```y_train``` and ```y_test``` using the ```rbind()``` function.
- ```subject_all``` (10299 rows, 1 column) is created by merging ```subject_train``` and ```subject_test``` using the ```rbind()``` function.
- ```merged_data``` (10299 rows, 563 column) is created by merging ```subject_all```, ```y_all``` and ```x_all``` using the ```cbind()``` function.


## Extracting only the measurements on the mean and standard deviation for each measurement
```tidy_data``` (10299 rows, 88 columns) is created by subsetting ```merged_data```, selecting only the columns: ```subject```, ```code``` and the measurements on the ```mean``` and standard deviation (```std```) for each measurement.


## Using descriptive actvity names
All numbers in the ```code``` column of the ```tidy_data``` replaced with corresponding activity taken from second column of the activities variable.


## Labeling the data with descriptive varible names appropriately
- ```code``` column in ```tidy_data``` renamed into ```activities```.
- All ```Acc``` in column’s name replaced by ```Accelerometer```.
- All ```Gyro``` in column’s name replaced by ```Gyroscope```.
- All ```BodyBody``` in column’s name replaced by ```Body```.
- All ```Mag``` in column’s name replaced by ```Magnitude```.
- All start with character ```f``` in column’s name replaced by ```Frequency```.
- All start with character ```t``` in column’s name replaced by ```Time```.


## Averaging each variable for each activity and each subject to form the final tidy dataset
- ```final_data``` (180 rows, 88 columns) is created by sumarizing ```tidy_data``` taking the means of each variable for each activity and each subject, after groupped by subject and activity.
- Export ```final_data``` into ```final_data.txt``` file.
