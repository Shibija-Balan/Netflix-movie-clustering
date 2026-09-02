# Netflix Movie Clustering

An exploratory clustering project examining how Netflix movies group by duration, content classification and primary genre.

## Dataset

Source: Netflix Titles Dataset on Kaggle (`shivamb/netflix-shows`). The analysis focuses on movies rather than TV shows and uses:

- `duration` — movie length in minutes
- `rating` — Netflix content classification such as PG, R or TV-MA
- `listed_in` — genre/category information

## Workflow

1. Filter the dataset to movies and clean duration values.
2. Extract a primary genre from the category field.
3. Encode categorical features and standardise the feature matrix.
4. Apply K-Means clustering with five clusters.
5. Visualise and summarise the resulting groups.

## Important methodological limitation

The original notebook uses integer label encoding for nominal variables such as content classification and genre before applying K-Means. This is a useful early clustering exercise, but it imposes an artificial numeric ordering and distance structure on categories that do not naturally have one. For example, an encoded value of 7 is not inherently "more" genre or a "better" rating than a value of 3.

Because K-Means relies on Euclidean distance, the categorical treatment limits how strongly the resulting clusters should be interpreted. A stronger follow-up would use one-hot encoding where appropriate or a mixed-data clustering method such as k-prototypes or Gower-distance-based clustering.

Also, the Netflix `rating` field is a **content classification**, not an audience review score. Cluster summaries should therefore be interpreted as differences in content classifications rather than differences in audience approval.

## Repository structure

- `netflix_clustering.ipynb` — exploratory notebook
- `data/` — dataset location
- `images/` — generated visualisations
- `requirements.txt` — Python dependencies

## Tools

Python, pandas, NumPy, matplotlib, seaborn, scikit-learn

## Next improvements

- Replace ordinal label encoding of nominal categories with an appropriate categorical representation.
- Compare several cluster counts using diagnostics such as silhouette score.
- Test cluster stability under alternative preprocessing choices.
- Produce cluster profiles based on interpretable original features.

This repository is retained as an early unsupervised-learning project, with its methodological limitations documented explicitly rather than disguised by prettier charts. Science survives embarrassment; portfolios should too.
