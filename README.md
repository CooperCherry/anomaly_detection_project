# Network Intrusion Detection via Clustering and Feature Learning
## Overview

This project explores how unsupervised learning can be used to identify patterns in network traffic and distinguish between normal and anomalous behavior. Using the UNSW-NB15 dataset, the goal is not direct classification, but to understand how different types of traffic group together based on behavioral features.

## Goals
- Apply clustering techniques to a real-world cybersecurity dataset
- Compare methods for handling mixed numerical and categorical data
- Evaluate how well clustering captures differences between normal and attack traffic
- Explore feature learning as a way to improve clustering performance

## Methodology
- Data Processing
- Removed irrelevant infrastructure-specific features
- Separated numerical and categorical variables
- Applied scaling (numerical) and appropriate encoding depending on model
- Preserved labels only for evaluation purposes

## Models Used
- K-Means (baseline, numerical only)
- K-Modes (categorical data)
- K-Prototypes (mixed data)
- Neural Network + K-Means (feature-based clustering)

## Approach
- Perform baseline clustering on raw data
- Analyze cluster composition using attack distributions and feature averages
- Identify limitations in separating normal vs. anomalous traffic
- Train a neural network to learn feature representations
- Cluster learned features and compare results

## Key Findings
- Clustering consistently groups behavioral patterns, not strictly labels
- Attack-heavy clusters tend to show:
- high transmission rates
- low data volume
- repetitive, lightweight interactions
- Normal traffic clusters exhibit:
  - larger data exchanges
  - more variability and complexity
  - Significant overlap exists between normal and attack traffic, highlighting the difficulty of anomaly detection
- Feature-based clustering improves structure, producing more coherent and interpretable groupings.

## Limitations
- Clusters are not perfectly separable
- Some attacks closely mimic normal behavior
- Results depend on feature representation and model assumptions

## What I Learned
- Clustering is best used for pattern discovery, not direct classification
- Handling mixed data types is critical in real-world datasets
- Feature learning (via neural networks) can significantly improve clustering quality
- Model evaluation in unsupervised learning requires interpretation, not just metrics

## Future Work
- Explore alternative clustering methods (e.g., DBSCAN, Kamila)
- Improve feature representations and model architectures
- Investigate anomaly detection frameworks built on clustering outputs

## How to Run
- Open the Jupyter Notebook
- Run cells sequentially from preprocessing → clustering → analysis
- Ensure required libraries are installed (scikit-learn, kmodes, etc.)
