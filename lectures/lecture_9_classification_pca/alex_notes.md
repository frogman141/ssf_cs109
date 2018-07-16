# Lecture 9: Classificaiton and Dimensionality Reduction

## I focused primarily on dimensionality reduction techniques in these notes not the K-NN classification Algorithm

- **Curse of Dimensionality:**
    - A brief summary when dimensionality in a dataset increases , the volume of the space increases so fast that the avaliable data becomes sparse.
    - Statistically, sound result requires the sample size N to grow exponentailly as d Dimensions increases.
    - This is extremely impractical.

- **The Basic Ideas behind Dimesionality Reduction**
    - There really only two major basic methodologies of reducing data projection and manifold learning
    - **Projection:**
        - In real world problems training instance do not cross all dimensions equally. Most features are constant while others are highly correlated with each other.
        - These correlations between a few dimensions and overall constant in the other dimensions mean training instances actually lie within a lower-dimensional subspace. 
        - Therefore, if project the high-dimension dataset into this lower-dimensional subspace will find that the lower-dimensional subspace is a better fit on the data.
        - This is the basic principal that **Principal Compenent Analysis (PCA)** follows
    - **Manifold Learning**
        - Manifold learning are dimensionality techniques that really upon the manifold hypothesis.
        - The Manifold hypothesis states high-dimensional datasets lie close to a much lower-dimensional dataset. 
            - What this means is that the degree of Freedom to generate X is lower that the degreee of Freedom to generate anything.
    
- **PCA**
    - **Overview**
        - PCA is the most common dimensionality reduction algorithm. It can be used for data-compression, visualization of high-dimensional datasets, feature selections, and noise cleaning.
        - The aim of PCA is perserve as much variance in a dataset as possible while reducing the number of dimensions. This is done by first identifying the hyper-plane that lies closest to the data, and then projects the data onto it.
        - Before PCA projects the data into a lower-dimensional space. It first identifies the axis that preserves the maximum amount of  variance in the data for each d dimension in the dataset.
    
    - **PCA Algorithm**
        1. Subtract the mean of from the data (Center X/Z-scaling)
        2. Scale each dimension by it's variance. This helps PCA pay less attention to magnitude of dimensions.
        3. Compute covariance matrix S
        4. Compute k largest eigenvector of S
        5. These eigenvector are the K **Principal Components**.
    
    - **Projecting data into a lower dimension**
        - Once all of the **Principal Components** ahve been identified you can project data into d dimensional space. 
        - This project of the dataset onto a hyperplane is done by computing the dot product by the training set matrix X by the matrix
        Wd. Where Wd is defined as the matrix of the first d **Principal Components**.
    
    - **Explained Variance Ratio's** indicates the proportion of the datasets variance lies alng the axis of each **Principal Component**.

    - **Choosing the right number of Components**
        - The generally philospophy for choosing the right number of components is to choose the number of dimensions that explain 95% of the variance.
        - A way to visualization this to use for this is the elbow plot. Where you plot the explained variance ratio as a function of Principal Components.

    - **Useful Info about PCA:**
        - You can decompress your data after compressing it with PCA. When decompress your data though there will be a slight loss of information. This side effect of PCA is typically utilized for removing noise from data.
        - There are ways to identify what dimensions in a dataset are related which principal compenonents. This is done by creaint a coerrlation matrix between the dimensions and principal component. However you data needs to be z-scaled for this to work.
    
    - **Alternative implementations of PCA**
        - Incremental PCA
        - Randomized PCA
        - Kernal PCA

- **Multi-Dimensional Scaling**
    - This reduction algorithms aims to find a set of points whose pairwise disctance match a given distance matrix.
    - In essesence what it's doing is reducing dimensionality while preserving the distance between the instances.

- **Other Dimensionality Reduction Methods**
    - **Isomap** creates a graph by connecting each instance to its nearest neighbors, then reduces dimensionality while trying to preserve the geodesic distances9 between the instances.
    - **Locally linear embedding (LLE)** works by first measuring how each training instance linearly relates to its closest neighbors (c.n.), and then looking for a low-dimensional representation of the training set where these local relationships are best preserved (more details shortly).
    - **t-Distributed Stochastic Neighbor Embedding (T-SNE)** reduces dimensionality while trying to keep similar instances close and dissimilar instances apart. It is mostly used for visualization, in particular to visualize clusters of instances in high-dimensional space
    - **Linear Discriminant Analysis (LDA)** is actually a classification algorithm, but during training it learns the most discriminative axes between the classes, and these axes can then be used to define a hyperplane onto which to project the data. The benefit is that the projection will keep classes as far apart as possible, so LDA is a good technique to reduce dimensionality before running another classification algorithm such as an SVM classifier