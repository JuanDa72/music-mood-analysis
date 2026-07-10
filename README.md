# Music Mood Analysis

This repository contains an exploratory analysis of Spotify track features to study how musical attributes relate to perceived mood.

Dataset
-
- Location: `data/spotify_tracks.csv`
- A cleaned extract of Spotify track-level features (see the `notebooks/exploration.ipynb` for details).

Key columns
-
- `mode` — Musical mode of the track: `1` = Major (often perceived as happier), `0` = Minor (often perceived as sadder).
- `valence` — A measure of musical positiveness (range 0.0–1.0). Higher values indicate a more positive, happy mood.
- `tempo` — Speed in beats per minute (BPM).
- `energy` — Perceptual energy of the track (0.0 = calm/soft, 1.0 = very energetic/loud).
- `loudness` — Overall loudness in decibels (dB).
- `key` — Estimated musical key (0=C, 1=C♯/D♭, ... 11=B). A value of `-1` means unknown or not detected.

Phase 1 — Statistical study
-
- Mode vs. Valence: two-sample t-test — Do songs in major mode (`mode=1`) have significantly higher `valence` than songs in minor mode (`mode=0`)?
- Tempo vs. Energy: Pearson correlation — How strongly are tempo and energy correlated?
- Loudness vs. Energy: correlation — Expect a high correlation; useful to verify and discuss.
- Key vs. Valence: one-way ANOVA — Are some keys associated with higher mean `valence`?

How to use
-
- Install dependencies: `pip install -r requirements.txt`.
- Open and run the exploratory notebook: `notebooks/exploration.ipynb` (recommended to use Jupyter or JupyterLab).
- Quick checks from the command line:

```bash
python -c "import pandas as pd; print(pd.read_csv('data/spotify_tracks.csv').shape)"
```

Next steps
-
- Extend the analysis with clustering or classification models to predict mood.
