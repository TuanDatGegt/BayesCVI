# Bayesian Cluster Validity Index (BCVI)

## 1. Introduction
Clustering is a fundamental unsupervised learning technique used to group similar observations in data science and machine learning. A crucial step in this process is determining the optimal number of clusters, a task often performed using Cluster Validity Indices (CVIs).

This project introduces a new CVI called the **Bayesian Cluster Validity Index (BCVI)**. BCVI builds upon existing CVIs by integrating user expertise through Dirichlet and Generalized Dirichlet priors. This innovative approach allows for flexible, customizable selection of the optimal number of clusters, making it adaptable to specific application needs. BCVI can be applied to both **hard clustering** (e.g., K-Means) and **soft clustering** (e.g., Fuzzy C-Means) algorithms.

---

## 2. Research Objectives
The primary objective of this project is to develop the BCVI for evaluating the validity of the number of clusters in data clustering problems, particularly for image and real-world datasets. BCVI aims to determine the optimal number of clusters more accurately than traditional CVI methods, thereby improving the overall quality of clustering results.

---

## 3. Methodology and Algorithms

### 3.1. Clustering Algorithms
- **K-Means**: A simple yet effective algorithm that partitions data into k clusters. It works by assigning each data point to the nearest centroid and iteratively updating centroids until convergence, minimizing the Within-Cluster Sum of Squares (WCSS).
- **Fuzzy C-Means (FCM)**: A soft clustering technique where each data point is assigned a degree of membership to each cluster. The algorithm's objective is to minimize a function based on membership degrees and distances to cluster centroids.

### 3.2. Traditional Cluster Validity Indices (CVIs)
The following traditional CVIs serve as the foundation for the BCVI framework:

**Hard Clustering:**
- Calinski-Harabasz (CH)
- Cluster Validity Index based on Nearest Neighbors (CVNN)
- Davies-Bouldin (DB)
- Silhouette (SH)
- Starczewski (STR)
- Wiroonsri (WI)

**Soft Clustering:**
- KWON2
- Wiroonsri and Preedasawakul (WP)
- Xie and Beni (XB)

### 3.3. Bayesian Cluster Validity Index (BCVI)
BCVI combines prior knowledge with observed data using Dirichlet and Generalized Dirichlet distributions to identify the optimal number of clusters.

**Key Steps:**
1. **Select Base CVIs**: Choose one or more traditional CVIs as the foundation.
2. **Apply Dirichlet or Generalized Dirichlet Priors**: Use these distributions to establish a prior probability for the number of clusters based on user expertise or domain knowledge.
3. **Compute Posterior Distribution**: Based on the data and the chosen prior, calculate the posterior distribution to derive probabilities for a range of possible cluster numbers.
4. **Determine Optimal Cluster Count**: The optimal cluster count is selected based on the posterior probabilities. BCVI can identify local maxima, giving users flexible options for choosing the most suitable number of clusters.

**BCVI Properties:**
- **Flexibility**: Allows for customization based on prior knowledge.
- **Evidential**: Integrates data-driven evidence with prior beliefs.
- **Provides Multiple Options**: Can detect local maxima in the posterior distribution.
- **Accuracy**: Improves the determination of the optimal number of clusters.

---

## 4. Experimental Applications

### 4.1. Datasets
- **Synthetic Data**: Generated from Gaussian and Uniform distributions (sourced from O-PREEDASAWAKUL 2023's GitHub). This data allows for controlled evaluation of BCVI's performance under ideal conditions.
- **Real-World Data**: The Dry Bean Dataset from the UCI Machine Learning Repository (M. Koklu, Ilker Ali Özkan, 2020). This dataset contains seven similar types of beans and is used to test BCVI's robustness in a real-world setting.
- **Brain MRI Images**: Original data from the preceding BCVI research paper, used for brain tumor detection.

### 4.2. Experimental Procedures
1. **Image Preprocessing**: Normalize image sizes to 128x128 pixels and standardize pixel values.
2. **Clustering**: Apply K-Means and FCM algorithms to the datasets.
3. **Evaluation**: Assess clustering using both traditional CVIs and BCVI.
4. **Testing**: Experiment with various values of K and different base CVIs.

---

## 5. Key Findings
- BCVI significantly improves the ability to determine the optimal number of clusters.
- In the brain tumor detection task, BCVI consistently identified the optimal number of clusters as **K=4**. Even with K=5, K-means successfully segmented the tumor.
- Clustering accuracy on the real-world dataset exceeded **75%**.
- BCVI can correct for suboptimal cluster numbers suggested by base CVIs.

---

## 6. Potential Applications
- **Healthcare**: MRI image processing, tumor detection.
- **Marketing**: Customer segmentation.
- **Scientific Research**: Applications in biology, sociology, and other fields.
- **Big Data**: Processing large datasets.

---

## 7. Research Limitations
- **Sensitivity to Alpha**: Performance is dependent on the selection of the prior's alpha (α) value.
- **Data Size**: The method's effectiveness may be sensitive to the size of the dataset.
- **Data Quality**: The quality of the input data significantly influences the results.
- **Reliance on Base CVIs**: The performance of BCVI is limited by the quality of the underlying CVI.
- **Data Type**: BCVI may not be suitable for all types of data.
- **Synthetic vs. Real-World**: Synthetic data may not fully reflect the complexity of real-world scenarios.

---

## 8. Future Work
- Test BCVI on larger medical datasets.
- Integrate BCVI into a diagnostic support system.
- Extend BCVI to incorporate other types of prior distributions.
- Evaluate its performance on more complex and high-dimensional datasets.
