# Project-4-Predicting-Insulin-Prescriptions

## Introduction
The CDC's NHANES (National Health and Nutrition Examination Study) study is a wealth of information taken from approximately 5,000 participants. This includes data regarding participant diet, prescriptions taken, results of a physical exam and demographic information. The datasets of particular interest in this project are the dietary factors and prescriptions taken. The goal is to use machine learning to predict whether a participant takes insulin or not. The results can be used by a clinician to help predict those who may be at risk of requiring an insulin prescription based on their dietary factors. It is important to note, I am not a physician and this should not be construed medical advice. This is a data science project intended to assist clinicians.  

This dataset was retrieved from Kaggle at the following URL:  

 https://www.kaggle.com/cdc/national-health-and-nutrition-examination-survey#diet.csv
## Included in this Repository
This repository contains:
1. A Jupyter notebook detailing the specific code written
2. The .csv files for all of datasets included in the 2013-2014 NHANES study
3. A .gslides slide deck detailing the main takeaways of this analysis
## Data Cleaning
For this project, the diet.csv and medications.csv were used. The first step in the process was to clean the data. First, in order to suit our purposes, a new feature was created to encode whether a patient was on insulin or not. Due to the nature of the input, there were a lot of null values that were converted to zeros. A new dataframe was engineered that included all of a participants dietary factors and the binary insulin column. 
## Experimenting with several models
Several machine learning algorithms were chosen and evaluated for their efficiency in predicting if a participant took insulin. Due to the unbalanced nature of the dataset (only 2% of participants had an insulin prescription), the F1 score was used to evaluate the model rather than the accuracy score.  
Random Forest Classifier F1 Score: 0.05  
K Nearest Neighbors F1 Score: 0.0  
XGBoost F1 Score: 0.06  
To help adjust for the unbalanced data, the Random Forest Classifier was attempted twice- once with class_weight = Default and once with class_weight = balanced. The higher score is with the balanced class weight.  
For the K Nearest Neighbors, a range of 1 to 30 n_estimators was attemped, however each F1 score returned 0.0.  
## Choosing a best performing model and tuning hyperparameters
Choosing to use the XGBoost model, several hyperparamters were tuned using GridSearchCV which yielded a 4.9% increase in F1 score. 
## Removing 'Cheat' features
Because the effect of sugar consumption on blood glucose is well known, several features regarding low or high sugar diets and sugar consumption in grams was omitted to explore if there was any further knowledge to be gleaned. However, the model did not perform well enough to confidently identify other factors. 
## Repeating the process with Glipizide
Insulin is prescribed to both Type 1 and Type 2 diabetics. Therefore, in the interest of exploration, the process was repeated for a popular anti-diabetic drug, Glipizide. The model that performed best was a K Nearest Neighbors. This was tuned and yielded an F1 score of 0.04. 
## Ideas for future work
Some considerations for further exploration:  
1. Using a method to balance the data such as SMOTE to return more accurate models. 
2. Look into feature importance of the Glipizide model 
3. Consider other ways to solve the same problem using the given dataset- for example, could blood insulin levels or diagnosis codes yield a more accurate result? 
