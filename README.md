This project focuses on developing an autonomous natural language classification system to optimize the analysis of unstructured operational data. The model aims to classify and identify patterns in failure reports from Centro Industrial Ternium, enabling streamlined processes and providing actionable insights for improving operational efficiency.

The mathematical and computational model developed uses Natural Language Processing (NLP) and Unsupervised Machine Learning techniques to classify free-form text entries, address inconsistencies in data, and identify clusters of similar failure types.


## **Business Understanding** 
The primary objective is to provide a system capable of analyzing failure reports for operational optimization at Ternium. The analysis targets specific areas in the reports that are crucial for identifying recurring issues and improving maintenance processes.

## **Data Preparation**
### Exploration
The raw dataset contains over 64,000 rows with 13 columns, including free-form text fields like "Descripción" and "¿Qué pasó?" that describe reported failures. The exploration stage involves understanding the distribution and quality of the data, identifying critical text fields for model input, and ensuring the data is ready for NLP processing.

### Cleaning and Standardization
- **Text Cleaning**: The data is preprocessed to standardize text format. All entries are lowercased, and special characters, punctuation, and irrelevant stopwords are removed using **Regex** and **`nltk`**.
- **Error Correction**: Domain-specific spelling corrections and standardization are performed using a custom dictionary.
- **Tokenization and Lemmatization**: The cleaned text is tokenized into words (unigrams), and stemming or lemmatization is applied to reduce words to their base forms.

### Translation
The free-form Spanish text is translated to English using the `googletrans` library to leverage the capabilities of English NLP libraries, enabling better tokenization and processing. Translations are carried out while preserving the context of operational terminologies.

## **Feature Extraction**
### TF-IDF Transformation
- **TF-IDF Vectorization**: The `TfidfVectorizer` from `scikit-learn` is used to transform the text into a **Term Frequency-Inverse Document Frequency (TF-IDF)** matrix. This matrix represents the significance of terms across failure reports, highlighting the most informative words.
- **Parameter Tuning**: The `max_features` parameter limits the vocabulary size, and the `ngram_range=(1,2)` allows for both unigrams and bigrams. `min_df` and `max_df` thresholds filter out terms that are either too common or too rare, ensuring optimal feature selection.

### Dimensionality Reduction with NMF
- **Non-negative Matrix Factorization (NMF)**: The NMF model is applied to the TF-IDF matrix to reduce dimensionality while preserving the semantic structure of the data.
- **Choosing the Number of Components**: An optimal number of components is determined using reconstruction error analysis, selecting the number of clusters that captures maximum variance without overfitting.

## **Modeling and Clustering**
### Clustering with K-Means
- **K-Means Clustering**: The reduced NMF matrix is fed into a K-Means algorithm, which groups failure reports based on semantic similarity. The **elbow method** is used to find the optimal `k` (number of clusters), ensuring balanced cluster size and distinctiveness.
- **Initialization and Random States**: The clustering is initialized multiple times (`n_init` parameter) to avoid convergence to local minima, ensuring the model finds the optimal cluster centers.

### Cosine Similarity Calculation
- **Cosine Similarity**: To evaluate the proximity of cluster centroids and failure reports, cosine similarity is calculated, which is particularly effective for text data. This allows visualization of how closely related different clusters are.
- **Visualization**: A similarity heatmap is created to assess the cohesiveness of clusters, revealing groups with shared context.

## **Evaluation and Interpretation**
### Visualization and Interpretation of Clusters
- **t-SNE/PCA Visualization**: The clusters are visualized using dimensionality reduction techniques like t-SNE or PCA to interpret their structure in 2D space.
- **Key Terms Analysis**: Word clouds and bar plots are generated to display the most significant words within each cluster, providing a semantic interpretation of each group's main topic.

### Cluster Quality Metrics
- **Silhouette Score and Davies-Bouldin Index**: Metrics are computed to evaluate the compactness and separability of the clusters. Higher silhouette scores indicate well-separated and cohesive clusters.

## **Results and Recommendations**
- **Classification Results**: The model groups failure reports into distinct clusters, each representing specific operational themes (e.g., equipment failures, oil leaks, system errors). These clusters facilitate automated classification of new reports.
- **Operational Insights**: The analysis highlights areas for improvement in data quality and operational processes. Recommendations include:
  - **Standardizing Data Input**: Transition to structured form-based data entry to reduce variability in text entries.
  - **Proactive Maintenance**: Use clustering insights to detect recurring failure types and prioritize maintenance efforts accordingly.
  - **Optimization of Data Storage**: Implement strategies to store pre-classified reports for quick retrieval and analysis.

## **Constraints and Considerations**
1. **Time and Budget**: The project focuses on processing textual data within a feasible time limit and computational budget.
2. **Model Robustness**: Models are tested for robustness against noisy input and spelling variations, ensuring reliable classification across a variety of text inputs.

By implementing this natural language classification system, Ternium can effectively categorize operational issues, enabling faster response times, targeted maintenance, and overall process improvement.

