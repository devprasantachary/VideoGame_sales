# VideoGame_sales
# I am Using PySpark, Mateplote.lib, Seaborn 


# 🎮 Video Games Sales & Profitability Analysis

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458.svg?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.12%2B-3776AB.svg)](https://seaborn.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7%2B-orange.svg)](https://matplotlib.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

An end-to-end Exploratory Data Analysis (EDA) and data cleaning pipeline for global and regional video game sales performance, profitability, platform popularity, and genre trends across multiple markets (2010–2017).

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Dataset Summary](#-dataset-summary)
- [Data Preprocessing & Cleaning](#-data-preprocessing--cleaning)
- [Key Insights & Visualizations](#-key-insights--visualizations)
  - [1. Regional & Country-Level Sales Breakdown](#1-regional--country-level-sales-breakdown)
  - [2. Genre Distribution & Sales Spread](#2-genre-distribution--sales-spread)
  - [3. National vs. Global Market Share](#3-national-vs-global-market-share)
  - [4. Longitudinal Sales Trends (2010–2017)](#4-longitudinal-sales-trends-20102017)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Tech Stack](#-tech-stack)
- [License](#-license)

---

## 📖 Project Overview

This repository contains a data analysis notebook investigating commercial video game sales across international regions. The objective is to understand how platform selection, genre preferences, geography, and publication timelines drive national and global revenue and profitability.

---

## 📊 Dataset Summary

The dataset comprises **5,893 records** across **15 attributes**, spanning video game releases from **2010 to 2017**:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Rank` | Integer | Overall sales ranking of the title |
| `Name` | String | Title of the video game |
| `Platform` | Category (26) | Gaming platform / console (e.g., Wii, NES, GBA, PSP, PS4, XOne) |
| `Year` | Numeric (2010–2017) | Release / recording year |
| `Month` | Category (14) | Month of commercial activity |
| `Genre` | Category (12) | Game genre (Sports, Platform, Action, Adventure, Fighting, etc.) |
| `Publisher` | Category (219) | Publishing studio (Nintendo, EA, Activision, etc.) |
| `Country` | Category (2) | Primary recording country (United States, Australia) |
| `City` / `State` / `Region` | Categorical | Geographic distribution fields |
| `National Sales` | Numeric ($M) | Revenue generated nationally (currency-cleaned & 95th percentile capped) |
| `Global Sales` | Numeric ($M) | Total worldwide sales revenue |
| `National Profit` | Numeric ($M) | Net profit recorded within the national market |
| `Global Profit` | Numeric ($M) | Net profit recorded globally |

---

## 🧹 Data Preprocessing & Cleaning

The raw data underwent systematic preprocessing to ensure statistical validity and visual clarity:

1. **Deduplication**: Removed duplicate records across all feature combinations.
2. **Missing Value Imputation**:
   - Imputed missing `Region` entries with default `"North"`.
   - Replaced missing `NA_Sales` values with the column mean.
3. **Format Normalization & Regex Sanitization**:
   - Stripped special currency characters (`$`) from sales figures using regex and cast to numeric floats.
   - Normalized country names (e.g., mapped `"USA"` to `"United States"` and applied title casing).
   - Standardized column names for consistency (`NA_Sales` $
ightarrow$ `National Sales`, `Global_Sales` $
ightarrow$ `Global Sales`, etc.).
4. **Outlier Treatment & Robust Capping**:
   - Applied right-tail 95th-percentile Winsorization/capping on `National Sales` (`quantile(0.95)`) to mitigate skewness from extreme blockbuster outliers without discarding valid observations.

---

## 📈 Key Insights & Visualizations

### 1. Regional & Country-Level Sales Breakdown
- **Grouped Bar Chart (`Seaborn`)**: Aggregated total National Sales segmented across regions (West, East, Central, South, North) and filtered by country.
- **Insight**: Highlights market concentration in specific regional hubs, revealing key target demographics for physical and digital distribution.

### 2. Genre Distribution & Sales Spread
- **Box Plot (`Seaborn`)**: Evaluates sales dispersion, median performance, interquartile range (IQR), and mean markers across all 12 genres.
- **Insight**: Identifies high-variance genres (such as Action and Sports) versus consistent baseline performers (like Platformers and Role-Playing games).

### 3. National vs. Global Market Share
- **Comparative Dual Pie Charts (`Matplotlib Subplots`)**: Visualizes the proportional contribution of the United States vs. Australia across domestic and global sales volumes.
- **Insight**: Demonstrates domestic revenue weight relative to total worldwide monetization.

### 4. Longitudinal Sales Trends (2010–2017)
- **Multi-Line Time Series (`Matplotlib`)**: Correlates the trajectory of National Sales against Global Sales over an 8-year timeline.
- **Insight**: Uncovers cyclical peaks coinciding with major eighth-generation console launches and transitionary sales shifts.

---

## 📁 Project Structure

```text
├── data/
│   └── VideoGamesSales.csv         # Raw dataset
├── notebooks/
│   └── Video_Game_Sales_EDA.ipynb   # Main Jupyter/Colab notebook
├── images/                         # Exported charts & visual assets
├── README.md                       # Project documentation
└── requirements.txt                # Python dependencies
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Jupyter Notebook or Google Colab

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/video-games-sales-analysis.git
   cd video-games-sales-analysis
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate       # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch the notebook:**
   ```bash
   jupyter notebook notebooks/Video_Game_Sales_EDA.ipynb
   ```

---

## 🛠 Tech Stack

- **Language:** Python
- **Data Manipulation:** `pandas`, `numpy`
- **Data Visualization:** `matplotlib`, `seaborn`
- **Environment:** Jupyter Notebook / Google Colab

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) - feel free to use and adapt this work for your own analyses.
