# Project 3: APIs, NLP, and Classification

## Table of Content
[1. Executive Summary](#Executive-Summary) <br>
[2. Data Dictionary](#Data-Dictionary) <br>
[3. Repository Structure](#Repository-Structure) <br>
[4. File Description](#File-Description)

## Executive Summary

**Coursera** and **EdX** are the giants among MOOC(Massive Open Online Course) platforms, combining to over 100+ million users. As product owner of coursera, the goal of this project is to use machine learning classification model to classify posts from two subreddits - **Coursera & EdX**. Classifying and separating the two subreddits is a quick way to gauge strengths and weakness compared to the competitor.

The steps of each project are as follows:
1. Data Acquisition - Reddit API to extract dat to csv
2. Data Exploratory - EDA on title and comment to find key differences
3. Model Comparison - Compare optimized machine learning models
4. Final Model & Evaluation - Select the model most suitable for production and evaluate the performance

After we've acquired out data, we proceeded to the next step of the project which is the EDA. For EDA I've decided to use **Tf-Idf Vectorize** and **Lemmatized** title, as this will be easier to interpret. The findings from this EDA shows that **Coursera** and **EdX** are similar in areas such as free courses, data related courses, and certificates. Some area of differences seem to be types of courses and pace of courses.

Then we tried 9 models to fit on our **title**, for each model the choices of **Normalization**, **Vectorization**, and **Simplification** are adjusted based on the performane of each model. Each model was then compared using metrices such as the accuracy, recall, and f1-score. The top two performing models are **Tf-Idf Vectorizer + Logistic Regression** and **Count Vectorizer + Multinomial Naive Bayes Classifier**.

The final model that we've selected is the **Tf-Idf Vectorizer + Logistic Regression** due to the similarity in performance, while being less prone to overfitting which will be beneficial in the long run. Additionally, **Logistic Regression** are generally easier to evaluate and explain.

With the final model we explore deeply into where the model went right and wrong. This tells us the differences and similarities between the two subreddits - two MOOC platforms. Which can then be used to identify areas that are current good and areas that needs improvement as follows:

**Coursera:** <br>

Currently doing well:
- Business oriented courses in partnership with Google/IBM
- Professional certificate
- Financial aid
- Self-paced courses with no waiting time

Areas to improve:
- Improve customer support experience
- Improve log-in button and chat bubble
- Keeps improving financial aid as it's one of the most discussed topic

**EdX:** <br>

Currently doing well:
- University-based courses such as *Introduction to Computer Science* by Harvard
- MicroMaster programs
- Audit courses
- Some self-paced courses

Areas to improve:
- More verified certificate
- More self-paced courses
- Keep up with free audit courses

---

## Data Dictionary

### Post DataFrame
|column|explanation|type|
|---|---|---|
|name|reddit's naming code of the thread|str|
|title|title of the thread|str|
|selftext|description inside the thread|str|
|ups|no. of upvotes|int|
|upvote_ratio|% of votes being upvotes|float|
|permalink|link to the comment section|str|
|subreddit|cousera or edx|str|
|title_length|length of the title in characters|int|
|title_count|length of the title in word couts|int|
|title_lemma|lemmatized title|str|
|title_stem|stemmed title|str|

### Comments DataFrame
|column|explanation|type|
|---|---|---|
|name|reddit's naming code of the thread|str|
|subreddit|cousera or edx|str|
|title|the comment|str|
|title_length|length of the title in characters|int|
|title_count|length of the title in word couts|int|
|title_lemma|lemmatized comments|str|
|title_stem|stemmed comments|str|

---

## Repository Structure 
```
dsi_project_nlp
|
|__ code
|   |__ 01_API_Web_Scraping.ipynb   
|   |__ 02_EDA.ipynb   
|   |__ 03_Model_Comparison.ipynb
|   |__ 04_Final_Model_Evaluation.ipynb  
|  
|__ datasets
|   |__ coursera_edx_posts_f.csv
|   |__ coursera_edx_posts_cleaned.csv
|   |__ coursera_edx_comments_f.csv
|   |__ coursera_edx_comments_cleaned.csv
|
|__ model
|   |__ lr_model.pkl
|
|__ README.md

```
<br>

---

## File Description
<br>

    01_API_Web_Scraping.ipynb
- Using Reddit.com API to scrape data from *Coursera* and *EdX* subreddit

<br>

    02_EDA.ipynb
- Exploratory Data Analysis to understand differences in recurring words

<br>

    03_Model_Comparison.ipynb

- Comparing different models and optimizing them to find production model

<br>

    04_Final_Model_Evaluation.ipynb
- Using final model to evaluation correct classification and misclassification