### Human Activity Recognition Using Smartphones Dataset, Version 1.0
The `run_analysis.R` script is used to prepare the data as defined in the course project.

#### Download and extract the dataset
The file downloaded represent data collected from the accelerometers from the Samsung Galaxy S smartphone, the data was saved in a file called `projectfiles_UCI_HAR_Dataset`, and extracted under the folder called `UCI HAR Dataset`.

For each record it is provided:
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.

#### Read the dataset
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
- `features`: List of all features.
- `activity_labels`: Links the class labels with their activity name.

** The following data are available for the train and test data (`subject_test`, `X_test` and `y_test`). Their descriptions are equivalent. **
- `subject_train`: Each row identifies the subject who performed the activity for each window sample.
- `X_train`: Training set, with features names included as a column names.
- `y_train`: Contains training labels of activities code labels.

#### Merges the training and the test sets to create one data set
- `X_data`: Is created by merging `X_train` and `X_test`.
- `y_data`: Is created by merging `y_train` and `y_test`.
- `subject_data`: Is created by merging `subject_train` and `subject_test`.

 **Note:** Merging is done by row binding.
 
### Extracts only the measurements on the mean and standard deviation for each measurement
The means and stds calculated for each measure are selected.
-  `X_mean_std`: Is created by selecting the measurements on the mean and std (standard deviation) for each measurement. 

### Uses descriptive activity names to name the activities in the data set
In `y_data` the activity code labels were replaced by their respective activity name, labels taken from the `activity_labels` variable.

### Appropriately labels the data set with descriptive variable names. 
In the data set `X_mean_std` measures were renamed by more descriptive and complete names, in the code using regular expressions, the abbreviations
for the measure names were found and replaced by their full names (e.g. `Acc` to `Accelerometer`).

### From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.
- `all_data`: contains the entire data set and is created by merging `X_mean_std`, `y_data` and `subject_data` using `bind_cols()` function
- `tidy_data`: is created by grouping the data set `all_data` by activity and subject, then summarizing `all_data` taking the means of each variable
for each activity and each subject.

The final dataset (`tidy_data`) is exported into `tidy_data.csv` file
