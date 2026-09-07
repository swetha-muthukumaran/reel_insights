# 🎬 Reel Insights
## An End-to-End Exploratory Data Analysis of the Global Movie Industry

> **A complete data analytics project using TMDB movie data to uncover insights across box-office performance, genres, ratings, talent, keywords, budgets, and movie release trends.**

**SQL • Python • Pandas • NumPy • Data Visualization • MySQL • Power BI**

---

## 📌 Project Overview

**Reel Insights** is an end-to-end data analytics project built using movie data from **The Movie Database (TMDB)**.

The project transforms raw relational datasets into meaningful business insights through:

**Data Cleaning → Relational Database → SQL Analysis → Pandas EDA → Data Visualization → Power BI**

The analysis focuses on understanding movie performance, financial trends, genre economics, audience ratings, actor and director productivity, keywords, and movie release patterns.

---

## 🎯 Business Objective

The objective of this project is to analyze historical movie data and answer questions such as:

- Which movies generate the highest revenue?
- Which genres have the strongest financial performance?
- Which actors and directors appear most frequently?
- What is the relationship between production budget and revenue?
- Which genres receive higher audience ratings?
- What keywords and themes appear most frequently?
- How has movie production changed over time?
- Which high-budget movies have relatively low revenue?

The analysis is designed to demonstrate how data can support **content strategy, financial evaluation, talent analysis, and entertainment industry decision-making**.

---

# 🗂️ Dataset

The project uses six relational datasets containing approximately **2,500 movies**.

| Dataset | Description |
|---|---|
| `movies.csv` | Movie details, release date, budget, revenue, popularity and ratings |
| `genres.csv` | Genre reference information |
| `movie_genres.csv` | Many-to-many relationship between movies and genres |
| `cast.csv` | Actors, characters and billing information |
| `crew.csv` | Directors and other crew information |
| `movie_keywords.csv` | Keywords and themes associated with movies |

### Dataset Source

The dataset was provided as part of the project and is based on **The Movie Database (TMDB)**.

---

# 🧹 Data Cleaning & Validation

The raw datasets were loaded and processed using **Python and Pandas**.

### Cleaning performed

- Inspected dataset dimensions and data types
- Checked missing values
- Removed exact duplicate records
- Validated primary and surrogate IDs
- Checked referential integrity
- Checked for orphan records
- Converted `release_date` to datetime
- Created `release_year`
- Validated numerical columns
- Investigated zero budget and revenue values

### Budget & Revenue Treatment

In TMDB data, `0` can represent an unknown or unavailable budget or revenue value.

Therefore, zero values were retained in the dataset and excluded from relevant financial calculations such as:

- Average budget
- Average revenue
- Profit
- ROI

This prevents unknown financial values from being interpreted as actual zero-dollar values.

---

## 📊 Final Dataset

After cleaning and validation:

| Table | Records |
|---|---:|
| Movies | **2,503** |
| Genres | **19** |
| Movie-Genres | **6,878** |
| Cast | **24,902** |
| Crew | **7,289** |
| Movie Keywords | **41,681** |

### Data Quality Results

| Validation | Result |
|---|---:|
| Exact duplicates | **0** |
| Missing values | **0** |
| Orphan records | **0** |
| Duplicate Movie IDs | **0** |
| Duplicate Genre IDs | **0** |
| Duplicate Cast Row IDs | **0** |
| Duplicate Crew Row IDs | **0** |
| Earliest Release Date | **1921-01-21** |
| Latest Release Date | **2026-06-10** |

---

# 🗄️ Relational Database

The cleaned datasets were structured into a relational SQL database.

### Database Structure

```text
                    ┌──────────────┐
                    │    movies    │
                    └──────┬───────┘
                           │
             ┌─────────────┴─────────────┐
             │                           │
      ┌──────▼───────┐             ┌─────▼─────┐
      │ movie_genres │             │    cast   │
      └──────┬───────┘             └───────────┘
             │
      ┌──────▼───────┐
      │    genres    │
      └──────────────┘

      movies ───────────── crew

      movies ───────────── movie_keywords