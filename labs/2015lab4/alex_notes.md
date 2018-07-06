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
        - least squares is used to estimate beta0 and beta1
    
    - **Key Features of Linear Regression**
        - **Linearity:** The assumption that the relationship between the Indepedent and Dependent Variables is linear.
        - **Constant Standard Deviation:** The SD of the dependent variable should constant for different values of Indepedent variable.
        - **Normal Distribution of Errors:** epsilon is assumed to be normaly distributed
        - **Independent Errors:** Observations are assumed by obtained independent of each other.
    
- **Preventing Overfitting:**
    - A major issue when training machine learning model is one of overfitting. Overfitting is when your model is extremely accurate at predicting values within your training dataset but generalizes poorly to non-training data. 
    - The way you counter overfitting is through breaking your data into a training and validation datasets. Where you train your model one and then once you have sufficiently high accuracy you test it against your validation dataset. 
    
- **K-Fold Cross-Validation**
    - Cross-validation extends the idea of a holdout sample to multiple sequential holdout samples. The algorithm for basic k-fold cross-validation is as follows:
        1. Set aside 1/k of the data as a holdout sample.
        2. Train the model on the remaining data.
        3. Apply (score) the model to the 1/k holdout, and record needed model assessment metrics.
        4. Restore the first 1/k of the data, and set aside the next 1/k (excluding any records that got picked the first time).
        5. Repeat steps 2 and 3.
        6. Repeat until each record has been used in the holdout portion.
        7. Average or otherwise combine the model assessment metrics.

    - The division of the data into the training sample and the holdout sample is also called a fold.

- **Different Types of Regression**
    - **Ridge Regression** is a regularized version of Linear Regression: a regularization term equal to alpha sigma-summation Underscript i equals 1 Overscript n Endscripts theta Subscript i Superscript 2 is added to the cost function. This forces the learning algorithm to not only fit the data but also keep the model weights as small as possible. 
    - **LASSO Regression** Least Absolute Shrinkage and Selection Operator Regression (simply called Lasso Regression) is another regularized version of Linear Regression: just like Ridge Regression, it adds a regularization term to the cost function, but it uses the ℓ1 norm of the weight vector instead of half the square of the ℓ2 norm.