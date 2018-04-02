# Credit Card Clients

## Domain
This dataset describes and default payments of credit card clients in Taiwan from April to September 2005. It was sourced from the Department of Information Management, Chung Hua University, Taiwan and the Department of Civil Engineering, Tamkang University, Taiwan.

Past usage of the dataset include various proposals suggesting a classification problem such as the following:

https://www.linkedin.com/pulse/default-payment-prediction-system-duy-hoang-ly


## Problem Statement

The dataset compares the predictive accuracy of probability of default based on 23 feature describing demographics such as gender, marita status and educational backgound as well as financial features such as payment lateness for the past 6 months, payment amount and line of credit. For any give set of features we will use a classificatio model to predict if a credit card client will default or not.

## Dataset and Inputs
The data set contains 30k observations and 23 explanatory variables (56 categorical, 23 numeric) that are involved in assessing the category for default as 0 for not defaulting and 1 for defaulting.

The data set uses up 5.28 MB in memory.

## Evaluation Metrics
The dataset is not evenly distributed as most credit card client do not default. We can use the success of the model measuring against the F1 score and determine if our model predicts the correct default class  more reliably than the F1 score.

![](http://54.203.46.100/lab/tree/Credit-Card-Clients%2Fdata%2Fhistogram.png)


## Data Exploration

As seen above the distribution of defaulting is about 80% to 20%. In the below plot we can see the demograpphic distribution of the dataset:

![](http://54.203.46.100/lab/tree/Credit-Card-Clients%2Fdata%2FFeatures.png)

Gender (1 = male; 2 = female) 
Education (1 = graduate school; 2 = university; 3 = high school; 4 = others) 
Marital status (1 = married; 2 = single; 3 = others)

The dataset has a few more female clients than male with the majority of clients betwen the age of 25-40 and an almots evenly split between married and single.

Here is the summary of  all features:

![](http://54.203.46.100/lab/tree/Credit-Card-Clients%2Fdata%2FSummary.png)


Gender (1 = male; 2 = female) 
Education (1 = graduate school; 2 = university; 3 = high school; 4 = others) 
Marital status (1 = married; 2 = single; 3 = others)
 
We have to turn the various numerical features representing categories such as gender, education, martial status, age and history of past payment into factors and later one need to be one hot encoded. Also, a few values in the demographic features are zero, which is not defined in the legend. We can remove these outliers as they only make up 68 instances out ot the 30k we have available.

## Exploratory Visualization

When looking at the various demographic feature we can see that the distribution of defaulting to not defaulting is fairly similar tothe daatset as a whole (about 80/20)

![](http://54.203.46.100/lab/tree/Credit-Card-Clients%2Fdata%2FDistribution1.png)

This is suggesting that payment history, payment delay and pf given credit are better predictors for defaulting. This can be confirmed byt below correlations to the target:

![](http://54.203.46.100/lab/tree/Credit-Card-Clients%2Fdata%2FCorrelation.png)


## Solution Statement
A solution to this problem will be a classification model such as a logistic regression, decision tree, random forest, gradient-boosted tree, multilayer perceptron, one-vs-rest.

We are going to fit the dataset on a decision tree which is a decision support tool that uses a tree-like graph or model of decisions and their possible consequences. It is one way to display an algorithm that only contains conditional control statements. With that we are identifying the F1 score as ameasure precision and recall and then use hyperparameter tuning, boosting and/or a different model to improve the score. 


## Algorithms and Techniques

The decsion tree is fit with the standard algorithms. The quality of a split is measured by the Gini impurity with the best splitter and no maximal depth. The minimum number of samples required to split 2 and the minimum number of samples required to be at a leaf node is 1. The samples have equal weight and we do not limit the amount of features when looking at the best split. Since the decision tree requires minimal data trandforamtion and feature enginering it si a good model to start with.


## Benchmark Model
When fitting a desicion tree with above descibed default algorithm we are getting a 0.99 score for the train set which is to be expected as we didn't specify maximum depth and decision trees can easily overfit on a data set. We are laso getting a score of 0.72 on the test set and and F! score of 0.40 for the test and sets actual target values and the predicted values by the model. This has room for imporvement and next we would apply a boosting method such as gradient boosting, try to set a maximum depth for the decision tree model fitting and identify other hyperparameters that can improve the model.


## Project Design

In order to identify the best model for this project we should fit on various models such as logisitc regerssion, decision tree, random forest, gradient-boosted tree, multilayer perceptron, etc instead of juts fitting the decision tree. Once we have scores for the various models we can select the most pormising to further imporve upon with hyperparameter tuning and/or boosting.

