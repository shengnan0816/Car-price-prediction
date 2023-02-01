
# Car price predition with regression model

In this project, I followed a project on Kaggle and applied regression modelling on a car price dataset. After evaluating the result, I adjuested the model and improved accuracy of the predition.




## data and project link

 - [Polynomial Regression| Regularization| Assumptions](https://www.kaggle.com/code/farzadnekouei/polynomial-regression-regularization-assumptions#Step-10:-Build-2nd-order-Polynomial-Regression)



## Methodology

1 import libs

2 import data

3 data processing

4 EDA  
      
    4.1 categorical columns    
    - selling price vs. fuel type - Diesel cars are more expensive.   
    - selling price vs. seller type - Dealers sell cars at higher price; Trustmark Dealer sell at even higher price, but gap is small.     
    - selling price vs. transmission - automatic cars sell at higher price.      
    - selling price vs. owner - test drive cars are more expensive (of course!)    
    - selling price vs. seats - 7 seats are most expensive, 2 seats (sports car) is the 2nd most expensive cars       

    4.2 numeric columns    
    - all numeric values have right skewness which will require normoralization

    4.3 Target vs. Numerical Features Bivariate Analysis  
    - how numeric features are correlated with target?
        - age - negative
        - km_driven - negative
        - engine - positive
        - max_power - positive    

    4.4 Target vs. Categorical Features Bivariate Analysis     
    - Diesel cars have highest number
    - sales from deealers are the most
    - there are more automatic cars than mannual cars
    - first owned cars are the most popular 
    - most cars have 5 seats     

    4.5 Multivariate Analysis
    - almost no Diesel cars sold by Trustmark Dealer
    - auto & dealer car tend to have lower km_driven while manual & deal have more km_driven

    4.6 Categorical Variables Encoding
    - max power and engine are highly correlated -> should drop one of them

5 Modeling   

    5.1 linear regression    

    5.2 model evaluation      
    - 59% r2-score
    - MAE, MSE, RMSE checked as well    

    5.3.1 Assumption 1 - Linearity
    - plot shows no linearity between dependent var and independent var.    

    5.3.2 Assumption 2 - Normality of Residuals.    
    - Residuals are not normally distributed.     

    5.3.3 Assumption 3 - Multicollinearity
    - 1 cases of definite multicollinearity.    
    - need to drop col seats_5     

    5.3.4 Assumption 4 - No Autocorrelation of Residuals
    - Durbin-Watson test shows result 2.004 which means: Little to no autocorrelation.    

    5.3.5 Assumption 5 - Homoscedasticity
    - We can not see a fully uniform variance across our residuals because the orange line is not flat. The assumption is not satisfied
(**Homoscedasticity is a statistical property where the variance of the errors in a regression     model is equal across all independent variable values. This means that the spread of the residuals   (the difference between the actual and predicted values) is constant, regardless of the value of the predictor variable. Homoscedasticity is often assumed in linear regression models, as it makes it easier to interpret the model and assess its validity.)

6 Solution from assumption

    6.1 To satisfy the multicollinearity assumption, we remove the col seats_5 feature.    

    6.2 Then, according to the pattern in the plot of the residuals vs. predicted values, we will use box-cox transformation on the entire dataset.    

    6.3 By applying polynomial regression, we will try to improve the satisfaction of homoscedasticity and normality of residuals.     

    6.4 Finally, we will use regularization to reduce the probability of the model to be overfit
    (I paused at here).    
    - Ridge regression.   
    - Lasso regression.    




    

