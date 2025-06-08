# Predicting EPS Movement (Up/Down) from Earnings Call Transcripts
Can we predict whether a company’s EPS increased from the previous quarter using only the language in its quarterly earnings call transcript? We aim to identify whether investor-facing communication in earnings calls contains reliable signals of company performance, using conventional machine learning models and NNs trained on TF-IDF representations of transcript text.

---

## Authors
- **[Sung Ahn](https://github.com/sahn1998)**
- **[Chris Yang](https://github.com/ChristufaY)**
- Aakash
- Josh
- Tyler

---

## Project Overview
This project investigates whether the textual content of quarterly earnings call transcripts can be used to **predict changes in company performance**, specifically **whether EPS increased from the previous quarter**. Building on our earlier work using **unsupervised learning** to uncover industry-specific linguistic patterns, we extend our analysis with **supervised classification** to explore predictive relationships between language and earnings outcomes.

---

## Dataset

We collected **200+ quarterly earnings call transcripts** from **+30 publicly traded companies** across **six industries**, covering quarters from **Q1 2023 to Q1 2025**:

- **Industries**: Information Technology, Semiconductors, Airlines, Finance, Real Estate, Consumer Goods  
- Each transcript corresponds to a single quarterly earnings call  
- EPS values were retrieved and compared to the previous quarter to generate a **binary label**:
  - `Label = 1`: EPS increased  
  - `Label = 0`: EPS stayed the same or decreased

---

## Preprocessing Steps

- **Text cleaning**: lowercasing, removal of URLs, emails, boilerplate financial text, currency, and numbers  
- **Custom stopword removal**: removed filler and domain-specific noise words (e.g., "gaap", "non-gaap", "fiscal", etc.)  
- **Lemmatization**: reduced words to their root form using NLTK  
- **Vectorization**: used **TF-IDF** (unigrams + bigrams) to capture important terms and phrases, limited to the **top 1,000 words**

---

## 🧠 Methodology

### Supervised Learning (EPS Prediction)

- **Feature Set**: Top 1000 TF-IDF features per transcript  
- **Label**: Binary EPS movement (0 = no increase, 1 = increase)  
- **Models Used**:
  - Logistic Regression  
  - Random Forest  
  - XGBoost  
  - Support Vector Machine (SVM)  
  - K-Nearest Neighbors (KNN)  
  - Feed Foward Neural Networks (NN)
- **Evaluation Metrics**:
  - Accuracy  
  - F1 Score  
  - AUC-ROC  
  - Confusion Matrix  
  - Stratified K-Fold Cross-Validation  

### Unsupervised Learning (Industry Clustering)

- **SVD**: Reduced high-dimensional TF-IDF vectors to 30–60 latent components  
- **PCA**: Applied on SVD output for further compression and visualization  
- **Clustering Methods**:
  - K-Means  
  - Agglomerative Hierarchical Clustering (Ward linkage)  
- **Validation**:
  - Compared clusters to known industries (post-hoc)  
  - Metrics: silhouette score, cluster purity, dendrograms, heatmaps  