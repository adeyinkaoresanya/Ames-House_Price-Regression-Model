# Ames-House-Price-Regression-Model
The goal of this project was to predict the price of a home in Ames, Iowa, based on certain characteristics of the home. This was carried out using basic algorithms such as Linear Regression and random forest. This problem is a regression problem.

# About the data
The dataset, downloaded from [Kaggle](https://www.kaggle.com/c/house-prices-advanced-regression-techniques), contained information on 2919 houses in Ames. This was divided into train set [1460 rows, 81 columns] and test set [1459 rows, 80 columns], consisting of 36 numeric variables, 44 categorical variables and a numeric label.

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

* StandardScaler from Scikit-learn was used to standardize the features. 

