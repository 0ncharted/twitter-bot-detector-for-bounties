
# Evaluation Results

## Metrics (Test Set)
| Metric     | Value | Notes                  |
|------------|-------|------------------------|
| Precision | 0.9 | Low false spam flags  |
| Recall    | 0.82 | Catches most Sybils   |
| F1-Score  | 0.86 | Balanced performance  |

## Key Insights
- Top feature: no_tweets (imp: 0.19) – High tweets = repetitive spam.
- Robust: 0.86 F1 on real Twitter data; generalizes to bounty farming (low followers = fake subs).

Full eval in eval_results.txt.
