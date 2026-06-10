# 📊 Task 5 – Exploratory Data Analysis (EDA) Using NumPy and Pandas

A hands-on EDA notebook analyzing the **Netflix Titles dataset** using NumPy and Pandas — covering data loading, cleaning, statistical analysis, filtering, and grouping.

---

## 📚 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Libraries Used](#libraries-used)
- [EDA Steps Performed](#eda-steps-performed)
- [NumPy Operations](#numpy-operations)
- [Pandas Operations](#pandas-operations)
- [Key Findings](#key-findings)
- [Prerequisites](#prerequisites)
- [How to Run](#how-to-run)

---

## Overview

This notebook is **Task 5** of a Python Data Analysis series. It introduces Exploratory Data Analysis (EDA) — the essential first step before any machine learning or data science project. The notebook uses the real-world **Netflix Titles dataset** from Kaggle to demonstrate practical data exploration techniques.

---

## Dataset

| Property | Details |
|----------|---------|
| **Name** | Netflix Titles |
| **Source** | [Kaggle – Netflix Movies and TV Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) |
| **File** | `netflix_titles.csv` |
| **Content** | Movies and TV shows available on Netflix |

### Key Columns

| Column | Description |
|--------|-------------|
| `type` | Movie or TV Show |
| `title` | Title of the content |
| `director` | Director name |
| `country` | Country of production |
| `release_year` | Year of release |
| `rating` | Content rating (PG, R, etc.) |
| `duration` | Duration in minutes or seasons |

---

## Libraries Used

```python
import numpy as np   # Numerical operations, array stats
import pandas as pd  # Data loading, cleaning, analysis
```

---

## EDA Steps Performed

| Step | Method | Purpose |
|------|--------|---------|
| Load Data | `pd.read_csv()` | Import the CSV dataset |
| Preview Data | `df.head()`, `df.tail()` | Inspect first/last rows |
| Dataset Shape | `df.shape` | Get rows × columns count |
| Column Names | `df.columns` | List all features |
| Data Types | `df.info()` | Check dtypes and null counts |
| Missing Values | `df.isnull().sum()` | Identify null entries per column |
| Statistical Summary | `df.describe(include="all")` | Min, max, mean, frequency stats |
| Correlation Matrix | `df.corr(numeric_only=True)` | Relationship between numeric columns |

---

## NumPy Operations

Applied on the `release_year` column converted to a NumPy array:

```python
years = df["release_year"].to_numpy()

np.mean(years)   # Average release year
np.max(years)    # Most recent release year
np.min(years)    # Oldest release year
np.std(years)    # Spread of release years
```

---

## Pandas Operations

```python
# Filter by content type
movies   = df[df["type"] == "Movie"]
tv_shows = df[df["type"] == "TV Show"]

# Count content types
df["type"].value_counts()

# Group by type and find average release year
df.groupby("type")["release_year"].mean()
```

---

## Key Findings

- The dataset contains both **Movies and TV Shows** — Movies make up the majority of Netflix content.
- Missing values were found in columns like `director`, `cast`, and `country`.
- NumPy stats on `release_year` reveal the recency of Netflix's content library.
- Grouping by `type` shows that Movies and TV Shows have different average release years.

---

## Prerequisites

- Python 3.x
- Jupyter Notebook or JupyterLab
- Required libraries:

```bash
pip install numpy pandas
```

- Download `netflix_titles.csv` from [Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows) and place it in the same directory as the notebook.

---

## How to Run

```bash
jupyter notebook "Task_5___Exploratory_Data_Analysis__EDA__Using_NumPy_and_Pandas.ipynb"
```

Or open in [Google Colab](https://colab.research.google.com/) by uploading both the `.ipynb` file and `netflix_titles.csv`.

---

## Author

**Aditya** — Python Data Analysis Series, Task 5
