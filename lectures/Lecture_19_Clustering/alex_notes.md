# Lecture 19: Clustering

- **Cluster Analysis**
    - Clustering is the process of making groups of abstract objects into classes of similar objects
    - The main advantage of clustering over classification is that it is adaptive to changes and helps sinle out useful features that distinguish groups
    - Groups are partioned into groups based upon the data similarity and these groups of similar data points are then assigned labels
    - Clustering is utilized a multitude of fields: data mining, marketing, and image processing.

- **Clustering Algorithms**
   
    - **K-Means:**
        - The K-Means clusters data by separating samples into groups of equal variance, minimizing a clusters interia or within cluster sum of squares
        - Interia or the within-cluster sum of squares criteria are measures of how internal cohension of a cluster.
        - **K-Means Algorithms**
            1. Choose initial centroids, the similist method si to randomly initialized the centriods.
            2. Create new centroids by taking the mean value of all samples assigned to previous centroid.
            3. Computer the difference between the new centriod and old centriod. Check if there difference between the new and old centriods are below a certain threshold.
            - Step 2 and 3 repeat until the variance difference between the new and old centriod falls below a certain threshold.
        - K-Means is equavalent to the exception-maximization algorithm with a small, all-equal, covaraince matrix.
        - K-Means does need to be told how many clusters it's working with. 
        - **typically you assign the variable K to the number of clusters your looking for**
    
    - **Mean-Shift**
        - Mean-Shift clustering algorithm exploits the idea of Kernel Density Estimation (KDE) by imagining what the data would do if they climbed up the hill to the nearest peak.
        - Mean-Shift does this by iterating shifting each data point uphill until it reaches the nearest peak.
        - **Mean-Shift Algorithm**
            - For every data point
                1. is the data point at a KDE peak? 
                2. if no calculate the shift and then shift the data point
                3. if yes you've reached the peak and your done.
        - Clusters at one level will join with cluster at the next level
    
    - **Hierarchical Clustering**
        - Hierarchicalclustering is where you bluild a cluster tree (dendogram) to represent the data, where each group links bewteen two or more successor groups 
        - Each node in the cluster tree contains a gorup of similar data points, nodes group on the graph next to each other similar nodes
        - clusters at one level will join with clusters at the next level using there degree of similarity. This process of joining clusters contains until you only have one.
        - Dendograms is a type of tree diagram that shows the Hierarchical Clustering
        - **Hierarchical Clustering Algorithms**
            - There are two major Hierarchical clustering algorithms: Bottom Up (Hierarchical Agglomentre Clustering, HAC) and Top Down (Divisive Clustering)
            - **HAC**
                - The majority of Hierarchical Clustering Algorithms are Bottom up type of algorithm
                1. Treat each document as a signle cluster in the beginning. 
                2. Merge two items at a tiem int oa new cluster. How pairs emerge involves calculating disimilarity or similarity between each merged pair. Here are some of calculating disimilarity or similarity:
                    1. Complete Link: Similarity of the further pair (this method is exposed to outliers)
                    2. Single Link: Similarity of the closest pair
                    3. Group averages: similarity bewteen groups
                    4. Centroid Similarity: each iteration merges the cluster with the most similar central point
                3. The pairing continues until one cluster is formed.
                - **Downside**
                    - HAC algorithms typically require large computation and storage resources when working with large datasets
            - **Divisive Clustering**
                1. Data Starts as one gaint cluster
                2. the cluste splits into two distinct clusters according to some measure of the degree of similarity
                3. Slusters split into 2 again and again until cluster only contain one data point
        
- **Validating Unsupervised Methods**
    - **How to evaluate a cluster?**
        - user interpretation does the cluster seem to correspond to a specific topic
        - Internal criteria of a good clustering will produce high quality clusters with high intra-cluster similarity and low inter-cluster similarity
        - There are typically two ways of evaluating a clusters quality: 
            - internal indexes: a method of determinining cluster quality without having to know ground truth.
            - external indexes: If true class labels (ground truth) are known, the validity of a clustering can be verified by comparing the class labels and clustering labels

    - **Internal Index Methods**
        - **Sum of Square Error**
            - when using K-Means, plot the sum of squared error (SSE) for different K values
                - SSE will decrease as you increase the number of clusters
                - knee points in the SSE curve suggest good candidates for the number of clusters
        - **Stability Based Method**
            - Stability is defined as repeatedly producing similar clusters on data originating from the same source
            - Typically evaluating clusters with stability based methods requires evaluating multiple methods, and select the model resulting in the highest level of stability

            - Assessing Stability through Model Prediction Accuracy
                - For each K
                    1. Randomly split the data into training and testing. Along with keep track of cluster label
                    2. For each split:
                        - Cluster the training data using k
                        - Predict assignment for test set and compare it to the clustering result on test set
                    3. - Stability(k) = mean Prediction strength
                - Select k that maximize stability
    
    - **External Index Methods**
        - Given partition (P) and ground truth (G), measure the number of vector pairs that are:
            1. in the same class both in P and G.
            2. in the same class in P, but different classes in G.
            3. in different classes in P, but in the same class in G.
            4. in different classes both in P and G.
        - Compare to the expectation of the index assuming a random partition of the same cluster sizes




