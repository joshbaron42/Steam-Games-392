# BUS 3392A Group Project: Steam Data Exploration and Transformation

**Team:** Josh Baron and Juan Haro

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
| `BUS392SteamClean.ipynb` | Josh | Downloads the raw data, checks data quality, cleans it, and saves `steam_clean.csv` |
| `steam_clean.csv` | Josh | The cleaned dataset that both analysis notebooks start from |
| Q1/Q4 notebook | Josh | Popularity and correlation (to be added) |
| Q2/Q3 notebook | Juan | Genres/categories and older vs. newer games (to be added) |
| `charts/` | Both | Saved chart images for the report |
| `report/one_pager.pdf` | Both | Final one-page summary |

## Data
- **Source:** `steam_games.csv` from the Steam Games dataset on Kaggle (link on Canvas).
- **Version:** the dataset is updated daily, so we pinned **version 114** to make sure we both use identical data:
  `kagglehub.dataset_download("hubertsidorowicz/steam-games-dataset-daily-updates/versions/114")`
- **Raw file:** about 1.1 GB, over GitHub's 100 MB limit, so it is **not** stored in this repo.
- **Cleaned file:** `steam_clean.csv` (about 48 MB) **is** stored in this repo, on the `cleaned-data` branch.

### What the cleaning notebook does
1. Loads the 12 variables the assignment requires (150,643 games).
2. Checks data quality: blanks, duplicate `app_id`s, and games with an empty genre or category list (`"[]"`).
3. Removes games missing a `name` or `release_date` (150,559 games left).
4. Keeps games missing `price`, `recommendations`, or genres/categories; each analysis excludes them only where needed.
5. Converts `release_date` to real dates and adds `release_year` and `release_month`.
6. Unifies the two `estimated_owners` formats (`"20,000 .. 50,000"` becomes `"20000 - 50000"`).
7. Adds `owners_midpoint`, the middle of each owners range (`"0 - 0"` is left blank).

`genres` and `categories` are kept as text. To check whether a game has a genre, include the quotes,
for example `'"Action"' in genres_text`, so that `"Co-op"` doesn't also match `"Online Co-op"`.

## Branches
- `main`: approved, merged work only
- `cleaned-data`: the cleaning notebook and `steam_clean.csv`, shared by both of us
- `josh`: Josh's work
- `juan`: Juan's work

Work on your own branch, open a pull request, have your teammate review the diff, then merge into `main`.

## How to run the analysis notebooks
1. On GitHub, switch to the `cleaned-data` branch, open `steam_clean.csv`, and download it.
2. Open your notebook in Google Colab and upload `steam_clean.csv` using the folder icon on the left.
   Colab deletes uploaded files when the session ends, so re-upload it each new session.
3. Load the data:
   ```python
   import pandas as pd
   gamesData = pd.read_csv("steam_clean.csv", parse_dates=["release_date"])
   ```
   `parse_dates` turns `release_date` back into real dates, since CSV files store everything as text.

To rerun the cleaning from scratch, open `BUS392SteamClean.ipynb` and run all cells. It downloads
version 114 from Kaggle with `kagglehub`, so no upload is needed.
