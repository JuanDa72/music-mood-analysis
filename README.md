# Music Mood Analysis

This repository contains an exploratory analysis of Spotify track features to study how musical attributes relate to perceived mood.

## Dataset

* **Location:** `data/spotify_tracks.csv`
* **Description:** A cleaned extract of Spotify track-level features (see `notebooks/exploration.ipynb` for details).

## Key Columns

* `mode` — Musical mode of the track: `1` = Major (often perceived as happier), `0` = Minor (often perceived as sadder).
* `valence` — A measure of musical positiveness (range 0.0–1.0). Higher values indicate a more positive, happy mood.
* `tempo` — Speed in beats per minute (BPM).
* `energy` — Perceptual energy of the track (0.0 = calm/soft, 1.0 = very energetic/loud).
* `loudness` — Overall loudness in decibels (dB).
* `key` — Estimated musical key (0 = C, 1 = C♯/D♭, ... 11 = B). A value of `-1` means unknown or not detected.

## Phase 1 — Statistical Study

* **Mode vs. Valence (Two-sample t-test):** Do songs in major mode (`mode=1`) have significantly higher `valence` than songs in minor mode (`mode=0`)Key columns?
* **Tempo vs. Energy (Pearson correlation):** How strongly are tempo and energy correlated?
* **Loudness vs. Energy (Correlation):** Expect a high correlation; useful to verify and discuss.
* **Key vs. Valence (One-way ANOVA):** Are some keys associated with higher mean `valence`?

## Phase 2 — Mood Modeling (ML)

### 2a. Clustering (Unsupervised) — Discovering Natural Mood Groups

* **Features:** `valence` and `energy` (the classic circumplex model of musical emotion).
* Scale features (`StandardScaler`) before clustering.
* Determine optimal number of clusters via the elbow method.
* Run K-Means and visualize clusters (valence vs. energy scatter plot, colored by cluster).
* Interpret and label each cluster (e.g., "happy-energetic", "sad-calm", "aggressive", "chill").

### 2b. Classification (Supervised) — Predicting Mood for New Songs

* Use cluster labels from 2a as the target variable (`mood_label`).
* Perform train/test split.
* **Baseline model:** Logistic Regression.
* Compare against Random Forest.
* Evaluate with accuracy, confusion matrix, and F1-score (per class, due to potential imbalance).

## How to Use

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt