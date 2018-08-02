# Lecture 13: Best Practices

- **Out of Bag Errors**
    - Out of Bag (OOB) Errors is a method of measuring prediction error of ensemble models that utilzie boostrap aggregating 
        - Typically, these models are decision tree based
    - OOB errors works by takign the remaining out of bag observations for a given predictor and predict the response for these observations.
    - From a training instances labels and predicted labels responses we can compute the error of the bagged model.
    - OOB errors is essentially equivalent leave one out cross validation error

- **Variable Importance**
    - Variable importance is the increase in a models prediction error upon permutation
    - more formally a features important if it's permutating increases model error 
    - features are unimportant if it's permutating does not increase model error
    - Features are unimportant if permutating it results in no change in a models error
    
    - **Advantages**
        - Easy interputation: Feature importance is the increase in model error as features information is destoryed.
        - Feature Importance provideds a highly compressed, global insight into the model's behavior
        - Feature importance is comparable across different problems
    - **Disadvantages**
        - you need access to the actual outcome of the targets
        - feature importance is tied to the error of model

- **Similarity Measures**
    - **Pearson Correlation Coefficient (PPC)**
        - PCC is a measure of the linear correlation between two variables
        - PCC values are between +1 and -1. 
            - +1 is a totally positive correlation.
            - -1 is a totally negative correlation.
            - 0 is where there are no correlations between the two variables.
    - **Cosine Similarity**