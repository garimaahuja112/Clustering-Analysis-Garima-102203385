# Clustering Analysis
This project performs a clustering analysis on the Heart Failure Clinical Records Dataset to explore different clustering models and preprocessing techniques to identify the best configuration for grouping patients based on their clinical records.

# Dataset
The dataset used in this project is heart_failure_clinical_records_dataset.csv, sourced from UCL (University College London), which contains clinical records of patients who have suffered from heart failure. The dataset contains 299 rows and 13 columns, including features such as age, gender, anaemia, high blood pressure, ejection fraction, serum creatinine levels, etc., and a target variable (DEATH_EVENT) where 0 represents patient did not die and 1 represents patient died during the follow-up period. For the purposes of this clustering analysis, the target variable has been excluded to enable unsupervised learning purely based on patient characteristics.

# Models Evaluated
The following clustering models were evaluated:

- **KMeans:** A centroid-based clustering technique that partitions the data into k clusters by minimizing intra-cluster variance.

- **Hierarchical Clustering (Agglomerative):** A bottom-up approach that builds clusters hierarchically by merging or splitting them based on linkage criteria.

- **Spectral Clustering:** A graph-based method that uses the eigenvalues of a similarity matrix to reduce dimensionality before clustering.

# Preprocessing Techniques Applied
The models were evaluated under different preprocessing configurations to assess their impact on clustering quality:

- **None:** No preprocessing applied.

- **Normalization:** Features were scaled using normalization.

- **Transformation:** Power transformation was applied to make data more Gaussian-like.

- **PCA:** Dimensionality was reduced using Principal Component Analysis.

- **T + N:** Combination of transformation and normalization.

- **T + N + PCA:** Combined transformation, normalization, and dimensionality reduction using PCA.

# Cluster Counts Evaluated
The models were evaluated with different numbers of clusters to assess their impact on clustering performance:
- 3 Clusters
- 4 Clusters
- 5 Clusters

# Evaluation Criteria
Each model-preprocessing-cluster combination was evaluated using the following metrics:

- **Silhouette Score:** Measures cohesion and separation of the clusters. Higher values indicate well-defined clusters.

- **Calinski-Harabasz Index:** Ratio of between-cluster dispersion to within-cluster dispersion. Higher is better.

- **Davies-Bouldin Index:** Measures the average similarity between each cluster and its most similar one. Lower values are better.

- **Composite Score:** A weighted combination of all three metrics to assess overall clustering performance:\
  ```40% Silhouette Score, 40% Calinski-Harabasz Index, 20% Inverted Davies-Bouldin Index```

# Results
After evaluating all combinations of models, preprocessing methods, and cluster counts, the best configuration for each model was identified based on a composite score combining the Silhouette Score, Calinski-Harabasz Index, and Davies-Bouldin Index.

**Best Configuration for Each Model:**
|   Model    |Preprocessing|Clusters|Silhouette Score|Calinski-Harabasz Index|Davies-Bouldin Index|Composite Score|
|------------|-------------|--------|----------------|-----------------------|--------------------|---------------|
|Hierarchical|     NaN     |   5    |      0.541     |         558.6         |        0.490       |    0.966303   |
|KMeans      |     PCA     |   5    |      0.536     |         602.3         |        0.509       |    0.993372   |
|Spectral    |    T + N    |   3    |     -0.063     |          2.0          |        5.454       |    0.359796   |

The **overall best configuration across all models** was achieved by the **KMeans model** with **PCA preprocessing** and **5 clusters**, obtaining the highest composite score of **0.993372**.
