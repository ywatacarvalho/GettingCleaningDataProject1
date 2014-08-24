GettingCleaningDataProject1
===========================

Repository with files for Project 1 of the Gettting and Cleaning Data Course

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
