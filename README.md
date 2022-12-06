# ECS 171 Final Project

## Data Exploration Step
There are 241 observations. Male:female, student:faculty, percent-financial-aid, and percent-enrolled are all normally distributed. The distribution for sat verbal and sat math are bimodal. We have two peaks (0 and 500/600). We believe 0 means the school doesn't accept SAT score, so it makes sense that they are bimodal. The distribution for percent-admittance is left skewed. And the 3 classes we have are all multimodal distributed.

The scale for male:female is 0 to 1, 0 means all students are female and 1 means all students are male. The scale for student:faculty is also 0 to 1. The scales for the two SAT scores are 0 to 800. The scales for the 3 percentage we have are all 0 to 100. The values for our classes are 0 to 5 (5 means the best).

We updated the male:female feature from ratio to percentage. The new definition for male:female feature is how many % of students in this school are males. The new definition for student:faculty feature is how many % of people in this school are students.

## Data Preprocessing Step
We imputed our data (we replaced NA or other invalid values with most frequent values. For one feature, we used Google to get the missing values). Since most of the data are normally distributed, we plan to scale our data using normalization and standardization. We also plan to encode our features (state, control, no-of-students, expenses, and no-applicants) using value replacement.

In the second milestone, we also used MinMaxScaler to scale to following features: `sat verbal, sat math, percent-admittance`. And we used StandardScaler to scale to scale the following features `percent-financial-aid, percent-enrolled`. We used StandardScaler for the last two features because they are normally distributed.

We also encoded our data using the following mappings.

```
control
private: 0, state: 1, city: 2

no-of-students
thous:5-: 0, thous:5-10: 1, thous:10-15: 2, thous:15-20: 3, thous:20+: 4

expenses
thous$:4-: 0, thous$:4-7: 1, thous$:7-10: 2, thous$:10+: 3

no-applicants
thous:4-: 0, thous:4-7: 1, thous:7-10: 2, thous:10-13: 3, thous:13-17: 4, thous:17+: 5

academics scale:1-5, social scale:1-5, and quality-of-life scale:1-5
1-2: 0, 3-5: 1
```

## First Model Evaluation

Our first model is a LogisticRegression model. Value >= 0.5 means it belong to class 1 (good), value < 0.5 means it belong to class 0 (bad).

We see no sign of overfitting. For academics class, the training MSE is 0.190 and the testing MSE is 0.219. For quality-of-life class, the training MSE is 0.298 vs testing MSE 0.301.
Testing MSE are higher than training MSE, but the errors are very small.
For our second class (social), testing MSE (0.233) is lower than the training MSE (0.304).
However, since the both training and testing MSE are higher than our expected error, perhaps this is a sign of underfitting.
Overall, we can conclude that our models are between underfitting range and ideal range range.

==================

## A. Introduction 
There are more than 4,000 higher-education institutions within the United States. Due to the sheer number of institutions and unique students, it becomes difficult to individually assess each universities’ performance manually. 

By using the University Dataset from UCI’s Machine Learning Repository, we aim to visualize and present the correlation between attributes such as SAT scores, the number of applicants who were admitted, enrolled, and attended, as well as the student-faculty ratio to predict the academic/social performance, as well as the quality-of-life from each university. The analysis will use supervised learning with classification and regression models to determine the correlation/predictions as mentioned above.

By utilizing the University Dataset and the ANN model we have created, it is possible to discover a correlation between a universities’ reported social atmosphere, academic life, and overall quality of life within the respective university depending on features such as the reported SAT scores, student-faculty ratio, male-to-female ratio, etc. As a result, this would be especially important for students who are applying to various universities to find correlations regarding the university’s environment compared to their average statistics, as it could influence their decisions on which university to attend based on their own relevant statistics, their personal preferences, and so on.

## B. Methods
a. Data Exploration
There are 241 observations. Male:female, student:faculty, percent-financial-aid, and percent-enrolled are all normally distributed. The distribution for sat verbal (Figure 1) and sat math (Figure 2) are bimodal. We have two peaks (0 and 500/600). We believe 0 means the school doesn't accept SAT scores, so it makes sense that they are bimodal. The distribution for percent-admittance is left-skewed (Figure 3). And the 3 classes we have are all multimodal distributed.

The scale for male:female is 0 to 1, 0 means all students are female and 1 means all students are male. The scale for student:faculty is also 0 to 1. The scales for the two SAT scores are 0 to 800. The scales for the 3 percentages we have are all 0 to 100. The values for our classes are 0 to 5 (5 means the best).

We updated the male:female feature from ratio to percentage. The new definition for male:female feature is how many % of students in this school are males. The new definition for student:faculty feature is how many % of people in this school are students.

b. Preprocessing
We imputed our data (we replaced NA or other invalid values with the most frequent values. For one feature, we used Google to get the missing values). Since most of the data are normally distributed, we plan to scale our data using normalization and standardization. We also plan to encode our features (state, control, no-of-students, expenses, and no-applicants) using value replacement.

In the second milestone, we also used MinMaxScaler to scale to the following features: sat verbal, sat math, and percent-admittance. And we used StandardScaler to scale the following features percent-financial-aid, and percent-enrolled. We used StandardScaler for the last two features because they are normally distributed.

c. Model 1
The data for the first model was split into training and testing sets with a 70:30 ratio. We then oversampled the training data using RandomOverSampler before finally creating the Logistic Regression Model.

d. Model 2
Training our second model. We added dense layers with 8 units relu activation, 6 units tanh activation, 6 units sigmoid activation, and 2 units tanh activation to the model, with the last layer being the same sigmoid layer. We split the data into training and testing sets with a ratio of 70:30. Then we oversample the training data. Lastly, an ANN model was built.

## C. Results
a. Logistic Regression Model
Our first model is a LogisticRegression model. Value >= 0.5 means it belongs to class 1 (good), and value < 0.5 means it belongs to class 0 (bad). We see no sign of overfitting. For the academics class, the training MSE is 0.190 and the testing MSE is 0.219 (Figure 4). As for the quality-of-life class, the training MSE is 0.298 vs the testing MSE is 0.301. As we can see from the MSEs above, the testing MSEs are slightly higher than training MSE, as the errors are very small. For our second class (social), the testing MSE (0.233) is lower than the training MSE (0.304). However, since both training and testing MSE are higher than our expected error, this may be a sign of underfitting. Overall, we can conclude that our models are between the underfitting range and the ideal range. Figure 4 below gives a visualization of the training and testing MSEs for each respective class.

b. ANN Model
Our second model is an ANN model. For academics class, the training MSE is 0.160 and the testing MSE is 0.191. For the social class, the training MSE is 0.178 vs the testing MSE is 0.191. For the quality-of-life class, the training MSE is 0.125 vs the testing MSE is 0.301.

In order to visualize the MSE for the respective classes (academics, social, and quality of life), the figures (Figures 5, 6, and 7) below are provided with the training and testing MSEs recorded at Epoch 80, with the following statistics:

Academics
Training MSE: 0.16071428571428573
Testing MSE: 0.1917808219178082

Social
Training MSE: 0.17857142857142858
Testing MSE: 0.1917808219178082

Quality of Life
Training MSE: 0.125
Testing MSE: 0.3013698630136986

## D. Discussion
With all of us being students of UC Davis, we thought it would be a good idea to see if there is a correlation between the schools’ academic/social atmosphere and the schools’ statistics. We chose the University data set and used features such as the number of students, male:female ratio, student:faculty ratio, and many other features to predict academics, social, and quality of life on a scale from 1-5. We chose to target those 3 categories since the quality of the students' life and experiences was what we wanted to understand and interpret. We dropped unnecessary data points such as name and state since those are not as important from an academic and social perspective. After looking through the data, we saw that there was a slight skew in the data results. To fix this, we decided to oversample our data to make it more even. This resulted in a slightly better result in the final version of the models. 

Overall, the results for our model were close to what we expected. There is no sign of overfitting but we did realize that it might be underfitting a bit compared to the ideal range because our MSE is higher than our expected error. This affects our perception of our results since ideally we would want to be more accurate and we could potentially make a better model with greater accuracy. We still believe our results and model were sufficient. Our first model was generally accurate, at around 70%+ accuracy for predicting the academics (78%), social (77%), and quality of life (70%) aspects of students. A higher accuracy would be much favored and we considered that when we created our second model which we decided to make more complex. 

For our second model, we used a neural network that had 5 layers.  We decided to use what seemed to us a more complex model that may end up yielding better results and with our type of data, it was a good fit. Our results were expected where the accuracy was similar and in some cases higher, with predicting academics at 81% accuracy, social quality at 81%, and quality of life at 70%. Our second model in its testing had a higher or equal accuracy compared to the first model. However, something to note is that the accuracy may change for model 2 given that it is nondeterministic while model 1 is deterministic, which in some cases may make model 1 more accurate. We tested with different activation functions and numbers of layers and saw that model yielded the best results. We did not want to make the model too complex as training would take too long and we would get diminishing results. To prevent underfitting or overfitting, we trained the model with different epochs and graphed the training and testing MSE. As the epochs increased, we saw the training mse decrease (Figure 5,6,7). The testing mse was decreasing at first, but after around 80 epochs, we saw the testing mse start to increase. After analyzing the graph, we decided to train our models for 80 epochs. The second model and its results were mostly accurate and we were satisfied with the results. 

Overall, it is pretty believable that our models could accurately predict what the school’s environment would look like based on the statistics of the school. For example, we know intuitively that a school with low acceptance rates and high average SAT scores would have a good academic atmosphere. The models have all the data to make these predictions and were able to pretty accurately predict them, giving us insight into how the quality of life, academics, and social aspects of students may be. 

## E. Conclusion
With the University Data Set, we were able to assess the performance of each of the universities with relatively high accuracy. Though our first model was mostly accurate, we thought there was still space for improvement. So for our second model, we decided to make some changes. We chose to use a neural network for our second model and made it more complex than the first one, which yielded a higher accuracy. For the future, we think the accuracy can be improved more (80%+ across all categories) if we had more thoroughly tested the neural network using a variety of different activation functions and number of layers. Our analysis is all in all accurate at predicting the social and academic performance of universities, which is a good indicator if a university is a good fit for prospective students.

## F. Collaboration Section
Name: Rashed Alrayssi
	Title: Writer
Contribution: Worked on the discussion section of the written part of the assignment. Discussed some parts of choosing possible models for model 1. Helped with some coordination on Discord and editing the final write up. 

Name: Kevin Guan
	Title: Programmer
Contribution: Discussed with the team then turned our idea into Python code. Reviewed final writeup and gave some feedback.

Name: Ferica Ting
	Title: Writer
	Contribution: Worked on the conclusion section of the write-up and proofread/edited 
parts of the writeup.

Name: Whitzer Tsai
	Title: Writer
Contribution: Worked on the methods and results section of the written part. And making some modifications to the final write-up.

Name: Anthony Vu
	Title: Writer/Programmer
	Contribution: Worked on the discussion section of the final write up and did some touch
	up editing on the other sections. Gave feedback on some of the parts. Edited the model
	2 code to include Epoch vs MSE graphs for training and test set.

Name: Judy Zhang
	Title: Writer/Manager
Contribution: Worked on the introduction section of the write-up as well as added the figures for the write-up. Also coordinated team members with the sections of the project they wished to work on while creating the necessary shared resources (repo/shared docs) for the project.
