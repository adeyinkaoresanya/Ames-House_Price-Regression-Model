# Ames-House-Price-Regression-Model

The goal of this project was to predict the price of a home in Ames, Iowa, based on certain characteristics of the building. This was carried out using basic algorithms such as Linear Regression and Random Forest. This problem is a regression problem.

# About the data
The dataset, downloaded from [Kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques), contained information on 2919 houses in Ames. This was divided into train set [1460 rows, 81 columns] and test set [1459 rows, 80 columns], consisting of 36 numeric variables, 44 categorical variables and a numeric label (present in the train set).

## Exploratory Analysis
* The data had a lot of categorical variables and contained considerable amount of missing values in 19 variables.




* The distribution of the target variable, 'SalePrice' showed peakedness and positive skewness but no zero values, implying the variable is not normally distributed, as is common with price variables. As this could pose a problem when training linear algorithms, log transformation was carried out to normalise it.

*	On observing the numeric features, some were highly correlated with one another, for instance:

1. 'GarageCars' vs 'GarageArea'
2. 'TotalBsmtSF' vs '1stFlrSF'
3.  'TotRmsAbvGrd' vs 'GrLivArea' 
4.  'YearBuilt' vs 'GarageYrBlt'

In order to prevent multicollinearity, one of the features, lesser correlated with the target variable was dropped. 

* Manual inspection of the categorical variables shows that some were ordinal features which had a meaningful ranking. These were transformed into discrete variables.
* Neighborhood has big impact on house prices and having a pool in the building increases the price substantially.


## Data Cleaning
*	Missing values in numeric variables were imputed with their median because most were not normally distributed while nominal variables were imputed with the mode. As for the ordinal variables, NaN indicated absence of the characteristics, hence they were filled with zeros.

## Feature Engineering

* New features were created from some of the numeric variables.
* Polynomials of the top 15 features highly correlated with the target variable was generated.
* Categorical variables were transformed through dummy coding.
* 83 skewed numerical features were normalised using log transformation.
* Afterwards, StandardScaler from Scikit-learn was used to standardize the features.

## Model Building and Evaluation

*	Two models were built using Linear Regression and Random Forest algorithms. These gave a RMSE score of 1.248 and 0.138 respectively on the validation set. To achieve a RMSE threshold of less than 0.14 according to the project requirement, features driving the model performance were selected using the Random Forest's feature_importances_ method. Reducing the dimension of the dataset using feature importances improved the linear regression model performance by 99.1%, decreased the training time by 57.1% and the inference time by 12.5%.

For model built with random forest, performance improved by 1.4% while training and inference time decreased by 25.2% and 1.6% respectively.

![alt text](https://github.com/adeyinkaoresanya/Zindi_DSN_2020_ExpressoChurnPrediction/blob/master/Feature%20importances.png "Feature importances")

## Conclusion
This shows that high dimensionality makes linear models give a poor performance  unlike tree models. Overall, quality is better than quantity when building machine learning models

## Recommendations
* A customer micro-segmentation should be conducted in order to offer personalised incentives that the likely churner would find difficult to refuse.
* Set up a customer engagement strategy for preventing customer inactivity.


