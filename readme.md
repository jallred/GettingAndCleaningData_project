Project goal

The class was tasked with taking two sets of data (testing and training) which contained 
several variables containing accelerometer and gyro data for several subjects, each of 
which were accomplishing several tasks.

R script description

The script created the tidy data for this project in the following manner:

1. set the right libraries and the working directory. careful with the library order

library(plyr)
library(dplyr)
setwd("~/Documents/coursera/Data Science/Getting and Cleaning Data/UCI HAR Dataset")

2. read the raw testing and training data

test_raw <- read.table("test/X_test.txt")
train_raw <- read.table("train/X_train.txt")

3. read the features, then tidy up the feature names -- replace commas by underscores 

features_raw <- read.table("features.txt")
features <- gsub(",","_",features)

4. apply the tidied feature names to the raw data

names(test_raw) <- features
names(train_raw) <- features

5. we're tasked to process the mean and standard deviation data, so search for columns
with the right names (mean or std). Discard the duplicates.

uniq_columns <- unique(features)

relevant_col_names <- uniq_columns[grepl("(mean|std)",uniq_columns,ignore.case=TRUE)]
test_processed  <- test_raw[,relevant_col_names];
train_processed  <- train_raw[,relevant_col_names];

6. extract the activity names

activities <- read.table("activity_labels.txt",as.is=TRUE)
activities <- activities$V2

7. for testing and training data, create subject and activity names

subject_test <- read.table("test/subject_test.txt")
Y_test <- read.table("test/Y_test.txt")
Y_test_final <- mutate(Y_test,Subject=as.character(subject_test$V1), Activity = factor(V1, labels = activities))

subject_train <- read.table("train/subject_train.txt")
Y_train <- read.table("train/Y_train.txt")
Y_train_final <- mutate(Y_train,Subject=as.character(subject_train$V1), Activity = factor(V1, labels = activities))

8. join subject and activites titles on testing and training data

test_final<- mutate(test_processed, Subject=Y_test_final$Subject, Activity = as.character(Y_test_final$Activity))
train_final <- mutate(train_processed, Subject=Y_train_final$Subject, Activity = as.character(Y_train_final$Activity))

joined_data <- rbind(train_final, test_final)
final_data <- ddply(train_final,.(Subject,Activity),colwise(mean,is.numeric)) 


Acknowledgements:
A huge thank you to the folks on the forums who gave invaluable hints for some of the more 
difficult parts of the project, and for the codebook examples. Special thanks to David
Hood the Community TA.