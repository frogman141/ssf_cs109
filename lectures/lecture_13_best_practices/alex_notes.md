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
        - cosine similarity metrics finds the normalized dot product of the 2 attributes. cosine similarity works by finding the cosine angle between two objects.
        - Therefore, cosine similarity is judging the orientation not magnitude 
            - 2 vectors with the same orientation will have a cosine similarity of 1
            - 2 vectors at 90 degrees of each other will have a cosine similarity of 0
            - vectors going in a oppisite direction is -1

- **Missing Data Strategies**
    - In most real world situations you will have an imbalance between classes you are trying to classify. There are 3 primary methods handling this situation
    - **Metric Selection**
        - Typically, this problem can be solved by emphasing metrics such as recall or precisions over accuracy
    - **Cost-Sensitive Learning**
        - Typically, misclassification are treated equally. But when you have imbalance in your data you may want to assign a greater penalty to misclassification of minority classes.
        - This can be done via cost-sensitivity learning. Typically, cost-sensitivity learning has the cost equal the inverse of the proportin of the dataset that the classes make up
        - Thereby, increasing the penalty as the class size decreases
    - **Sampling**
        - Another way of solving imbalance dataset is to oversample minority classes, or undersample majority classes
            - A warning though these simple sampling methods are flawed and won't work 100% of the time.
        - a more robust sampling methods such as SMOTE, which actually creates now instances of a minority class by creating convex combinations of neighboring instances.
            - this method will cause some overfitting but not mcu has we create synthetic examples rather than using duplicates