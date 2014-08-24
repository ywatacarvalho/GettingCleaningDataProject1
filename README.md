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

The R scripts are below:

    rm(list=ls());
    
    library(reshape2);
    library(plyr);
    library(stringr);
    
    getwd();
    
    setwd("C:/Alex/AulasWEB/GettingCleaningData/Project1");
    
    if (!file.exists("data")) #checking if directory exists
    {
      dir.create("data"); #create directory
    }
    
    y_test <- read.table("./data/test/y_test.txt", header = FALSE);
    y_test <- rename(y_test, c("V1" = "label"));
    
    obs <- 1:nrow(y_test);
    
    subject_test <- read.table("./data/test/subject_test.txt", header = FALSE);
    subject_test <- rename(subject_test, c("V1"="individuo"));
    subject_test$sample <- "test";
    subject_test <- cbind(obs, subject_test, y_test);
    
    subject_test[subject_test$label == 1, "activity"] <- "Walking";
    subject_test[subject_test$label == 2, "activity"] <- "Walking upstairs";
    subject_test[subject_test$label == 3, "activity"] <- "Walking downstairs";
    subject_test[subject_test$label == 4, "activity"] <- "Sitting";
    subject_test[subject_test$label == 5, "activity"] <- "Standing";
    subject_test[subject_test$label == 6, "activity"] <- "Laying";
    
    subject_test$activity <- as.factor(subject_test$activity);
    table(subject_test$activity)
    
    x_test <- read.table("./data/test/x_test.txt", header = FALSE);
    x_test <- cbind(subject_test, x_test);
    
    y_train <- read.table("./data/train/y_train.txt", header = FALSE);
    y_train <- rename(y_train, c("V1" = "label"));
    
    obs <- 1:nrow(y_train);
    
    subject_train <- read.table("./data/train/subject_train.txt", header = FALSE);
    subject_train <- rename(subject_train, c("V1"="individuo"));
    subject_train$sample <- "train";
    subject_train <- cbind(obs, subject_train, y_train);
    
    subject_train[subject_train$label == 1, "activity"] <- "Walking";
    subject_train[subject_train$label == 2, "activity"] <- "Walking upstairs";
    subject_train[subject_train$label == 3, "activity"] <- "Walking downstairs";
    subject_train[subject_train$label == 4, "activity"] <- "Sitting";
    subject_train[subject_train$label == 5, "activity"] <- "Standing";
    subject_train[subject_train$label == 6, "activity"] <- "Laying";
    
    subject_train$activity <- as.factor(subject_train$activity);
    table(subject_train$activity)
    
    x_train <- read.table("./data/train/x_train.txt", header = FALSE);
    x_train <- cbind(subject_train, x_train);
    
    consol_data_all_vars <- rbind(x_train, x_test);
    
    features <- read.table("./data/features.txt", header = FALSE)
    features_selected <- features[grepl("mean()", features$V2) | grepl("std()", features$V2),];
    features_selected <- features_selected[!grepl("meanFreq", features_selected$V2),];
    features_selected$variaveis <- paste("V", features_selected$V1, sep="");
    features_selected$var_names <- gsub("-", "_", features_selected$V2);
    features_selected$var_names <- sub(")", "", features_selected$var_names)
    features_selected$var_names <- str_replace(features_selected$var_names, "[(]", "");
    
    lista1 <- c("obs", "individuo", "sample", "label", "activity");
    lista2 <- features_selected$variaveis;
    lista <- c(lista1, lista2);
    
    consol_data <- consol_data_all_vars[, lista];
    
    nomes_old <- features_selected$variaveis;
    nomes_new <- features_selected$var_names;
    
    for (i in 1:length(nomes_old))
    {
        names(consol_data)[names(consol_data) == nomes_old[i]] <- nomes_new[i];
    }
    
    consol_data_melt <- melt(consol_data, id = lista1, measure.vars = nomes_new);
    
    consol_data_means <- dcast(consol_data_melt, individuo * activity ~ variable, mean);
    
    write.table(consol_data_means, "./data/tidy_data_with_variable_averages.txt", row.names = FALSE);
    
    #load_data_teste <- read.table("./data/tidy_data_with_variable_averages.txt", header = TRUE);
    
