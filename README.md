# La Liga Match Outcome Predictor

Predicts Home win / Draw / Away win for La Liga matches using
Elo ratings and recent form, built around El Clásico (Oct 25, 2026).

## Data
football-data.co.uk, La Liga 2019-20 to 2026-27 (~2,750 matches).

## Features
- **Elo rating difference** (K=20, home advantage = 60), computed
  match by match with no future data leakage
- **Recent form**: avg points per game over the last 5 matches

## Method
Multinomial logistic regression. Time-based split: train on 2020-21
to 2024-25, test on 2025-26 + 2026-27. 2019-20 is an Elo warm-up.

## Results (469 test matches)
| Model | Accuracy | Log loss |
|---|---|---|
| Always home | 48.0% | – |
| This model | 51.4% | 0.975 |
| Bet365 implied | 54.6% | 0.957 |

The model almost never predicts draws (3/469). Draws are common
(~25%) but rarely the single most likely outcome.

## El Clásico prediction (made Oct 24, 2026, before kickoff)
Barcelona 55.4% · Draw 18.7% · Real Madrid 25.9%

**Result:** _to be added_

## Next steps
- Add goal and shot-based features
- Tune K and home advantage
- Compare against a random forest
