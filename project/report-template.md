# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Javdaneh Nooshi

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
I used predictor.describe() to check the minimum values, to ensure there are no negative values. I also included the datetime column as well as the counts in the submission, as shown in the kaggle example.


### What was the top ranked model that performed?
Looking at predictor.leaderboard(), the best ranking model appeared to be WeightedEnsemble_L3.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
I did the exploratory analysis by first creating a histogram of the features - this showed the distribution of each feature, and was useful in highlighting any extreme outliers, and showing that we have a mix of features, some of which show a relatively normal distribution (atemp), bimodal (workingday and holiday), and skewed (count). 
For adding additional features, I separated out the datetime features into month and year, to give a better idea of how the demand changes depending on the month, and any trends over the years.

### How much better did your model preform after adding additional features and why do you think that is?
I was expecting a greater change in my model performance after adding more features, but I only saw a difference of 0.101% - it might be due to an error on my part, or the way I added the new features, this would require a more detailed analysis. 

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
Following Hyper parameter tuning, the model performed better, having an increase in accuracy of ~8% (1.44560 for initial, compared to 1.33722 score in the final). This could potentially be further improved by testing alternative AutoGluon higher level parameters.

### If you were given more time with this dataset, where do you think you would spend more time?
It would be useful to spend more time on exploratory data analysis, as I would like to really understand the data and find any outliers that might affect the model preformance. This might also have helped in identifying more interesting features, that I could have included in the second run of the model to provide better data insights. I  would also like to spend more time identifying why the model scores did not change much after adding more features. 

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|train_data|eval_metric|Presets|1.44560|
|add_features|train_new_cols|eval_metric|presets|1.44414|
|hpo|train_new_cols|eval_metric|hyperparameter_tune_kwargs|1.33722|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

![model_train_score.png](model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![model_test_score.png](model_test_score.png)

## Summary

