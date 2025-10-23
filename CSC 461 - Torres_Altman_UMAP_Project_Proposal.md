
# CSC 461 Project Proposal
#### 10/17/25 

#### Team Members - Thomas Torres, Amy Altman

### Problem Definition - How has a newer dimension reduction algorithm (UMAP) improved on previous methods and what are its strengths and weaknesses?

Dimension reduction takes a dataset of high dimensional data and maps it to a lower dimensional dataset that can be visualized while preserving some structure of the higher dimensional data. Throughout the decades many algorithms have been produced to handle the issue of dimension reduction, but they all have unique tradeoffs. We are going to focus on one of the newest algorithms UMAP which we briefly touched on in class. We want to provide an intuitive and mathematical description for this dimension reduction algorithm works under the hood. I also want to implement this algorithm in Python, and start out by trying them on the Mammoth data set and the Mnist data set.

The activity in class covered all the following dimension reduction techniques- PCA, t-SNE, PaCMAP, and UMAP, but only at a quick glance. I am hoping to go much further. We are gonna focus on UMAP because it was one of the most capable and modern algorithms. We will implement data from the Mammoth set, MNist set, and synthetic datasets of our design in order to show the capabilities and limitations of UMAP.

### Introduction

##### Provide Context and existing work for the problem. 

PCA quickly performs dimension reduction on a dataset but assumes the dataset is linear, in turn only producing projections onto linear subspaces that do not necessarily respect the structures of clusters in high dimensions. In 2008, t-SNE significantly improved upon PCA and other existing dimension reduction techniques, but t-SNE is an old algorithm with an expensive $O(n^2)$ computational cost for $n$ data points. t-SNE tends to be good at preserving local structure, but the preserved local structure is at the expense of global structure. Therefore, t-SNE and PCA has since left much to be desired. However, much innovation has occurred within the last 5 years on better dimension reduction algorithms. 

We will focus on UMAP, because it improves upon features that both PCA and t-SNE fail at. UMAP is better at producing local low level projections, and has a significantly lower time complexity than previous algorithms with similar focusses. Because UMAP is able to get the performance of simpler algorithms without making linearity assumptions or being limited to higher level projections. 

The existing work for these problem already exists and is explained thoroughly in the respective research papers UMAP. The main purpose of our project is to gain an in-depth understanding of a powerful, flexible modern machine learning algorithm and share its applications and limitations with our class with an example and an overview of the literature

##### What prior work in the field are you building off of?

These are the research papers for background and the primary paper on the UMAP algorithm:

- UMAP: [https://arxiv.org/pdf/1802.03426](https://arxiv.org/pdf/1802.03426)
- Trade-Offs Between Different Algorithms/PaCMAP: [https://arxiv.org/pdf/2012.04456](https://arxiv.org/pdf/2012.04456)
- PCA : [https://www.cs.cmu.edu/~elaw/papers/pca.pdf](https://www.cs.cmu.edu/~elaw/papers/pca.pdf)
- Duke UMAP Clustering Paper for Data and Replication of Figures: [https://sites.duke.edu/dimensionreduction/](https://sites.duke.edu/dimensionreduction/)

Depending on how the scope of the project changes, the methods and according papers we use will be subject to change. We included a lot of sources to start with since it is better than a few. The papers about the older dimension reduction algorithms will be briefly touched on when talking about the improvements and specific strengths of UMAP.
---
# Data Description

Our aim for the data is replication of results in research papers, primarily using the MNIST Dataset and the Mammoth dataset. Two additional categories of datasets will additionally be used. The first is a synthetic dataset using the make_blobs from scikit to create a variety of gaussian multi-dimensional clusters to illustrate the capability of UMAP and its limitations. We are also interested in finding a dataset on a public dataset repository such as Kaggle that hasn't been applied to UMAP yet and seeing if we can improve performance on that dataset by applying the newer dimension reduction algorithm.

##### Data Set 1.) [https://www.kaggle.com/datasets/hojjatk/mnist-dataset](https://www.kaggle.com/datasets/hojjatk/mnist-dataset)

The MNIST dataset contains handwritten digits from 0-9. The dataset is quite large, and was compile in 1988 by the US Postal Service. Each image in MNIST is $16 \times 16$ pixels and black and white.  The dataset is famous, and commonly used in educational settings and in research papers. It was used as an example in the Duke Dimension reduction paper site, as well as multiple papers above. It is a nice set to work with since we would already expect there to be 10 clusters formed following a projection. 

##### Data Set 2.) [https://github.com/MNoichl/UMAP-examples-mammoth/blob/master/umammoth.ipynb](https://github.com/MNoichl/UMAP-examples-mammoth/blob/master/umammoth.ipynb)
The Mammoth (and other animal sets in this collection of datasets) is a collection of points that constitute a Mammoth that can clearly be seen if plotted. It was generated by the authors of the UMAP paper in 2023, and was used in the UMAP paper and the Duke University Data Reduction site to showcase the benefits of UMAP at preserving the structure of the Mammoth set when projecting into 2d. The dataset is open source on GitHub, so it likely has been used by other academics, but largely it has been used by Duke University in their paper. 

---
# Methods, Tools, and Evaluation Metrics 
A big concern, especially for large datasets is computational complexity. For instance, a key advantage of UMap over other dimension reduction algorithms is that UMap is much quicker, so UMap's computational complexity should be lower across multiple applications. Space Complexity is also a large concern for algorithms operating over potentially billions of entries. 

A key evaluation metric for these models is visualization. Visualization gives us a direct window into the quality of a projection. Lower subspaces should reflect the expected characteristics of the MNIST and Mammoth datasets respectively. The MNIST data set is expected to have 10 clusters when projected since there are 10 digits from 0 through 9. The Mammoth set is expected to preserve the image of a Mammoth relatively well when it is projected down. 

Since we are looking to preserve clusters in many of these algorithms, we can use the silhouette score to compute the quality of the clusters after they have been projected into a lower dimensional space. It can also be verified that the projected clusters correspond to data, like in the instance of the MNIST data set. 



