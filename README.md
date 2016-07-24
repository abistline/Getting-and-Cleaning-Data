# Getting-and-Cleaning-Data
## Created for completing Week 4 Assignment - Creating and tidying datasets derived from "wearable" technology measurements

# The functionality of "run_analysis.R"

1. Begins by defining the internet source of the wearables datasets.
2. If the datasets do not already exist on the local directory, downloads and unzips the file leading to the datasets.
3. Ensures the proper R-packages are in place for code to run correctly.  This includes the "dplyr" and "reshape2" packages.
4. Summons the "features" variable into a 561 x 1 data frame.  Builds a vector for quickly selecting only the features variables that corresponds to mean and standard deviation.
5. Summons the sampled "train" values, X_train, into a 7352 x 86 data frame.  Summons y_train "activity" variable into a 7352 x 1 data frame.  Summons the subjTrain "subject" variable into a 7352 x 1 data frame.  Binds the subject and activity columns to the X_train data frame for a single "train" data frame with dimensions 7352 x 88.
6. Summons the sampled "test" values, X_test, into a 2947 x 86 data frame.   Summons the y_test "activity" variable into a 2947 x 1 data frame.  Summons the subjTest "subject" variable into a 2947 x 1 data frame.  Binds the subject and activity columns to the X_test data frame for a single  "test" data frame with dimensions 2947 x 88.
7. Merges the train and test data frames into a single 10299 x 88 data frame and names the columns. Note:  The function Uses gsub to remove the "()" and "-" characters from the column names.
8. Summons the activity-labels vector, and replaces the numbers in the "activity" column with their corresponding labels.  Also re-arranges the dataset:  first by subjectID, then by activity.
9.  Prints the dimensions of the resulting "test_train" data frame for a qc check (Should be 10299 x 88).
10. Creates a new tidy dataset of the average value per subject and activity.  Names all of the columns (except "subjectID" and "activity") "Average of ...(measurement)".
11. Prints the dimensions of the resulting "avgMeasurements" data frame for a qc check (Should be 180 x 88).
12. Creates two new TIDY datasets in .txt format for future analysis, placing them in the users workspace.
## The original README file of the study that created the datasets

# The original README of the wearables datasets is as follows:

==================================================================
Human Activity Recognition Using Smartphones Dataset
Version 1.0
==================================================================
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Università degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws
==================================================================

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details. 

For each record it is provided:
======================================

- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

The dataset includes the following files:
=========================================

- 'README.txt'

- 'features_info.txt': Shows information about the variables used on the feature vector.

- 'features.txt': List of all features.

- 'activity_labels.txt': Links the class labels with their activity name.

- 'train/X_train.txt': Training set.

- 'train/y_train.txt': Training labels.

- 'test/X_test.txt': Test set.

- 'test/y_test.txt': Test labels.

The following files are available for the train and test data. Their descriptions are equivalent. 

- 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 

- 'train/Inertial Signals/total_acc_x_train.txt': The acceleration signal from the smartphone accelerometer X axis in standard gravity units 'g'. Every row shows a 128 element vector. The same description applies for the 'total_acc_x_train.txt' and 'total_acc_z_train.txt' files for the Y and Z axis. 

- 'train/Inertial Signals/body_acc_x_train.txt': The body acceleration signal obtained by subtracting the gravity from the total acceleration. 

- 'train/Inertial Signals/body_gyro_x_train.txt': The angular velocity vector measured by the gyroscope for each window sample. The units are radians/second. 

Notes: 
======
- Features are normalized and bounded within [-1,1].
- Each feature vector is a row on the text file.

For more information about this dataset contact: activityrecognition@smartlab.ws

License:
========
Use of this dataset in publications must be acknowledged by referencing the following publication [1] 

[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012

This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.

Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita. November 2012.

# The functionality of "run_analysis.R"

1. Begins by defining the internet source of the wearables datasets.
2. If the datasets do not already exist on the local directory, downloads and unzips the file leading to the datasets.
3. Ensures the proper R-packages are in place for code to run correctly.  This includes the "dplyr" and "reshape2" packages.
4. Summons the "features" variable into a 561 x 1 data frame.  Builds a vector for quickly selecting only the features variables that corresponds to mean and standard deviation.
5. Summons the sampled "train" values, X_train, into a 7352 x 86 data frame.  Summons y_train "activity" variable into a 7352 x 1 data frame.  Summons the subjTrain "subject" variable into a 7352 x 1 data frame.  Binds the subject and activity columns to the X_train data frame for a single "train" data frame with dimensions 7352 x 88.
6. Summons the sampled "test" values, X_test, into a 2947 x 86 data frame.   Summons the y_test "activity" variable into a 2947 x 1 data frame.  Summons the subjTest "subject" variable into a 2947 x 1 data frame.  Binds the subject and activity columns to the X_test data frame for a single  "test" data frame with dimensions 2947 x 88.
7. Merges the train and test data frames into a single 10299 x 88 data frame and names the columns. Note:  The function Uses gsub to remove the "()" and "-" characters from the column names.
8. Summons the activity-labels vector, and replaces the numbers in the "activity" column with their corresponding labels.  Also re-arranges the dataset:  first by subjectID, then by activity.
9.  Prints the dimensions of the resulting "test_train" data frame for a qc check (Should be 10299 x 88).
10. Creates a new tidy dataset of the average value per subject and activity.  Names all of the columns (except "subjectID" and "activity") "Average of ...(measurement)".
11. Prints the dimensions of the resulting "avgMeasurements" data frame for a qc check (Should be 180 x 88).
12. Creates two new TIDY datasets in .txt format for future analysis, placing them in the users workspace.
