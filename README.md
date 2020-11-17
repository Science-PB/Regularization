# Regularization
Training Vs. Test Data, Cross Validation, Lasso Regularization, 

# Introduction

Predictive data analytics is the application of data, algorithms, and machine learning
techniques to determine future outcomes based on historical data (SAS, n.d.). Regularization
methods are an important component to predictive analytics in that they work to describe and identify
significant relationships between variables to make suitable predictions. While there are various types
of methods used to conduct regularization, the Lasso method is one frequently referred to. This paper
will go into depth using R code to apply the Lasso technique to the real-world data set “swiss”, which
provides standardized fertility measures and socio-economic indicators from Switzerland in 1888.

# Regularization

Regularization in terms of machine learning is a method that regularizes or shrinks coefficients
towards zero by assigning penalties to the coefficients (Edureka, 2020). One of the most popular
regularization methods is Lasso Regression. Lasso stands for least absolute shrinkage and selection
operator. The technique that Lasso regularization uses is considered an L1 regularization, specifically
it modifies the residual sum of squares (RSS) by adding a shrinkage quantity or penalty equivalent to
the sum of the absolute value of coefficients (Edureka, 2020). What the use of Lasso regression
seeks to accomplish is reducing over-fitting, thereby attaining a more reliable prediction for future
observations.
One of the most important components of the Lasso regression model is the identification of
the optimal lambda value. The lambda value is multiplied by the sum of the absolute value of the
coefficients and makes up the shrinkage penalty (Machine Learning with R, n.d.). The Lasso
technique uses lambda not only for shrinkage but determining which variables can be removed as
those variables that achieve a result of zero are eliminated from the model.
To demonstrate the applicability of utilizing the Lasso regression technique on a dataset, data
showcasing the standardized fertility measures and socio-economic indicators from Switzerland in
1888 will be analyzed to predict fertility. The intent being to understand the important socio-economic
variables in predicting fertility, as well as an understanding of the variance between the actual values
to the outputted predicted values. Application of the Lasso regularization method will be done through
the use of R.

# Training Vs. Test Data
In order to run a successful Lasso model, the first step is assigning the independent and
dependent variables. For the purposes of the “swiss” dataset and the intention to predict fertility, the
variable “Fertility” is assigned as the dependent (y-axis) variable with the rest of the variables being assigned as independent (x-axis). By assigning variables the effects of the independents can be
reviewed against that of the dependent.
Already highlighted as a main component of Lasso regularization, the lambda is a critical initial
step in the set-up process. R is used to create all lambda values from 0.001 through 100 for the
model to try out, this along with the variable assignment can be seen in the R code featured in Figure
1. The generation of lambda values is an important step as lambda is the tuning parameter used to
add a penalty to each variable. As the value of lambda increases, shrinkage occurs enabling
variables that result in zero to be “thrown away” (Machine Learning with R, n.d.).



While steps have been taken to set up the data, another critical component when
implementing regularization is to determine which values are utilized for training and which are
utilized for testing. The intent behind splitting up the data is that the model is built on the training data
and then is evaluated by its performance on the test data (Singh, 2019). For this use case a random
seed for reproducibility of results is implemented in R, assigning half the data as training and half as
testing. The R code utilized to split and assign the data is seen in Figure 2.



# Cross Validation

Once data is structured and properly set-up to support running a regularization model the most
optimal lambda needs to be determined. The method for determining the optimal lambda is referred
to as cross validation. Cross validation is conceptually the evaluation of the prediction error through
examination of the data under control, and thus the minimum error when changing lambda is
considered to obtain the optimal lambda value (Obuchi & Kabashima, 2016). Cross validation is
performed using the cv.glmnet function in R. Figure 3 showcases the R code and result of the optimal
lambda coefficient, 0.03.


A further look into obtaining the optimal lambda can be made by plotting the cross-validated
mean squared error as seen in Figure 4. Looking at the plot, the two vertical dotted lines represent the minimum lambda that results in the lowest mean square error (MSE) as well as the lambda value within one standard error of the minimum (Columbia University, 2020). The choice of the lambda
value is dependent on the context and objective of the study, but it is important to determine how
much “fit” is wanted. At the top of the plot the numbers represent the quantity of nonzero coefficients
or variables that the model chooses to use.

