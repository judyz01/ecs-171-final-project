# ECS 171 Final Project

## Data Exploration Step
There are 241 observations. Male:female, student:faculty, percent-financial-aid, and percent-enrolled are all normally distributed. The distribution for sat verbal and sat math are bimodal. We have two peaks (0 and 500/600). We believe 0 means the school doesn't accept SAT score, so it makes sense that they are bimodal. The distribution for percent-admittance is left skewed. And the 3 classes we have are all multimodal distributed.

The scale for male:female is 0 to 1, 0 means all students are female and 1 means all students are male. The scale for student:faculty is also 0 to 1. The scales for the two SAT scores are 0 to 800. The scales for the 3 percentage we have are all 0 to 100. The values for our classes are 0 to 5 (5 means the best).

We updated the male:female feature from ratio to percentage. The new definition for male:female feature is how many % of students in this school are males. The new definition for student:faculty feature is how many % of people in this school are students.

## Data Preprocessing Step
We already imputed our data (we replaced NA or other invalid values with most frequent values. For one feature, we used Google to get the missing values). Since most of the data are normally distributed, we plan to scale our data using normalization and standardization. We also plan to encode our features (state, control, no-of-students, expenses, and no-applicants) using value replacement.
