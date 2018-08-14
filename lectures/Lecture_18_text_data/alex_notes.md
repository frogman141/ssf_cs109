# Lecture 18: Bayesian Methods and How to handle text data.

- **Heirarchy Bayesian Models**
    - **Pooling**
        - The Pooling method of modeling are that do not assume any potiential grouping/subgrouping within the data. Therefore models built with this method of modeling will lack specificity when modeling these groups.
        - An example of this is building a regression model to predict the house prices in california. The model may do alright over all but predicitons made for houses in a extremely wealthy and poor counties of California will most likely be inaccurate.
    - **No-Pooling**
        - No Pooling methods of modeling is when you assume there are nature grouping within your data and therefore build an individual model for each of these groupings in the data.
        - An example of this buidling a regression model for predicting house prices for every individual county of california.
    - **Mix-Pooling (Heirarchical models)**
        - In many datasets you can have natural groupings/subgroupings within the data. For instance, continuing our example of predicting house prices in california we have natural subgrouping based on county/geolocation.
        - Heirarchial Bayesian Models assume the models parameters are different for each grouping in the data. But that all of the parameters come from a common distribution unique to the group.
        - Therefore, heirarchial bayesian models assumes a model parameters come from a distribution centered around their respective group.
        - Hierarchial Bayesian Models are fundamentally a mix of pooling and no-pooling models.

- **Metropolis-Hasting Algorithm**
    - Metropolis-Hasting algorithms is a Monte Carlos Markov Chain (MCMC) method of sampling a distribution when traditional methods fail only requires begin able to evaluate the density function
    - The metropolis-hasting algorithm is defined by the confidence generating density function q(x, y)
    - The algorithm works as follow:
        1. Draw y from q(x,) and u from U(0,1)
        2. If u <= alpha(x^i, y) set x^(j+1) = y
        3. otherwise, set x^(j+1) = x^(j)
    
- **What are N-Grams?**
    - N-Grams are used extensively in text minning they are sets of co-occuring words within a given window (typically windows of 2).
    - When Computing n-grams you typically move one word forward. Though you can move N words forward.
    - By moving words forward you create unique word pairings for further texting processing (i.e. topic modeling).

- **Topic Modeling**
    - Topic modeling are methods of organizing, understand, and summarize a collection of documents
    - Applications of Topic Modeling:
        - Discovery hidden topical patterns that are present across the collection
        - Annotating documents by there topics
        - Use annotations to organize search and summarize topics
    - Topic Modeling can be used to find groups of words that best describe info in the document collection
    - **Latent Dirichet Allocation (LDA)**
        - LDA views each document is a mixture of topics that are present in the corpus. The model proposes that each word in the document is attribute to of those topics.
        - Collapsed Gibbs sampling is one way the LDA learns the topics and the topic representations of each document. The procedure is as follows:
            1. Go through each document and randomly assign each word in the document to one of K topics (K is chosen beforehand)
                - This random assignment gives topic representations of all documents and word distributions of all the topics, albeit not very good ones.
            - For each document d, go through each word w and compute:
                2. p(topic t | document d): proportion of words in document d that are assigned to topic t
                3. p(word w| topic t): proportion of assignments to topic t, over all documents d, that come from word w
                4. Reassign word w a new topic t’, where we choose topic t’ with probability
                p(topic t’ | document d) * p(word w | topic t’)
        - This generative model predicts the probability that topic t’ generated word w
        - On repeating the last step a large number of times, we reach a steady state where topic assignments are pretty good. These assignments are then used to determine the topic mixtures of each document.
    - **TextRank**
        - TextRank is a graph-based algorithm that derives keywords/keyphrases that represent the collection of document based on the information derived from the entire graph. The basic idea, implemented by a graph-based ranking model, is that of “voting”
        - The voting works through links between the vertex's. When one vertex links to another on thats a vote for that other vertex. Thereby, increasing the importance of vertex that recieved the link.
        - Additionally, the importance of the vertex casting the vote determines how important the vote itself.
        - **TextRank Algorithm**
            1. Identify text units that best define the task at hand, and add them as vertices in the graph.
            2. Identify relations that connect such text units, and use these relations to draw edges between vertices in the graph. Edges    can be directed or undirected, weighted or unweighted.
            3. Iterate the graph-based ranking algorithm until convergence.
            4. Sort vertices based on their final score. Use the values attached to each vertex for ranking / selection decisions.