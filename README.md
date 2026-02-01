# Bassline.io — Song Popularity Prediction

## Project Overview
This project evaluates whether existing engineered audio features can effectively predict song popularity for a music streaming platform, **Bassline.io**.  
The objective is model evaluation and feature usefulness analysis — not production deployment.

---

## Business Context
The data science team at Bassline.io has previously engineered several audio-related features and wants to assess:

- Whether these features can predict song popularity
- Which features contribute most to prediction
- Whether further feature engineering is necessary

---

## Dataset
The dataset consists of song-level engineered audio features, including:

- Danceability  
- Energy  
- Acousticness  
- Other numerical audio characteristics  

The target variable is **song popularity**, represented as a continuous numerical score.

---

## Methodology
1. **Exploratory Data Analysis (EDA)**
   - Distribution analysis
   - Correlation analysis
   - Feature-to-target relationships

2. **Preprocessing**
   - Train/test split
   - Feature scaling
   - Multicollinearity assessment

3. **Modeling**
   - Linear Regression used as a baseline model
   - Model trained exclusively on engineered audio features

4. **Evaluation**
   - Mean Squared Error (MSE)
   - Train vs test performance comparison
   - Residual diagnostics

---

## Results & Key Insights
- The model shows limited but meaningful predictive capability.
- Features such as **energy** and **danceability** demonstrate stronger relationships with popularity.
- Similar train and test performance suggests acceptable generalization with noted limitations.

---

## Repository Structure
- `notebook.ipynb` — Full analysis, modeling, and evaluation
- `data.csv` — Dataset used for training and testing
- `model.pkl` — Serialized trained regression model

---

## Limitations
- Popularity is influenced by many external factors not captured in the dataset.
- Linear regression assumptions may oversimplify complex listener behavior.
- Feature set is limited to pre-engineered variables.

---

## Future Improvements
- Introduce non-linear models (Random Forest, Gradient Boosting)
- Expand feature engineering
- Explore genre-specific or temporal effects

---

## Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib / Seaborn
- Jupyter Notebook
