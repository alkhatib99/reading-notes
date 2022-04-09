# class_13 - Linear Regression

## Linear Regression in Python

### Regression

Regression analysis is one of the most important fields in statistics and machine learning. 
<br>
find a function that maps some features or variables to others sufficiently well.
The dependent features are called the dependent variables, outputs, or responses.
<br>
The independent features are called the independent variables, inputs, or predictors.

### When Do You Need Regression?

you need regression to answer whether and how some phenomenon influences the other or how several variables are related. 
<br>
Regression is also useful when you want to forecast a response using a new set of predictors. 

#### Linear Regression

Linear regression is probably one of the most important and widely used regression techniques.

#### Problem Formulation

<img src='https://image.slidesharecdn.com/linearlogisticregressiononspark-170119124155/95/implementation-of-linear-regression-and-logistic-regression-on-spark-4-638.jpg?cb=1598789500'/>
#### Regression Performance
The coefficient of determination, denoted as 𝑅², tells you which amount of variation in 𝑦 can be explained by the dependence on 𝐱 using the particular regression model. 
<br>
The value 𝑅² = 1 corresponds to SSR = 0, that is to the perfect fit since the values of predicted and actual responses fit completely to each other.
#### Underfitting and Overfitting
* Underfitting occurs when a model can’t accurately capture the dependencies among data, usually as a consequence of its own simplicity. 
<br>
* Overfitting happens when a model learns both dependencies among data and random fluctuations
<br>
<img src='https://www.researchgate.net/publication/339680577/figure/fig2/AS:865364518924290@1583330387982/llustration-of-the-underfitting-overfitting-issue-on-a-simple-regression-case-Data.png'/> 

#### How to Run Linear Regression in Python

Scikit-learn is a powerful Python module for machine learning. It contains function for regression, classification, clustering, model selection and dimensionality reduction. Today, I will explore the sklearn.linear_model module which contains “methods intended for regression in which the target value is expected to be a linear combination of the input variables”.

```Python
import numpy as np
import pandas as pd
import scipy.stats as stats
import matplotlib.pyplot as plt
import sklearn
```

Linear regression is a basic and commonly used type of predictive analysis. The overall idea of regression is to examine two things: (1) does a set of predictor variables do a good job in predicting an outcome (dependent) variable? (2) Which variables in particular are significant predictors of the outcome variable, and in what way do they–indicated by the magnitude and sign of the beta estimates–impact the outcome variable? These regression estimates are used to explain the relationship between one dependent variable and one or more independent variables.

[Back to Homepage](../README.md)
