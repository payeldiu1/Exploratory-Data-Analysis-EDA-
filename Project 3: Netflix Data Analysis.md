# 📺 Netflix Content Analysis with Python

## Business Problem

Netflix has a vast and continuously growing content library. To make informed decisions about content acquisition, production, and regional expansion, Netflix needs to understand trends within its catalog. This analysis explores the dataset to identify patterns in content type, country of origin, genres, ratings, and growth over time.

---

# Business Questions

This project aims to answer the following business questions:

1. Which countries produce the most Netflix content?
2. What is the ratio of Movies vs. TV Shows?
3. Which genres are the most popular?
4. Which years had the highest number of content additions?
5. How has Netflix's content library evolved over time?
6. Which content ratings are the most common?
7. Which directors have produced the highest number of Movies and TV Shows?

---

# Dataset

**Source:** Kaggle – Netflix Movies and TV Shows

https://www.kaggle.com/datasets/shivamb/netflix-shows

**Dataset Includes**

* Show ID
* Content Type (Movie / TV Show)
* Title
* Director
* Cast
* Country
* Date Added
* Release Year
* Rating
* Duration
* Genre (Listed In)
* Description

---

# Data Cleaning

The following preprocessing steps were performed before analysis:

* Removed duplicate records
* Handled missing values
* Converted `date_added` to datetime format
* Extracted:
  * Added Year
* Split multiple countries into separate values where necessary
* Standardized text formatting
* Removed unnecessary whitespace

---

# Exploratory Data Analysis (EDA)

The analysis includes:

* Distribution of Movies vs TV Shows
* Top content-producing countries
* Most common content ratings
* Most popular genres
* Number of titles added by year
* Content growth over time
* Top directors
* Duration analysis
* Release year distribution

#What is the ratio of Movies vs TV Shows?

sns.countplot(data=df, x="type")

<img width="580" height="432" alt="image" src="https://github.com/user-attachments/assets/79485fec-c6a8-45e0-9266-8aa2a436778a" />


# Business Insights

## 1. Movies dominate the Netflix catalog

Movies make up most of Netflix's catalog while maintaining a smaller collection of TV Shows.

---

## 2. The United States contributes the largest share of content

The United States is by far the largest contributor to Netflix's catalog, followed by countries such as India, the United Kingdom, Canada, and Japan.

**Business Value**

* Strong dependence on U.S. productions
* Opportunity to further expand regional content

---

## 3. TV-MA is the most common content rating

Most Netflix titles are rated **TV-MA**, suggesting that Netflix primarily targets mature audiences.

**Business Value**

* Adult-oriented content dominates the platform
* Useful for audience segmentation and recommendation systems

---

## 4. Netflix rapidly expanded between 2018 and 2020

The number of titles added increased dramatically during 2018–2020, representing Netflix's fastest period of catalog growth.

**Business Value**

* Aggressive investment in content acquisition
* Significant increase in platform diversity

---

## 5. Drama and International Movies are the most popular genres

Drama and International Movies appear most frequently within the catalog.

Other highly represented genres include:

* Comedies
* Documentaries
* Action & Adventure
* Independent Movies

**Business Value**

* Viewers have strong demand for dramatic and international content. also they are interested in Stand-Up Comedy
* These genres should remain key investment areas

---

## 6. Raúl Campos and Jan Suter have directed the highest number of Netflix titles

Among listed directors, **Raúl Campos**  have the highest number of Movies and TV Shows available on Netflix.

---

# Conclusion

The analysis reveals several important trends in Netflix's content strategy:

* Movies significantly outnumber TV Shows.
* The United States remains the primary source of content.
* TV-MA is the dominant content rating.
* Netflix experienced rapid catalog expansion between 2018 and 2020.
* Drama and International Movies are the most common genres.
* Raúl Campos and Jan Suter are among the platform's most prolific directors.

These insights can help support future decisions regarding content acquisition, production planning, market expansion, and personalized recommendations.

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* colab Notebook

  Script: https://colab.research.google.com/drive/19x0GTHTSOpDB6Z9JjS43stXEclfKfu9g#scrollTo=3hemghxV9irV

---

# Author

**Mohammad Mijanur Rahman**

Data Analytics | Python | SQL | Machine Learning | Data Visualization
