# Bassline.io — Song Popularity Prediction

Can audio features predict how popular a song will be on streaming platforms? This project investigates that question — and the answer is more interesting than a simple yes or no.

---

## Project Goal

Assess whether engineered audio features (danceability, energy, acousticness) carry meaningful predictive signal for song popularity, and identify where that signal breaks down.

---

## Dataset

- **18,835 tracks** after cleaning (20.76% duplicates removed)
- 14 features including danceability, energy, acousticness, instrumentalness, liveness, tempo, and more
- Target variable: `song_popularity` (0–100 scale)
- Mean popularity: 52.99 | Median: 56.0

---

## Methodology

### Why Ridge Regression

The three primary features — danceability, energy, and acousticness — are correlated with each other. Energy and acousticness alone have a correlation of **−0.66**. Standard linear regression inflates and destabilises coefficients under multicollinearity. Ridge regression penalises large coefficients, producing stable, interpretable estimates. The goal was not to maximise predictive accuracy but to understand which features matter and in what direction — Ridge is the right tool for that question.

### Process

- Exploratory data analysis and correlation analysis
- Feature preprocessing with StandardScaler
- Linear regression as baseline
- Ridge regression with 5-fold cross-validated GridSearchCV over alpha ∈ {0.01, 0.1, 1, 10, 100}
- Best alpha: **100**
- Model evaluation: MSE, residual analysis, coefficient interpretation

---

## Results

| | MSE |
|---|---|
| Train | 472.04 |
| Test | 474.57 |

Train and test MSE are nearly identical — minimal overfitting. The model generalises well.

**Feature coefficients (Ridge, α=100):**

| Feature | Coefficient |
|---|---|
| Danceability | +2.04 |
| Acousticness | −1.78 |
| Energy | −1.24 |

Danceability is the strongest positive predictor. Acousticness has a negative relationship with popularity — acoustic tracks consistently underperform across genres.

---

## Key Finding

The model is well-behaved but the predictive ceiling is low. An RMSE of ~21.8 points on a 0–100 scale reflects real but limited signal from audio features alone.

**This is itself the finding.** Song popularity on streaming platforms is driven primarily by factors outside the audio itself — artist following, label backing, playlist placement, marketing spend, and social momentum. Audio features capture what a song *is*. They cannot capture what happens *around* it.

Knowing where a model's predictive power ends is as valuable as the model itself.

---

## Limitations

- Only three audio features used as primary predictors
- No external drivers included (artist popularity, release timing, platform promotion)
- Linear model assumptions may not capture non-linear relationships

---

## Future Improvements

- Incorporate external features: artist follower count, release date, label size
- Test non-linear models: Random Forest, XGBoost
- Genre and temporal segmentation — popularity dynamics differ significantly across genres and time periods
- Confidence interval visualisation on predictions

---

## Stack

Python · pandas · scikit-learn · Ridge Regression · GridSearchCV · Matplotlib · Seaborn
