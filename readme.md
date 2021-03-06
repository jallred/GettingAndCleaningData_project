Project goal

The class was tasked with taking two sets of data (testing and training) which contained 
several variables containing accelerometer and gyro data for several subjects, each of 
which were accomplishing designated tasks. The testing and training data sets were joined. 
Then, the mean and standard deviation of each measurement for each subject and activity 
was extracted and added to the tidy data.

R script description

The script created the tidy data for this project in the following manner:

#### set the right libraries and the working directory. careful with the library order

```R
library(plyr)

library(dplyr)

setwd("~/Documents/coursera/Data Science/Getting and Cleaning Data/UCI HAR Dataset")
```

#### read the raw testing and training data
```R
test_raw <- read.table("test/X_test.txt")

train_raw <- read.table("train/X_train.txt")
```
#### read the features, then tidy up the feature names -- replace commas by underscores to avoid csv data issues later 
```R
features_raw <- read.table("features.txt")

features <- gsub(",","_",features)
```
#### apply the modified feature names to the raw data
```R
names(test_raw) <- features

names(train_raw) <- features
```
#### we're tasked to process the mean and standard deviation data, so search for columns with the right names (mean or std). Discard the duplicates.
```R
uniq_columns <- unique(features)

relevant_col_names <- uniq_columns[grepl("(mean|std)",uniq_columns,ignore.case=TRUE)]

test_processed  <- test_raw[,relevant_col_names];

train_processed  <- train_raw[,relevant_col_names];
```
#### extract the activity names
```R
activities <- read.table("activity_labels.txt",as.is=TRUE)
activities <- activities$V2
```
#### for testing and training data, create subject and activity names
```R
subject_test <- read.table("test/subject_test.txt")

Y_test <- read.table("test/Y_test.txt")

Y_test_final <- mutate(Y_test,Subject=as.character(subject_test$V1), Activity = factor(V1, labels = activities))

subject_train <- read.table("train/subject_train.txt")

Y_train <- read.table("train/Y_train.txt")

Y_train_final <- mutate(Y_train,Subject=as.character(subject_train$V1), Activity = factor(V1, labels = activities))
```
#### join subject and activites titles on testing and training data
```R
test_final<- mutate(test_processed, Subject=Y_test_final$Subject, Activity = as.character(Y_test_final$Activity))

train_final <- mutate(train_processed, Subject=Y_train_final$Subject, Activity = as.character(Y_train_final$Activity))

joined_data <- rbind(train_final, test_final)

final_data <- ddply(train_final,.(Subject,Activity),colwise(mean,is.numeric)) 
```

Acknowledgements:
A huge thank you to the folks on the forums who gave invaluable hints for some of the more 
difficult parts of the project, and for the codebook examples. Special thanks to David
Hood the Community TA.