Code book for the steps performed to create the requested tidy data
=======================================================================

The program in R executes the following steps to prepare the tidy data requested:

      1. I registered the libraries to be used and the path for the files;
      2. I read the txt files: subject_test.txt, subject_train.txt, x_test.txt, y_test.txt, features.txt
      3. For the labels based on the y files, I assigned the activities names
      4. I merged the data sets for test and train data, using rbind()
      5. Based on the measures on the features.txt file, I selected only the features containing mean() or std()
      6. I used the list from the previous step to select only the columns corresponding to the selected features (mean and standard deviation)
      7. For the features description, I replaced "-" by "_" and removed the "()" strings from the descriptions to create valid variable names
      8. I renamed all variables originally imported (V1, V2, ...) by the new names created in the previous step
      9. After steps 1 to 8, I had a merged table, with train and test sets, with variables with proper description and activities also with their description (from the activity_labels.txt file)
      10. I applied the melt command and then the dcast command to create the tidy data, with averages for the selected columns, by subject (column 'individuo') and by activity. 

The variables created in the tidy data are the following:

    variable 'individuo' corresponds to the subject identification number
    varlable 'activity' corresponds to the recorded activity
    variable 'tBodyAcc_mean_X' corresponds to the average of feature 'tBodyAcc-mean()-X'
    variable 'tBodyAcc_mean_Y' corresponds to the average of feature 'tBodyAcc-mean()-Y'
    variable 'tBodyAcc_mean_Z' corresponds to the average of feature 'tBodyAcc-mean()-Z'
    variable 'tBodyAcc_std_X' corresponds to the average of feature 'tBodyAcc-std()-X'
    variable 'tBodyAcc_std_Y' corresponds to the average of feature 'tBodyAcc-std()-Y'
    variable 'tBodyAcc_std_Z' corresponds to the average of feature 'tBodyAcc-std()-Z'
    variable 'tGravityAcc_mean_X' corresponds to the average of feature 'tGravityAcc-mean()-X'
    variable 'tGravityAcc_mean_Y' corresponds to the average of feature 'tGravityAcc-mean()-Y'
    variable 'tGravityAcc_mean_Z' corresponds to the average of feature 'tGravityAcc-mean()-Z'
    variable 'tGravityAcc_std_X' corresponds to the average of feature 'tGravityAcc-std()-X'
    variable 'tGravityAcc_std_Y' corresponds to the average of feature 'tGravityAcc-std()-Y'
    variable 'tGravityAcc_std_Z' corresponds to the average of feature 'tGravityAcc-std()-Z'
    variable 'tBodyAccJerk_mean_X' corresponds to the average of feature 'tBodyAccJerk-mean()-X'
    variable 'tBodyAccJerk_mean_Y' corresponds to the average of feature 'tBodyAccJerk-mean()-Y'
    variable 'tBodyAccJerk_mean_Z' corresponds to the average of feature 'tBodyAccJerk-mean()-Z'
    variable 'tBodyAccJerk_std_X' corresponds to the average of feature 'tBodyAccJerk-std()-X'
    variable 'tBodyAccJerk_std_Y' corresponds to the average of feature 'tBodyAccJerk-std()-Y'
    variable 'tBodyAccJerk_std_Z' corresponds to the average of feature 'tBodyAccJerk-std()-Z'
    variable 'tBodyGyro_mean_X' corresponds to the average of feature 'tBodyGyro-mean()-X'
    variable 'tBodyGyro_mean_Y' corresponds to the average of feature 'tBodyGyro-mean()-Y'
    variable 'tBodyGyro_mean_Z' corresponds to the average of feature 'tBodyGyro-mean()-Z'
    variable 'tBodyGyro_std_X' corresponds to the average of feature 'tBodyGyro-std()-X'
    variable 'tBodyGyro_std_Y' corresponds to the average of feature 'tBodyGyro-std()-Y'
    variable 'tBodyGyro_std_Z' corresponds to the average of feature 'tBodyGyro-std()-Z'
    variable 'tBodyGyroJerk_mean_X' corresponds to the average of feature 'tBodyGyroJerk-mean()-X'
    variable 'tBodyGyroJerk_mean_Y' corresponds to the average of feature 'tBodyGyroJerk-mean()-Y'
    variable 'tBodyGyroJerk_mean_Z' corresponds to the average of feature 'tBodyGyroJerk-mean()-Z'
    variable 'tBodyGyroJerk_std_X' corresponds to the average of feature 'tBodyGyroJerk-std()-X'
    variable 'tBodyGyroJerk_std_Y' corresponds to the average of feature 'tBodyGyroJerk-std()-Y'
    variable 'tBodyGyroJerk_std_Z' corresponds to the average of feature 'tBodyGyroJerk-std()-Z'
    variable 'tBodyAccMag_mean' corresponds to the average of feature 'tBodyAccMag-mean()'
    variable 'tBodyAccMag_std' corresponds to the average of feature 'tBodyAccMag-std()'
    variable 'tGravityAccMag_mean' corresponds to the average of feature 'tGravityAccMag-mean()'
    variable 'tGravityAccMag_std' corresponds to the average of feature 'tGravityAccMag-std()'
    variable 'tBodyAccJerkMag_mean' corresponds to the average of feature 'tBodyAccJerkMag-mean()'
    variable 'tBodyAccJerkMag_std' corresponds to the average of feature 'tBodyAccJerkMag-std()'
    variable 'tBodyGyroMag_mean' corresponds to the average of feature 'tBodyGyroMag-mean()'
    variable 'tBodyGyroMag_std' corresponds to the average of feature 'tBodyGyroMag-std()'
    variable 'tBodyGyroJerkMag_mean' corresponds to the average of feature 'tBodyGyroJerkMag-mean()'
    variable 'tBodyGyroJerkMag_std' corresponds to the average of feature 'tBodyGyroJerkMag-std()'
    variable 'fBodyAcc_mean_X' corresponds to the average of feature 'fBodyAcc-mean()-X'
    variable 'fBodyAcc_mean_Y' corresponds to the average of feature 'fBodyAcc-mean()-Y'
    variable 'fBodyAcc_mean_Z' corresponds to the average of feature 'fBodyAcc-mean()-Z'
    variable 'fBodyAcc_std_X' corresponds to the average of feature 'fBodyAcc-std()-X'
    variable 'fBodyAcc_std_Y' corresponds to the average of feature 'fBodyAcc-std()-Y'
    variable 'fBodyAcc_std_Z' corresponds to the average of feature 'fBodyAcc-std()-Z'
    variable 'fBodyAccJerk_mean_X' corresponds to the average of feature 'fBodyAccJerk-mean()-X'
    variable 'fBodyAccJerk_mean_Y' corresponds to the average of feature 'fBodyAccJerk-mean()-Y'
    variable 'fBodyAccJerk_mean_Z' corresponds to the average of feature 'fBodyAccJerk-mean()-Z'
    variable 'fBodyAccJerk_std_X' corresponds to the average of feature 'fBodyAccJerk-std()-X'
    variable 'fBodyAccJerk_std_Y' corresponds to the average of feature 'fBodyAccJerk-std()-Y'
    variable 'fBodyAccJerk_std_Z' corresponds to the average of feature 'fBodyAccJerk-std()-Z'
    variable 'fBodyGyro_mean_X' corresponds to the average of feature 'fBodyGyro-mean()-X'
    variable 'fBodyGyro_mean_Y' corresponds to the average of feature 'fBodyGyro-mean()-Y'
    variable 'fBodyGyro_mean_Z' corresponds to the average of feature 'fBodyGyro-mean()-Z'
    variable 'fBodyGyro_std_X' corresponds to the average of feature 'fBodyGyro-std()-X'
    variable 'fBodyGyro_std_Y' corresponds to the average of feature 'fBodyGyro-std()-Y'
    variable 'fBodyGyro_std_Z' corresponds to the average of feature 'fBodyGyro-std()-Z'
    variable 'fBodyAccMag_mean' corresponds to the average of feature 'fBodyAccMag-mean()'
    variable 'fBodyAccMag_std' corresponds to the average of feature 'fBodyAccMag-std()'
    variable 'fBodyBodyAccJerkMag_mean' corresponds to the average of feature 'fBodyBodyAccJerkMag-mean()'
    variable 'fBodyBodyAccJerkMag_std' corresponds to the average of feature 'fBodyBodyAccJerkMag-std()'
    variable 'fBodyBodyGyroMag_mean' corresponds to the average of feature 'fBodyBodyGyroMag-mean()'
    variable 'fBodyBodyGyroMag_std' corresponds to the average of feature 'fBodyBodyGyroMag-std()'
    variable 'fBodyBodyGyroJerkMag_mean' corresponds to the average of feature 'fBodyBodyGyroJerkMag-mean()'
    variable 'fBodyBodyGyroJerkMag_std' corresponds to the average of feature 'fBodyBodyGyroJerkMag-std()'
