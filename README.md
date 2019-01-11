# Iowa Housing Price Prediction
Team members: Jaehyeong Lee, Avash Monjaemi, Sally Zhu, Iris Liu

# Introduction
As a team of 4, we participated in Kaggle competition for predicting affordability of residential homes in Ames, Iowa. During the course, we utilized feature engineering methods such as Principal Component Analysis (PCA) amd dimension reduction on raw dataset that contained sheer number of 79 variables. 

After a rigorous data cleaning and data manipulation, we moved onto using various advanced regression techniques such as Random Forest (RF) and logistic regression. At the end, we have achieved accuracy of about 98% on test dataset and won _2nd place_ among participants of around 50 people!

# 1. Competition Description

![alt text](https://storage.googleapis.com/kaggle-competitions/kaggle/5407/media/housesbanner.png)

Ask a home buyer to describe their dream house, and they probably won't begin with the height of the basement ceiling or the proximity to an east-west railroad. But this playground competition's dataset proves that much more influences price negotiations than the number of bedrooms or a white-picket fence.

With 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa, this competition challenges you to predict the final price of each home.

# 2. Data Cleaning / Processing

Examining the dataset brieﬂy gives preliminary insight for how the training and testing data should be manipulated which are:

* Certain characteristics of a home have multiple variables linked to them. 
* Data collection from select predictors resulted in a number of NA results that ought to be corrected for.
* Existence of both numeric and character variables and how they may conﬂict during future data modeling procedures unless they are restructured or simpliﬁed. 

## Methods ##

__Deletion of a Predictor Entirely__

__1. Evidence claimed the predictor is not linked with aﬀordibilitty__ 
* _Example_ : Removal of the LotArea predictor due to evidence claiming that you cannot neccacarily determine the price of a home based on lot area. 

__2. Existence of other predictors already explain the predictor__ 
* _Example_ : BsmtFinType1 and BsmtFinType2 describe the rating of the basement ﬁnished area. After we take into account the existence of the predictor BsmtCond which evaluates the general condition of the basement, these variables now become obsolete by themselves as the general condition of the basement explains it enough. 

__3. Predictor result is embedded in creation of new predictors__ 
* _Example_ : FullBath and HalfBath variables are accounted for (totaled) in a new predictor which is total # of baths.

__4. Single level dominates the predictor (or too many NA’s)__
* _Example_ : The majority of homes in the data do contain central air conditioning (CentralAir : Yes or No), so analysis would be limited with the inclusion of this predictor due to the homogeneity. This is deleted completely. 

__5. Feature Creation__
* _Example_ : We develop new variables from existing variables to extract hidden relationships of the data. As said earlier, we want to predict the aﬀordabilitty of a home based upon number of baths and half baths. These individual variables may not have as strong of a connection with the response as the total number of baths so we uncover this to improve our future model accuracies.

__Conversion of Numeric Variables to Factors(w/levels)__

* _Example_ : The Porch area in square feet (ScreenPorch) variable was highly skewed to the right (Figure 1), taking on many values of 0 and an extremely small number of positive square feet values. In light of this it is rather important to view this data as simply having a porch or not and convert to it a factor with corresponding levels. • Note that we could also have transformed the Porch area variable (or other variables) by taking a log of this variable, correcting for some of the skewness. The variable of Ground Living Area is another example of a variable in which we may also take a logarithm of because of its skewness as shown below.
Simpliﬁcation of Factor Levels

* _Example_ : LotShape is simpliﬁed into a factor with only 2 levels. The motivation for this change is that there is no need to be too speciﬁc with the irregularity of a property shape and it is best classiﬁed as irregular or not.

## Recoding of NAs ##

__1. Variable descriptions indicate NA is an absence of a feature__ 
* _Example_ : Basement conditions with an NA indicates having no basement, and they are appropriately ﬁlled. 

__2. NAs are ﬁlled by measures of central tendency / most commonly occuring class__ 
* _Example_ : One observation for the training data’s MSZoning (zoning classiﬁcation of the sale) is an NA and therefore assigned to the most commonly occuring class of RL : Residental Low Densit

# Data Modeling

### Logistic Regression ###

We want to use Logistic Regression as our ﬁrst method for classiﬁcation and use it as a baseline that we will then compare with more complex and fancy algorithms. Furthermore, we want to utilize at least one method that will classify observations according to the probability that they correspond to a certain class. 

This means that if : ![alt text](https://latex.codecogs.com/gif.latex?Pr%28Affordable%7CX%29%20%3E%200.5) then we classify that home as being aﬀordable!


then we classify that home as being aﬀordable!

Models  | Accuracy
------------- | -------------
Random Forest  | 98%
Logistic Regression  | 96%
Support Vector Machine (SVM)  | 93%
Decision Trees  | 92%
Naive Bayes  | 90%
