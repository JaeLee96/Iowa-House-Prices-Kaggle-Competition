# Iowa Housing Price Prediction
Team members: Jaehyeong Lee, Avash Monjaemi, Sally Zhu, Iris Liu

# Overview
As a team of 4, we participated in Kaggle competition for predicting affordability of residential homes in Ames, Iowa. During the course, we utilized feature engineering methods such as Principal Component Analysis (PCA) amd dimension reduction on raw dataset that contained sheer number of 79 variables. After a rigorous data cleaning and data manipulation, we moved onto using various advanced regression techniques such as Random Forest (RF) and logistic regression. At the end, we have achieved accuracy of about 98% on test dataset and won _2nd place_ among participants of around 50 people!

# Competition Description

![alt text](https://storage.googleapis.com/kaggle-competitions/kaggle/5407/media/housesbanner.png)

Ask a home buyer to describe their dream house, and they probably won't begin with the height of the basement ceiling or the proximity to an east-west railroad. But this playground competition's dataset proves that much more influences price negotiations than the number of bedrooms or a white-picket fence.

With 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa, this competition challenges you to predict the final price of each home.

# Data Cleaning / Processing

Examining the dataset brieﬂy gives preliminary insight for how the training and testing data should be manipulated which are : (1) Certain characteristics of a home have multiple variables linked to them, (2) Data collection from select predictors resulted in a number of NA results that ought to be corrected for, and (3) Existence of both numeric and character variables and how they may conﬂict during future data modeling procedures unless they are restructured or simpliﬁed. 

# Methods

Models  | Accuracy
------------- | -------------
Random Forest  | 98%
Logistic Regression  | 96%
Support Vector Machine (SVM)  | 93%
Decision Trees  | 92%
Naive Bayes  | 90%
