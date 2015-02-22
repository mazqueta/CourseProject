CodeBook

Source Data:
========
Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

The original data source can be found at http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain.

DATA
=========================================================================
There is a data set: 
train/X_train.txt 	--Training set. Contains the calculated variables 					of each subject, doing each activity. Each 					row represents a time window. 
train/y_train.txt 	-- Training data label. Contains info about what 					activity is being done at each time window
train/subject_train.txt	-- Contains info about what Subject 						performed the activity each time window 

test/X_test.txt 		-- Test set
test/y_test.txt 		-- Test data label
test/subject_test.txt Subject who performed activity test

features.txt 		--- data set of features or calculated variables

Dimensions
=====================================================================
features.txt 		-- [1,561]
X_train.txt  		-- [7352,561]
y_train.txt  		-- [7352,1]
subject_train.txt 	-- [7352,1]
X_test.txt 			-- [2947,561]
y_test.txt  		-- [2947,1]
subject_test.txt		-- [2947,1]

DATA TRANSFORMATION
====================================================================

Merging data with the same number of columns
Files containing the measured features:

X_test<-read.table("X_test.txt")
X_train<-read.table("X_train.txt")

# Merge both data frames together in a data frame called total

total<-rbind(X_train, X_test)

total 	-- 10299 obs. of 561 variables

# We are interested on the files containing the measured activities:
y_train<-read.table("y_train.txt")
y_test<-read.table("y_test.txt")
# Merge both data frames together in a (column) data frame called #total_activity:

total_activity<-rbind(y_train, y_test)

total_activity --- 10299 obs of 1 variable


# We are interested on the files containing info about which measurements correspond to which subject:
subject_test<-read.table("subject_test.txt")
subject_train<-read.table("subject_train.txt")
# Merge both data frames together in a data frame called total_subjects
total_subjects<-rbind(subject_train, subject_test)

total_subjects  --- 10299 obs. of 1 variable

#Add header to the total Data frame, corresponding to the features
features<-read.table("features.txt")
features<-features[,2]
names(total)<-features

Extract columns of the Total_data data frame that contain the name Mean and std :

Extracted data frames:

total_mean 
total_std

# Merge these data frames (putting columns one next to the other)with the total data frame in a new data frame: total_clean



Tidydata.txt  DATA DICTIONARY
====================================================================
Subject	
		Volunteer performing the activity		
		1..30
Activity	
		Activity done by each volunteer
		Standing, walking, walking downstairs, walking upstairs, 			sitting, laying

tBodyAcc-mean()-X
		
		mean tBodyAcc-mean()-X of each subject doing each activity
same explanation for the rest of the columns























