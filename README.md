# UGTeleChurnCS
Telecom Churn Case Study

## Table of Contents
* [Objectives](#objectives)
* [Models](#models)
* [Recommendations](#recommendations)
* [Kaggle link](#kaggle-link)

## Objectives
The main goal of the case study is to build ML models to predict churn. The predictive model that you’re going to build will the following purposes:

1. It will be used to predict whether a high-value customer will churn or not - so that the company can take action steps such as providing special plans, discounts on recharge etc.
1. Identify important variables that are strong predictors of churn. 
1. In addition to accuracy, mention other metrics like precision, recall, etc. for the different models that can be used for evaluation purposes based on different business objectives. 
1. Recommend strategies to manage customer churn based on your observations.
  

## Models

||Model|PCA|Accuracy|Churn Recall|No Churn Recall|Accuracy on Test Set|
|---|---|---|---|---|---|---|
|1|__LightGBM__|No|92|__88__|__91__|90.3|
|2|RandomForest|No|93|83|93|91.4|
|3|RandomForest2|No|94|74|97|94.1|
|4|Logistic Regression|No|87|87|84|82.8|
|5|Logistic Regression|Yes|86|87|82|Not Submitted|
  
  
### LightGBM gives best balance between churn and no churn recall over Random Forrest and Logistic Regression
- Using PCA improved training time, but reducded Accuracy
- All models performed better without PCA

### Important metric - recall for churn
- For this case study, we will choose recall as the most important metric
- The data has class imbalance, data for churn is only 10% of available data
- This makes it difficult to predict churn
- Hence the model we choose must have high recall for churn

### Recommended models
__Model 1 - LightGBM__ is recommended for prediction of churn  
We sacrifice overall accuracy to get higher recall for churn_probability  
We will not use PCA, because both models performed better without PCA  


## Recommendations
Overall, the more the user uses the service, lower the chance of churn.
  
|Features|Interpretation|
|---|---|
|All ic, og \_mou_8|Total incoming and outgoing calls of ALL types are low|
|total_rech_amt_8, max_rech_amt_8|Total and max Recharge amout drops|
|last_day_rch_amt_8|Last day recharge amount is zero|
|All \_diff|All \_diff are negative - showing drop in usage compared to last 2 months|
|arpu_8|Average revenue drops|
|date_of_last_rech_8|Days since last recharge are high|
  
All top features are for last month usage.  
Company should monitor last month usage closely.

### Customers who are about the churn have following characteristics:
- low incoming and outgoing mous - overall usage drops
- They have not recharged in the last month
- Previous recharge amounts are also less than other customers
- Average revenue per user is almost zero
- More Days since last recharge show higher churn probability
- All usage indicators are less than other usage indicators

## Kaggle link
[Leaderboard](https://www.kaggle.com/competitions/telecom-churn-case-study-hackathon-C33/leaderboard)

## Contact
Created by [@nvkhedkar] - feel free to contact me!
