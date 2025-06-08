# Report: Predict Bike Sharing Demand with AutoGluon Solution
Narges Golmohammadi

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
When submitting, I realized some predicted count values were negative, which Kaggle doesn't allow. I fixed this by clipping predictions to be ≥ 0. I also made sure the submission file matched Kaggle’s format by keeping the datetime column and replacing the count column with the predictions.

### What was the top ranked model that performed?
basd on my codes, the best model was the last one which is predictor_new_hpo

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
The exploratory analysis showed that bike rental demand varies by time — especially by hour of the day, day of the week, and month. To capture these patterns, I extracted new features from the datetime column, including hour, day, month, and weekday. These helped the model learn time-based trends in user behavior and significantly improved prediction performance. also, I dropped two features: registered and casual so that train and test are in the same dimensions.

### How much better did your model preform after adding additional features and why do you think that is?
After adding time-based features like hour, day, and weekday, my model's Kaggle RMSE improved from 1.81560 to 0.9140, based on Kaggle evaluation, a significant boost. This likely happened because bike rental demand strongly depends on the time of day and day of the week, and the model was able to capture these patterns once they were explicitly included as features.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
After tuning hyperparameters, the Kaggle RMSE improved from 0.91408 to 0.46108. This improvement suggests that optimizing settings like learning_rate, num_boost_round, and max_depth helped the model generalize better and make more accurate predictions.

### If you were given more time with this dataset, where do you think you would spend more time?
I would focus on engineering more advanced features, such as weather interactions, holiday indicators, and rush-hour flags. Additionally, I’d analyze prediction errors to better understand where the model struggles.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|learning_rate=0.05|num_boost_round=100|max_depth=None|1.81560|
|add_features|learning_rate=0.05|num_boost_round=100|max_depth=None|0.91408|
|hpo|learning_rate=0.01|num_boost_round=300|max_depth=6|0.46108|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.
![image](https://github.com/user-attachments/assets/66720ab7-02c9-40e9-983f-e466a2f3727a)


### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![image](https://github.com/user-attachments/assets/fe456d08-e111-4e51-b300-3d46bca41da9)

## Summary
In this project, I used AutoGluon to predict bike-sharing demand based on historical data. I began with a baseline model, then improved it by engineering time-based features (such as hour, day, and weekday) and casting categorical variables properly. This significantly improved the Kaggle score from 1.81560 to 0.91408.

Next, I applied hyperparameter tuning, which further reduced the Kaggle RMSE to 0.46108. Through this process, I learned the importance of feature engineering, the impact of model tuning, and the difference between validation scores and real-world generalization. With more time, I would explore interaction features, advanced ensembling, and deeper error analysis.
