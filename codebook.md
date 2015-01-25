Codebook

Feature selection:

tAccXXX and tGyroXXX: Raw data was sampled at 50 Hz from a subject acting in a particular 
	way, and acceleration and gyroscopic data was captured and then filtered to reduce 
	noise.
	
fAccXXX and fGyroXXX: a Fast Fourier transform was performed on the time domain data 
	above, to gain frequency domain data for each subject and action.


Data Dictionary 

Variable	Description		Values	Value Explanation

Subject     Subject ID 		1->N	ID for each subject

Activity    Activity ID     1		WALKING
                            2		WALKING_UPSTAIRS
                            3		WALKING_DOWNSTAIRS
                            4		SITTING
                            5		STANDING
                            6		LAYING

tBodyAccmeanX           	-1->+1	normalized mean body acceleration in the X direction       
tBodyAccmeanY           	(below variables are similar)
tBodyAccmeanZ          
tBodyAccstdX
tBodyAccstdY
tBodyAccstdZ
tGravityAccmeanX      
tGravityAccmeanY        
tGravityAccmeanZ              
tGravityAccstdX
tGravityAccstdY
tGravityAccstdZ         
tBodyAccJerkmeanX
tBodyAccJerkmeanY
tBodyAccJerkmeanZ
tBodyAccJerkstdX
tBodyAccJerkstdY
tBodyAccJerkstdZ
tBodyGyromeanX
tBodyGyromeanY
tBodyGyromeanZ
tBodyGyrostdX
tBodyGyrostdY
tBodyGyrostdZ
tBodyGyroJerkmeanX
tBodyGyroJerkmeanY
tBodyGyroJerkmeanZ
tBodyGyroJerkstdX
tBodyGyroJerkstdY
tBodyGyroJerkstdZ
tBodyAccMagmean
tBodyAccMagstd
tGravityAccMagmean
tGravityAccMagstd
tBodyAccJerkMagmean
tBodyAccJerkMagstd
tBodyGyroMagmean
tBodyGyroMagstd
tBodyGyroJerkMagmean
tBodyGyroJerkMagstd
fBodyAccmeanX
fBodyAccmeanY
fBodyAccmeanZ
fBodyAccstdX
fBodyAccstdY
fBodyAccstdZ
fBodyAccmeanFreqX
fBodyAccmeanFreqY
fBodyAccmeanFreqZ
fBodyAccJerkmeanX
fBodyAccJerkmeanY
fBodyAccJerkmeanZ
fBodyAccJerkstdX
fBodyAccJerkstdY
fBodyAccJerkstdZ
fBodyAccJerkmeanFreqX
fBodyAccJerkmeanFreqY
fBodyAccJerkmeanFreqZ
fBodyGyromeanX
fBodyGyromeanY
fBodyGyromeanZ
fBodyGyrostdX
fBodyGyrostdY
fBodyGyrostdZ
fBodyGyromeanFreqX
fBodyGyromeanFreqY
fBodyGyromeanFreqZ
fBodyAccMagmean
fBodyAccMagstd
fBodyAccMagmeanFreq
fBodyBodyAccJerkMagmean
fBodyBodyAccJerkMagstd
fBodyBodyAccJerkMagmeanFreq
fBodyBodyGyroMagmean
fBodyBodyGyroMagstd
fBodyBodyGyroMagmeanFreq
fBodyBodyGyroJerkMagmean
fBodyBodyGyroJerkMagstd
fBodyBodyGyroJerkMagmeanFreq
angletBodyAccMean_gravity
angletBodyAccJerkMean_gravityMean
angletBodyGyroMean_gravityMean
angletBodyGyroJerkMean_gravityMean
angleX_gravityMean
angleY_gravityMean
angleZ_gravityMean