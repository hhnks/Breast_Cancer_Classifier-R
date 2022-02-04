# Breast_Cancer_Classifier-R

My postgraduate studies project:
A breast cancer classification in R Markdown

The dataset contains coded information on breast cancer patients. The aim of the project was to build 3 models that classifies whether the cancer is **malignant** or **benign** and select the best one according to the selected criterion.

I decided to create 3 models based on logistic regression, each using a different method:
- model 1: classic logistic regression without regularization
- model 2: stepwise regression
- model 3: logistic regression with Lasso regularization

The models were compared based on metrics:
- **Accuracy**, because it's intuitive, it's the ratio of correctly classified observation to the number of all classifications, good for balanced classes
- **F1**, which is the harmonic mean of recall and precision

The set consists of a `Diagnosis` target variable (M = malignant, B = benign) and 30 unknown variables.

##Metrics

![obraz](https://user-images.githubusercontent.com/84125127/152542121-5d35cddb-ee23-4ef1-9066-9a020fc077a9.png)

## What's interesting?

- **Variance inflation factor (VIF)**: There is high multicollinearity in the dataset and I've used VIF to measure the multicolinearity for each variable. For each variable, VIF was progressively calculated. If the coefficient for a variable exceeded a critical value, it was removed. This reduced the number of predictors by almost half already at the data cleaning stage.

- **outliers functions**: I created two functions for outliers - one for searching for outliers in dataset, which returns few informations about number of outliers in dataset and add column to dataset with number of outliers in each row. Second function was to deal with outliers by replacing them with e.g. median.

- **stepwise regression**: I used a stepwise regression model with backward elimination. It creates a logistic regression model with all variables and stepwise removes predictors by minimizing Akaike criterion (AIC). 


## Workflow of a project

Project is divided into parts:

1. Introduction <br />
2. EDA (outliers, NAs) <br />
3. Data Cleaning <br />
  3.1. Outliers <br />
  3.2. Multicollinearity <br />
4. Modeling <br />
  4.1. Model 1: classic logistic regression without regularization <br />
 &nbsp;&nbsp;   4.1.1. Reducing the number of predictors (p-value) <br />
 &nbsp;&nbsp;   4.1.2. Cross-validation <br />
  4.2. Model 2: stepwise regression <br />
 &nbsp;&nbsp;   4.2.1. Minimizing the Akaike's coefficient <br />
 &nbsp;&nbsp;   4.2.2. Cross-validation <br />
  4.3. Model 3: logistic regression with Lasso regularization <br />
   &nbsp;&nbsp;   4.3.1. Cross-validation for lambda <br />
   &nbsp;&nbsp;   4.3.2. Metrics <br />
Conclusions <br />

## R Markdown in R version 4.1.1 (2021-08-10)

R packages:
* `dplyr`
* `ggplot2`
* `gridExtra`
* `GLMNet`
