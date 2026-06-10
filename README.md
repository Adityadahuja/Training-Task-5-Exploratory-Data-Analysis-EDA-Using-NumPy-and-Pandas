# 📊 Task 5 – Exploratory Data Analysis (EDA) Using NumPy and Pandas

A comprehensive EDA notebook on the **Netflix Titles dataset** — covering statistical analysis, univariate & bivariate visualizations, and outlier detection using the IQR method.

---

## 📚 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Libraries Used](#libraries-used)
- [EDA Workflow](#eda-workflow)
- [Visualizations](#visualizations)
- [Outlier Detection](#outlier-detection)
- [Key Insights](#key-insights)
- [Prerequisites](#prerequisites)
- [How to Run](#how-to-run)

---

## Overview

This notebook performs end-to-end Exploratory Data Analysis (EDA) on the real-world **Netflix Titles dataset** from Kaggle. It goes beyond basic data inspection to include statistical analysis with NumPy, multiple chart types with Matplotlib and Seaborn, and outlier detection using the IQR method.

---

## Dataset

| Property | Details |
|----------|---------|
| **Name** | Netflix Titles |
| **Source** | [Kaggle – Netflix Movies and TV Shows](https://www.kaggle.com/datasets/shivamb/netflix-shows) |
| **File** | `netflix_titles.csv` |
| **Content** | Movies and TV Shows available on Netflix globally |

### Key Columns

| Column | Description |
|--------|-------------|
| `type` | Movie or TV Show |
| `title` | Title of the content |
| `director` | Director name |
| `country` | Country of production |
| `release_year` | Year of release |
| `rating` | Content rating (PG, R, TV-MA, etc.) |
| `duration` | Runtime (minutes for movies, seasons for TV shows) |

---

## Libraries Used

```python
import pandas as pd          # Data loading, cleaning, analysis
import numpy as np           # Numerical stats on arrays
import matplotlib.pyplot as plt  # Plotting charts
import seaborn as sns        # Statistical visualizations
```

---

## EDA Workflow

| Step | Method | Purpose |
|------|--------|---------|
| Load Data | `pd.read_csv()` | Import the dataset |
| Preview | `df.head()`, `df.tail()`, `df.sample(5)` | Inspect rows |
| Shape & Columns | `df.shape`, `df.columns` | Dataset dimensions |
| Data Types | `df.info()` | Dtypes and null counts |
| Missing Values | `df.isnull().sum()` | Null entries per column |
| Statistical Summary | `df.describe()` | Min, max, mean, std |
| NumPy Stats | `np.mean()`, `np.median()`, `np.std()` | Deeper numeric analysis |
| Skewness | `df['release_year'].skew()` | Distribution symmetry check |
| Filtering | Boolean indexing | Separate Movies vs TV Shows |
| Grouping | `df.groupby()` | Aggregate stats by category |
| Correlation | `df.corr(numeric_only=True)` | Numeric feature relationships |

---

## Visualizations

| Chart | Library | Insight |
|-------|---------|---------|
| Pie Chart | Matplotlib | Movies vs TV Shows distribution |
| Histogram | Matplotlib | Release year distribution |
| Bar Chart | Matplotlib | Top content ratings |
| Bar Chart | Matplotlib | Top 10 producing countries |
| Boxplot | Seaborn | Release year spread and outliers |
| Count Plot | Seaborn | Content count by type |
| Boxplot (bivariate) | Seaborn | Release year by content type |
| Count Plot (hue) | Seaborn | Ratings breakdown by content type |

---

## Outlier Detection

Outliers in `release_year` are identified using the **IQR Method**:

```python
Q1 = df['release_year'].quantile(0.25)
Q3 = df['release_year'].quantile(0.75)
IQR = Q3 - Q1

lower_limit = Q1 - (1.5 * IQR)
upper_limit = Q3 + (1.5 * IQR)

outliers = df[
    (df['release_year'] < lower_limit) |
    (df['release_year'] > upper_limit)
]
```

---

## Key Insights

- **Movies dominate** Netflix's catalogue compared to TV Shows.
- **Release years are left-skewed** — most content is recent, with a few older titles pulling the distribution.
- **TV-MA and TV-14** are the most common content ratings.
- **United States** is the top content-producing country by a large margin.
- Bivariate analysis shows **TV Shows tend to have a slightly higher average release year** than Movies.

---

## Prerequisites

- Python 3.x
- Jupyter Notebook or JupyterLab
- Required libraries:

```bash
pip install numpy pandas matplotlib seaborn
```

- Download `netflix_titles.csv` from [Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows) and place it in the same folder as the notebook.

---

## How to Run

```bash
jupyter notebook "Task_5___EDA_Using_NumPy_and_Pandas.ipynb"
```

Or open in [Google Colab](https://colab.research.google.com/) by uploading both the `.ipynb` file and `netflix_titles.csv`.

---

## Author

**Aditya** — Python Data Analysis Series, Task 5 (Revised)
