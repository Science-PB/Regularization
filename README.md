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

<img width="704" alt="Screen Shot 2020-11-16 at 8 42 58 PM" src="https://user-images.githubusercontent.com/66921930/99329619-9d807880-284c-11eb-9307-6659ff27b73e.png">

While steps have been taken to set up the data, another critical component when
implementing regularization is to determine which values are utilized for training and which are
utilized for testing. The intent behind splitting up the data is that the model is built on the training data
and then is evaluated by its performance on the test data (Singh, 2019). For this use case a random
seed for reproducibility of results is implemented in R, assigning half the data as training and half as
testing. The R code utilized to split and assign the data is seen in Figure 2.

<img width="686" alt="Screen Shot 2020-11-16 at 8 43 29 PM" src="https://user-images.githubusercontent.com/66921930/99329622-9eb1a580-284c-11eb-9b4a-70055ff532fa.png">

# Cross Validation

Once data is structured and properly set-up to support running a regularization model the most
optimal lambda needs to be determined. The method for determining the optimal lambda is referred
to as cross validation. Cross validation is conceptually the evaluation of the prediction error through
examination of the data under control, and thus the minimum error when changing lambda is
considered to obtain the optimal lambda value (Obuchi & Kabashima, 2016). Cross validation is
performed using the cv.glmnet function in R. Figure 3 showcases the R code and result of the optimal
lambda coefficient, 0.03.

<img width="749" alt="Screen Shot 2020-11-16 at 8 44 01 PM" src="https://user-images.githubusercontent.com/66921930/99329624-9eb1a580-284c-11eb-9c8c-ec93ed942f0c.png">

A further look into obtaining the optimal lambda can be made by plotting the cross-validated
mean squared error as seen in Figure 4. Looking at the plot, the two vertical dotted lines represent the minimum lambda that results in the lowest mean square error (MSE) as well as the lambda value within one standard error of the minimum (Columbia University, 2020). The choice of the lambda
value is dependent on the context and objective of the study, but it is important to determine how
much “fit” is wanted. At the top of the plot the numbers represent the quantity of nonzero coefficients
or variables that the model chooses to use.

<img width="750" alt="Screen Shot 2020-11-16 at 8 44 32 PM" src="https://user-images.githubusercontent.com/66921930/99329626-9f4a3c00-284c-11eb-97ac-02f1419a93cb.png">

# Lasso Regularization

After the optimal lambda has been identified, lasso regularization can be run to determine the
expected best model. This data lends itself to making predictions on fertility values. Two R functions
are utilized to output results, glmnet and predict. The output of the predictions can then be compared
to the actuals. Figure 5 showcases the R coding utilized as well as a representation of six of the
predicted values to their actuals, giving an idea of how the model performed.



One of the objectives of Lasso regression is the avoidance of overfitting the model. In order to
understand this, it is important to know the R-squared value achieved. Figure 6 provides the R code
and output of the R-squared value for the model. R-squared determines how close the data is to the
fitted regression line (The Minitab Blog, 2013). In general, the higher the R-squared the better the fit,
although that is not always the case. At 0.53 the R-squared for this model falls in the middle.


A last consideration for Lasso regression is the important variables in predicting “Fertility”.
Since Lasso regression can actually remove variables from the model it is beneficial to understand
which variables are influencers. Based on the R code run in Figure 7, the determination can be made
that “Catholic” and “Infant Mortality” were the variables utilized to make predictions on “Fertility”.


# Conclusion

The use of predictions for future variables in order to ascertain data patterns, is a regularly
practiced concept in machine learning. The use of regularization to the field of predictive analytics is
primarily associated with the intent of minimizing errors and reducing overfitting. It is, however, only a
component of improving accuracy in predictive analytics. The concept overall is that by building a
penalty into the algorithm the amount of bias is increased in order to improve variance, which is the
cause of an overfit model. There are multiple regularization models available for use, many with
similar characteristics, however the Lasso model stands out for its capability to remove variables
seen as nonvalue adds to the model.
As is the case with many aspects of statistics there are potential problems with using certain
techniques and Lasso regression is no exception. In fact, one of the main problems noted with Lasso
regression is that the removal of correlated variables can possibly lead to information loss resulting in
lower accuracy (Jain, 2017). The same can be said about making assumptions about the data
outputs based on generalizations. For example, a higher R-squared value in general means the
model is better fitted to the data, however R-squared does not indicate whether a regression model is
adequate and therefore having a low R-squared does not necessarily mean the model does not fit the
data (The Minitab Blog, 2013).
The important factor to take away about regularization techniques is that it is a tool designed to
improve accuracy in regression models but also one that can be easily misused, much like many
statistics processes. Lasso regression and its counterparts in regularization seeks to reduce the
noise, or data points that fail to represent the true properties in a data set (Gupta, 2017). With careful
consideration of applicability and use, as well as proper set-up and computations, regularization
methods such as the Lasso technique can be a tremendous aid in improving machine learning
models from the standard linear or multiple regression method.

# References

R Statistics Blog. (2020, May 17). Quick Tutorial On LASSO Regression With Example. R Statistics

Blog. Retrieved from: https://rstatisticsblog.com/data-science-in-action/machine-learning/lasso-
regression/#:~:text=LASSO%20regression%20stands%20for%20Least,large%20number%20of%20p

redictor%20variables.
SAS. (n.d.) Predictive Analytics: What it is and why it matters. SAS Institute Inc. Retrieved from:

https://www.sas.com/en_us/insights/analytics/predictive-
analytics.html#:~:text=Predictive%20analytics%20is%20the%20use,will%20happen%20in%20the%2

0future.
Edureka. (2020, Apr 24). How To Use Regularization in Machine Learning? Edureka. Retrieved from:
https://www.edureka.co/blog/regularization-in-machine-learning/

Machine Learning with R. (n.d.) Ridge and Lasso Regression Models. Machine Learning with R.
Retrieved from: http://wavedatalab.github.io/machinelearningwithr/post4.html

Obuchi, T and Kabashima, Y. (2016, May 31). Cross validation in LASSO and its acceleration. IOP
Science. Retrieved from: https://iopscience.iop.org/article/10.1088/1742-5468/2016/05/053304
Singh, D. (2019, Nov 12). Linear, Lasso, and Ridge Regression with R. Pluralsight. Retrieved from:
https://www.pluralsight.com/guides/linear-lasso-and-ridge-regression-with-r

The Minitab Blog (2013, May 30). Regression Analysis: How Do I Interpret R-squared and Assess the
Goodness-of-Fit? The Minitab Blog. Retrieved from: https://blog.minitab.com/blog/adventures-in-
statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit

Columbia University. (2020, May 22). Least Absolute Shrinkage and Selection Operator (LASSO).

Columbia University. Retrieved from: https://www.publichealth.columbia.edu/research/population-
health-methods/least-absolute-shrinkage-and-selection-operator-lasso

Jain, S. (2017, June 22). A comprehensive beginners guide for Linear, Ridge and Lasso Regression
in Python and R. Analytics Vidhya. Retrieved from: https://www.analyticsvidhya.com/blog/2017/06/a-11

comprehensive-guide-for-linear-ridge-and-lasso-
regression/#:~:text=The%20main%20problem%20with%20lasso,lower%20accuracy%20in%20our%2

0model.
Gupta, P. (2017, Nov 15). Regularization in Machine Learning. Medium. Retrieved from:

https://towardsdatascience.com/regularization-in-machine-learning-
76441ddcf99a#:~:text=Regularization,linear%20regression%20looks%20like%20this.
