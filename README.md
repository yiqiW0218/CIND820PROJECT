# CIND820 Project: Recommendation System Analysis for Yelp
Yiqi WANG
# 1. Data Preprocessing and Exploration
> File Name: Data Preprocessing and Exploration.ipynb

## 1.1 Prepocessing Steps

(1) Extract Vancouver business information from *business* and match with *review* to get *vancouver_reviews*. 

(2) Filter out Vancouver restaurant reviews(2015 - 2019) to *v_reviews_filtered*. 

(3) Left join *v_reviews_filtered* and *vancouver_business*, which adds business information for each review record(2015 - 2019), to get *reviews_business*.

(4) Collect user id who has rated Vancouver restaurants in selected period(2015 - 2019) and match with user to get related users information *users_data*.

(5) Discard users with review counts over 57 and get *user_filtered*.

(6) Left join *reviews_business* and *user_filtered*, drop review record whose user id is not in the *user_filtered*, and get *reviews_business_users*.

> Dataset link: https://drive.google.com/drive/folders/1Um-d9gXQC41queTfM6Qbke1xytatpONG?usp=sharing

## 1.2 EDA and Visualization


# 2. Recommendation System Evaluation
> File Name: Recommendation Systems Evaluation.ipynb
