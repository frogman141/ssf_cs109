# Lab4: Regression in Python

- In this lab you'll run through a brief introduction to how to conduct a regression analysis utilizing python. There are two crucial libraries you'll be using **scikit-learn** and **statsmodel** 

- **Linear Regression**
    - **Linear Regression** is a inferential statistical method to model the relationship between an X exploratory (independent) variable and Y dependent variable. 
        - linear regresssions basic assumption is that there is a linear relationship between the exploratory and dependent variables.
        ```
            Y = beta0 + (beta1 * X1) + epislon
        ```
        - Y = Dependent Variable
        - beta0 = Y-intercept
        - beta1 = coefficients
        - X = Exploratory Variable
    
    - **Multilinear Regression** is linear regression when you have more than one independent variables: X1, X2, X3

    - **Least Squares** is a method that estimates the the coefficient of the linear model by mininzming the difference between observations. 
        - least squares is estimate beta0 and beta1
    
    - **Key Features of Linear Regression**
        - **Linearity:** The assumption that the relationship between the Indepedent and Dependent Variables is linear.
        - **Constant Standard Deviation:** The SD of the dependent variable should constant for different values of Indepedent variable.
        - **Normal Distribution of Errors:** epsilon is assumed to be normaly distributed
        - **Independent Errors:** Observations are assumed by obtained independent of each other.
    
- **Preventing Overfitting:**