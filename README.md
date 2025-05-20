# Unsupervised Industry Clustering from Earnings Call Transcripts

## Authors
- **Sung Ahn** and **Chris Yang**

## Project Question
**Can we figure out which industry a company is in just by analyzing the language used in their earnings call transcripts using unsupervised learning (clustering)?**

This project explores whether latent linguistic patterns—extracted from public earnings call transcripts—can be used to group companies by industry *without using any industry labels during training*.

---

## Dataset
We collected quarterly earnings call transcripts for **20 publicly traded companies** across **five industries**:
- **Information Technology**
- **Semi-Conductor**
- **Airlines**
- **Finance**
0 **Real Estate**

Each company has 6–8 quarterly transcripts between **Q1 2023 and Q4 2024**, resulting in a corpus of **160+ documents**. Each transcript represents one quarterly earnings call.

---

## Methodology

### 1. Text Preprocessing & Feature Engineering
- **TF-IDF Vectorization**
- **Stopword removal** 

### 2. Dimensionality Reduction
- **Truncated SVD** to reduce sparse TF-IDF matrix to a dense, low-dimensional representation (e.g., 50D → 2D)

### 3. Clustering (Unsupervised)
- Applied **K-Means** clustering without using any industry labels
- Explored other clustering methods (e.g., Hierarchical, DBSCAN) for robustness

### 4. Post-Hoc Evaluation
- Industry labels were used **only after clustering** to assess how well unsupervised clusters align with true industry categories
- Evaluated using:
  - **Cluster purity**
  - **Confusion matrices**
  - **Silhouette scores**
  - **2D PCA/t-SNE visualizations**

---

## Goal
To determine whether **industry identity is embedded in corporate communication** and whether unsupervised learning methods can recover those groupings—purely based on **textual language structure and tone**, without relying on explicit metadata like stock price or financial ratios.

---