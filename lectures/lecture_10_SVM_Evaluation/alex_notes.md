# Lecture 10: Support Vector Machines, Hyperparameter Tuning and Model Evaluation

- **Support Vector Machine (SVMs)**
    - SVMs are an extremely powerful and versitle model capable of performing classification, regression, and outliar detection
        - It can also perform on both linear and non-linear tasks
    - **SVM functionality**
        - SVM classficiation works by trying to find the line of best fit with largest margin of seperation between two classes. This type of classfication is called **large margin classification**
        - The edge of the largest margins separating the two classes are called the **support vectors**. **Support vectors** define the classification edge of the classes and is represented as a vector of weights.
            - These support vectors line up closest the fringe data points in the training set. As such it is said that Support Vector Machines really only cares about the instances the two classes that are close to the 
        - **How do we train a SVM?**
            - The training objectives for a SVM is to minimize the absolute value of the support vectors. By doing this SVM maximizes the margin between the two classes in question for the line of best fit.
            - **Slack variables** are SVM hyperparameters that allow use to determine how much give/tolerance the SVM model has for outliers. The higher the **slack variable** the greater the outlier tolerance is.  
            - **Training Formula:**
            <img src='eq_54.png'>

        - **How does SVM actually perform classification**
            - SVM perform classification by computing the dot product of support vectors and how data plus bias.
                - if w^T * w + b < 0 then 0 is returned
                - if w^T * w + b >= 0 then 1 is returned
            - Some important information to understand the above equation:
                - 0 is were the hyperplane intersects the dataset SVM is working on.
                - 1 or -1 is when the value is at or past the support vector for a class.

- **Hyperparameter Tuning**
    - **What are Hyperparamters?**
        - Hyperparameters are parameters which define the model architecture. 
            - For example, the hyperparamters for an SVMs model is:
                - the kernel of choice
                - slack variables 
        
        - By changing these parameters you will change the fundamental behavior a model will have when training on data.
        - As such hyperparameters can not be estimated from your dataset they have be pre-specified before training.
        - The process of identifying the optimal hyperparameters for a given model is commonly referred to as **Hyperparameter Tuning**
    - **Methods of Hyperparameter Tuning**
        - **GridSearch**
            - Gridsearch is the simplest method of hyperparameter tuning.
            - **GridSearch Methodology:** 
                1. proved for all hyperparameters of interest list of possible hyperparameter value you wish to experiment. 
                2. Iterate through evey possible combination of the hyperparameters of interest build and evaluate a model.
                3. Then select the model that produces the best results and it's hyperparameter.
            - Because of how GridSearch searches a potiential hyperparameter space it is consider and exhaustive method and is rather computational inefficient.
        - **RandomSearch**
            - The theoritical underpinning of RandomSearch is that for most datasets only a few of the hyperparameters really matter, but that hyperparameters are important on different datasets.
            - **RandomSearch Method**
                1. Provide a statistical distributions for every hyperparameter of interest
                2. Define how my N iterations RandomSearch will perform
                3. For i in N iterations draw a sample for the statistical distributions provided.
                4. With i sample build a model and evaluate performance.
                5. Upon completing N iterations select the best performing model and hyperparameters.
            - RandomSearch improves the exploratory power and can focus on finding the optimal value for the important hyperparameter
        
        - **Bayesian Optimization**
            - In the previous 2 methods experiment where performed in isolation, we're not able to use the information from one experiment to improve the next experiment
            -  Bayesian optimization allows us to use the results of our previous iteration to improve our sampling method of the next experiment
            - **Bayesian Optimization Method**
                1. Define a model constructed with hyperparameters λ
                2. Train the model and evaulate according to some evaluation metric scored v
                3. Use the previously evaluated hyperparameter values to compute a posterior expectation of the hyperparameter space. 
                4. Choose the optimal hyperparameter values according to this posterior expectation as our next model candidate. We 
                5. iteratively repeat this process until converging to an optimum.

- **Model Evaluation Methods**
    - Evaluation metrics explain the performance of a model
    - Training predictive modeling works via the following feedback loop: 
        1. build a model
        2. recieve feedback from evaluation metrics
        3. make improvements
        4. continue until you achieve a desirable accuracy
    - An important thing to know is that the evaluation metic you choose to use will vary based upon the type of model your evaluating. For instance, Regression and Classification models require different evaluation methods.
    - These notes will primarily focus upon classfication methods of evaluation model performance.
    - **Confusion Matrix**
        - A Confustion Matrix is an N x N matrix where N is the number of classes being predicted by the model
        - From a Confustion Matrix you calculate the follow metrics:
            - **Accuracy** the proportion of the total number of predictions that were correct. (Both True Positive and True Negative)
            - **Precision** (Postive Prediction Value) the proportion of positive cases that were correctly identified.
            - **Negative Predictive Value** the proportion of negative cases that were correctly identified.
            - **Sensitivity or Recall** the proportion of actual positive cases which are correctly identified.
            - **Specificity** the proportion of actual negative cases which are correctly identified.
        - Typically, your concerned with only one of these metrics you can calculate.
    
    - **Receiver Operating Characteristic curve**
        - Receiver Operating Characteristic curve (ROC curve) is a plot of the true positive rate against the false positive rate
        - ROC Curve tells use the following about a model:
            1. It shows the tradeoff between sensitivity and specificity (any increase in sensitivity will be accompanied by a decrease in specificity).
            2. The closer the curve follows the left-hand border and then the top border of the ROC space, the more accurate the test.
            3. The closer the curve comes to the 45-degree diagonal of the ROC space, the less accurate the test.
    
    - **Precision-Recall curve**
        - Precision-Recall is a useful measure of success of prediction when the classes are very imbalanced. 
            - For example in information retrieval, precision is a measure of result relevancy, while recall is a measure of how many truly relevant results are returned.
        - For the Preceision Recall curve we want to see the curve move up towards upper left of graph.
        - The Precision-Recall curve shows the tradeoff between precision and recall for different threshold. 
            - A high area under the curve represents both high recall and high precision, where high precision relates to a low false positive rate, and high recall relates to a low false negative rate. 
            - High scores for both show that the classifier is returning accurate results (high precision), as well as returning a majority of all positive results 