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