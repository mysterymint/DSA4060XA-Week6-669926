# DSA4060XA-Week6-669926

* Student Name: EMMANUEL MUONDO
* Student ID: 669926

## Lab Objective
To evaluate recommender systems against a reasonable baseline using metrics matching actual recommendation objectives, ensuring that a model is judged not merely on its ability to produce recommendations, but on its prediction error, ranking quality, coverage, novelty, and diversity.

## Models Compared
1. **Popularity Baseline:** Predicts movies using training averages/global means and ranks items by average rating and rating count.
2. **Content-Based Filtering:** Converts genres into binary features, builds user preference profiles weighted by past ratings, and scores items via cosine similarity.
3. **Item-Based Collaborative Filtering:** Computes item-item similarity matrices from user interaction patterns to produce similarity-weighted rating predictions and rankings.

## Best Model for Rating Prediction
* **Item-Based Collaborative Filtering** achieved the lowest rating prediction errors with an **MAE of 0.924** and an **RMSE of 1.070**, outperforming both the Popularity Baseline ($\text{MAE} = 1.086$) and Content-Based Filtering ($\text{MAE} = 1.094$)].

## Best Model for Ranking
* **Content-Based Filtering** (alongside Popularity Baseline) achieved stronger Top-3 ranking metrics with an **NDCG@3 of 0.2** (compared to Item-Based CF's $0.0$), demonstrating a superior ability to place relevant items near the top of recommendation lists.

## Coverage, Novelty, and Diversity Findings
| Model | Catalogue Coverage | Novelty | Diversity |
| :--- | :--- | :--- | :--- |
| **Popularity Baseline** | 0.35 | 1.689 | 0.736 |
| **Content-Based** | 0.70 | 1.344 | 0.542 |
| **Item-Based CF** | **0.85** | **1.695** | **0.780** |

* **Catalogue Coverage:** Item-Based CF exposed the widest portion of the item catalogue ($85\%$), whereas the Popularity Baseline restricted recommendations to only $35\%$ of the movies.
* **Novelty:** Item-Based CF and the Popularity baseline surfaced less predictable, more niche items compared to the content-based approach.
* **Diversity:** Item-Based CF yielded the most diverse internal recommendation lists (genre dissimilarity score of $0.780$).

## Final Recommended Model
* **Content-Based Filtering** is recommended for scenarios prioritizing user discovery and catalog exploration without allowing mainstream titles to dominate every list. It balances genre alignment, novelty, and catalog coverage.

## At Least Three Limitations
1. **Extremely Small Dataset:** The dataset contains only 12 users and 20 movies (120 total interactions), leading to high sparsity and variance in collaborative filtering neighborhood calculations.
2. **Cold-Start Vulnerability:** New users or items with zero historical interaction cannot be reliably profiled or matched using collaborative or profile-matching techniques.
3. **Simplistic Feature Representation:** Genre metadata was mapped using basic binary one-hot encoding without capturing deeper semantic nuances, user intent, or temporal rating shifts.
