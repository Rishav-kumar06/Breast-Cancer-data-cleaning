# Data Cleaning — Raw Movies Dataset (Python & Pandas)

Cleaning a genuinely messy real-world dataset: movie metadata, box-office numbers and IMDB / Rotten Tomatoes ratings from the [vega-datasets](https://github.com/vega/vega-datasets) project (3,201 rows × 16 columns).

## Problems found in the raw data
- 9,205 missing values across 13 columns (up to 82% missing in a column)
- 22 release dates in the future (up to 2046) — wrong century
- Gross = 0 used to mean "not recorded"
- Numeric film titles (e.g. *1776*, *300*) stored as integers
- Inconsistent rating label (`Open`) and heavy right-skew / extreme values

## What the notebook does
1. Quality assessment (missing, duplicates, invalid values, mixed types)
2. Duplicates — checked exact and by title/date (repeated titles are remakes, kept)
3. Format and invalid-value fixes (dates, zero grosses, text types)
4. Missing values — a justified strategy per column (drop row / drop column / median / constant `Unknown`)
5. Outliers — IQR, z-score and box plots, with a keep/fix decision for each column
6. Encoding — ordinal (MPAA rating), one-hot (genre, creative type, source), frequency (distributor), date parts
7. Before/after comparison of shape, missing values and summary statistics

## Result
| | Before | After |
|---|---|---|
| Rows | 3,201 | 3,145 |
| Missing values | 9,205 | 0 |
| Duplicate rows | 0 | 0 |
| Max release year | 2046 | 2010 |

## Files
- `Data_Cleaning_Movies.ipynb` — full notebook with reasoning in markdown cells
- `movies.json` — raw data
- `movies_clean.csv` — cleaned data (readable categories)
- `movies_encoded.csv` — fully numeric, model-ready data

## Run it
```bash
pip install pandas numpy matplotlib seaborn jupyter
jupyter notebook Data_Cleaning_Movies.ipynb
```
