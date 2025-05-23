# Unsupervised Industry Clustering from Earnings Call Transcripts

## Authors
- **[Sung Ahn](https://github.com/sahn1998)**
- **[Chris Yang](https://github.com/ChristufaY)**

## Project Question
**Can we infer a company’s industry based purely on the language used in its earnings call transcripts, using unsupervised learning?**

This project explores whether latent linguistic patterns (words extracted from quarterly earnings call transcripts) can be used to cluster companies by industry without using any industry labels during training.

---

## Goal
- To investigate whether **industry-specific language** appears consistently in earnings calls
- To determine whether **unsupervised learning models** can uncover these hidden groupings from raw text
- To explore how companies from the same or different industries diverge in their communication style, tone, and terminology

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

### 1. Text Preprocessing
- Lowercasing, stopword removal, lemmatization
- TF-IDF vectorization with top **`n` number of frequent terms**

### 2. Dimensionality Reduction
- **Truncated SVD** to reduce TF-IDF to 50-100 components
- **PCA** used after SVD for visualization and clustering prep
- **t-SNE** and **2D PCA plots** used for interpretability

### 3. Unsupervised Clustering
- **K-Means clustering** on PCA-reduced components (50D)
- Used silhouette score and elbow method to guide number of clusters
- Optionally evaluated **GMM** and **hierarchical clustering** (future work)

### 4. Post-Hoc Evaluation
- Industry labels used **only after** clustering to assess alignment
- Metrics used:
  - Cluster purity
  - Confusion matrices
  - Silhouette scores
  - PCA and t-SNE visualizations, labeled by sector

---