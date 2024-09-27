# Natural Language Classifier for Operational Data Analysis

This project focuses on developing an autonomous natural language classification model to analyze and categorize unstructured text data from failure reports at Centro Industrial Ternium. By leveraging NLP and unsupervised machine learning, the goal is to identify patterns in operational issues, helping to streamline processes and reduce manual analysis.

## What Was Obtained
- **Organized and Standardized Data**: A cleaned and structured dataset that allows for easier and more efficient analysis of operational failure reports.
- **Automated Classification**: A model that automatically classifies and identifies patterns in textual data without requiring labeled examples.
- **Actionable Insights**: Visualizations and clustering of key terms that highlight major operational challenges and areas for improvement, aiding in decision-making and process optimization.

## **Business Understanding**: 
   - Understand the operational needs of Ternium and the nature of the failure reports to target key areas for analysis and optimization.
   
## **Data Preparation**: 
   - **Exploration**: Review the raw data to understand its structure and identify key columns containing textual information relevant to the operational issues.
   - **Cleaning**: Handle missing values, correct spelling errors, and standardize the text format for consistency.
   - **Translation and Tokenization**: Use NLP techniques to translate Spanish entries to English and tokenize the text for further processing.
   
## **Feature Extraction**:
   - **TF-IDF Transformation**: Convert the cleaned text data into a TF-IDF matrix, capturing the importance of words within each failure report.
   - **Dimensionality Reduction with NMF**: Reduce the dimensionality of the TF-IDF matrix using NMF, enabling better clustering and visualization of patterns in the text.
   
## **Modeling and Clustering**:
   - Implement clustering techniques to group similar failure reports based on the reduced features from NMF.
   - Calculate cosine similarity to measure and visualize the closeness of clusters.
   
## **Evaluation and Interpretation**:
   - Visualize the classified clusters to interpret the main operational issues and their similarities.
   - Provide recommendations based on the analysis, focusing on standardization of data entry and highlighting key operational problems.

## **Results and Recommendations**:
   - Successfully classify failure reports into meaningful groups.
   - Provide actionable recommendations to improve data quality and operational processes.
