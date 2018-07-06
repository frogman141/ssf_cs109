# Lecture 7: Bias and Regression

- **What is Bias?**
    - Statistical bias refers to measurement or sampling errors that are systematic and produced by the measurement or sampling process. 
    - An important distinction should be made between errors due to random chance, and errors due to bias. Consider the physical process of a gun shooting at a target. It will not hit the absolute center of the target every time, or even much at all. An unbiased process will produce error, but it is random and does not tend strongly in any direction
    - Bias comes in different forms, and may be observable or invisible.
    - **Data Snooping** Extensive hunting through data in search of something interesting
    - **Vast search effect** Bias or nonreproducibility resulting from repeated data modeling, or modeling data with large numbers of predictor variables.

- **Various forms of Bias:**
    - **Selection Bias**
        - self-selection bias can occur when they involve individauls takings action. For example, say your studying restraunt reviews on yelp. This leads to self-selection bias—the people motivated to write reviews may be those who had poor experiences, may have an association with the establishment, or may simply be a different type of person from those who do not write reviews
        - Selection bias refers to the practice of selectively choosing data—consciously or unconsciously—in a way that that leads to a conclusion that is misleading or ephemeral.
    
    - **Publication Bias** 
        - A type of bias that occurs in published academic research. It occurs when the outcome of an experiment or research study influences the decision whether to publish or otherwise distribute it. 
        - Publication bias matters because literature reviews regarding support for a hypothesis can be biased if the original literature is contaminated by publication bias. Publishing only results that show a significant finding disturbs the balance of findings.
    - **Non-response bias**
        - non-response bias occurs frequently in survery's. If you send a survey to 10 people and only 8 people respond. You have a non-response bias in your data because 2 of the survey recipients haven't returned.
    - **Length Bias**
        - this bias occurs when your trying to measure any event that can occur for varying lengths in time. For example, prison sentences. If you survery prisoners for the average jail sentence your data will be skewed towards prisoners with longer sentences. This is because prison sentances vary.
    
- **Bias-Variance Tradeoff**
    - An important theoretical result of statistics and Machine Learning is the fact that a model’s generalization error can be expressed as the sum of three very different errors:

        - **Bias:** this part of the generalization error is due to wrong assumptions, such as assuming that the data is linear when it is actually quadratic. A high-bias model is most likely to underfit the training data.
        - **Variance:** This part is due to the model’s excessive sensitivity to small variations in the training data. A model with many degrees of freedom (such as a high-degree polynomial model) is likely to have high variance, and thus to overfit the training data.
        - **Irreducible error:** This part is due to the noisiness of the data itself. The only way to reduce this part of the error is to clean up the data (e.g., fix the data sources, such as broken sensors, or detect and remove outliers).

    - Increasing a model’s complexity will typically increase its variance and reduce its bias. Conversely, reducing a model’s complexity increases its bias and reduces its variance. This is why it is called a tradeoff.

- Multiple Hypothesis Testing, **the Bonferroni Correction**:
    - Statistical hypothesis testing is based on rejecting the null hypothesis if the likelihood of the observed data under the null hypotheses is low. 
    - If multiple hypotheses are tested, the chance of a rare event increases, and therefore, the likelihood of incorrectly rejecting a null hypothesis (i.e., making a Type I error) increases.
    - The Bonferroni correction compensates for that increase by testing each individual hypothesis at a significance level of \alpha / m where \alpha  is the desired overall alpha level and m is the number of hypotheses.

- **Regression Towards The Mean (RTTM):**
    - Regression to the mean refers to a phenomenon involving successive measurements on a given variable: extreme observations tend to be followed by more central ones.
    - Attaching special focus and meaning to the extreme value can lead to a form of selection bias. This is most commonly observed by sports fans this is were the saying “rookie of the year, sophomore slump” comes from its a RTTM phenomena. 
    - The phenomenon was first identified by Francis Galton in 1886.

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