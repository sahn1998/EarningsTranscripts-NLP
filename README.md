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
We collected quarterly earnings call transcripts for **20 publicly traded companies** across **six industries**:
- **Information Technology**
- **Semi-Conductor**
- **Airlines**
- **Finance**
- **Real Estate**
- **Consumer Goods**

Each company has 6–8 quarterly transcripts between **Q1 2023 and Q4 2024**, resulting in a corpus of **120+ documents**. Each transcript represents one quarterly earnings call.

---

## Methodology

### 1. Text Preprocessing
- Cleaning steps including lowercasing, removing URLs, emails, financial boilerplate, numbers, and non-alphabetic characters
- Tokenization and lemmatization to reduce words to their root forms
- Customized stopword removal to filter out common but uninformative words

### 2. Vectorization with TF-IDF
- Converted cleaned text into numerical form using TF-IDF (Term Frequency-Inverse Document Frequency)
- Included unigrams and bigrams to capture single words and common phrases
- Limited vocabulary to the top 1,000–2,000 most informative terms to balance detail and noise reduction

### 3. Dimensionality Reduction
- Applied Singular Value Decomposition (SVD) to reduce the high-dimensional TF-IDF matrix to a smaller set of latent semantic components
- Followed by Principal Component Analysis (PCA) on the SVD output for visualization and further compression
- Scree plots guided the selection of approximately 30–60 components, explaining over 90% of data variance

### 4. Matrix Completion Validation
- Artificially masked 35% of TF-IDF entries to test whether low-rank approximations could recover missing data
- Demonstrated that dimensionality reduction effectively captures core data structure beyond observed values

### 5. Unsupervised Clustering
- Applied K-Means and Agglomerative Hierarchical Clustering on reduced datasets
- Explored various linkage methods for hierarchical clustering and set cluster count to six, matching sector count
- Generated dendrograms, cluster-sector heatmaps, and PCA scatterplots for cluster interpretation

### 6. Post-Hoc Evaluation
- Compared cluster assignments to true industry labels only after clustering
- Used metrics including silhouette scores, cluster purity, and visualization to assess clustering quality

---

## Key Findings

1. Distinct clusters emerged for sectors like Technology, Semiconductors, and Real Estate, indicating consistent industry-specific language patterns.
2. Clusters mixing multiple sectors often captured shared financial or corporate communication styles transcending industries.
3. Agglomerative clustering frequently grouped Tech and Semiconductors together, reflecting their related communication and business domains.
4. The Airline sector showed fragmented clusters, likely due to diverse messaging themes driven by varied operational focuses.
5. Silhouette scores peaked with 10-component SVD-reduced data, confirming that fewer, stronger dimensions yield clearer clusters.
6. Hierarchical clustering (especially Ward linkage) generally outperformed K-Means by capturing more nuanced cluster shapes.

---

## Future Work
- Experimenting with advanced embedding methods (e.g., BERT, Word2Vec) to capture deeper semantic meaning beyond TF-IDF
- Exploring additional clustering methods (e.g., Gaussian Mixture Models, DBSCAN) and hybrid approaches
- Enhancing preprocessing with domain-specific stopwords, named entity recognition, and phrase detection
- Dynamic vocabulary selection based on term relevance to improve signal-to-noise ratio in clustering inputs