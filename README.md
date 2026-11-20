# BUS 3392A Group Project: Steam Data Exploration and Transformation

**Team:** Josh Baron and Juan

## Goal
Analyze the Steam `steam_games.csv` dataset from Kaggle in Google Colab to explore,
clean, summarize, and transform game data, then present the findings in a one-page report.

## Research questions
1. **Popularity**: which metrics define it (ownership, reviews, playtime, recommendations),
   does free vs. paid matter, and which games are most popular? (Josh)
2. **Genres and categories**: summary statistics by genre, category, and selected combos. (Juan)
3. **Older vs. newer games**: do review patterns differ by release year or month? (Juan)
4. **Correlation**: do reviews, recommendations, playtime, and ownership agree? (Josh)

## Files
| File | Owner | Purpose |
| --- | --- | --- |
| `01_data_prep.ipynb` | Josh | Read the CSV, clean it, and parse genres/categories into lists |
| `02_q1_q4_metrics.ipynb` | Josh | Q1 and Q4 |
| `03_q2_q3_groups.ipynb` | Juan | Q2 and Q3 |
| `charts/` | Both | Saved chart images for the report |
| `report/one_pager.pdf` | Both | Final one-page summary |

## Data
- Source: `steam_games.csv` from Kaggle (link on Canvas).
- Download date: **November 20, 2026**. Both teammates use this same copy so results match.
- The file is about 1.1 GB, which is over GitHub's 100 MB limit, so it is **not** stored in this repo.
  It lives in our shared Google Drive folder. Point the notebooks at that path before running.

## Branches
- `main`: approved, merged work only
- `josh`: Josh's work
- `juan`: Juan's work

Work on your own branch, open a pull request, have your teammate review the diff, then merge into `main`.

## How to run
1. Open the notebook in Google Colab.
2. Mount Google Drive and set the path to `steam_games.csv`.
3. Optional: Edit > Notebook settings > choose a GPU/TPU for faster processing.
4. Run `01_data_prep.ipynb` first, then `02` and `03`.
