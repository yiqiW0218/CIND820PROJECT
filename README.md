# CIND820 Project: Recommendation System Analysis for Yelp
Yiqi WANG

This project uses Yelp dataset and aims to provide the most precise recommendation of Vancouver’s restaurant to the consumers. It will conduct research from the following four aspects:

> 1.The performance of collaborative filtering on the selected database;
> 
> 2.The performance of content-based filtering on the selected database;
> 
> 3.The performance of weighted hybrid filtering (collaborative filtering and content-based filtering) on the selected database;
> 
> 4.Performance comparison and obtain the highest prediction accuracy model.

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

Spearman’s Correlation between Review Ratings and Three Variables

Spearman’s Correlation between Business Stars and Business Review Counts

Numbers of Reviews in each Rating Group

Numbers of Restaurants in each Rating Group

Average Rating Stars and Review Counts per Business(Restaurant)/User

# 2. Recommendation System Evaluation
> File Name: Recommendation Systems Evaluation.ipynb

## 2.1 Collaborative Filtering Model

I use Python library Surprise (SVD, SVDpp, KNNBasic) to find the best collaborative filtering model based on RMSE, MAE, and Fit time.

## 2.2 Content-based Filtering Model

### 2.2.1 Data Implement

1. The data type of attributes column is the dictionary, and its values have three types which are True/False/None, text, and sub-dictionary(with values of True/False/None). Classify the key value by its value type.

2. Check and normalize the text string value and get attribute_text_lst.

3. Re-built attributes features, for example, keep the key value if the value is True. When the value is text, combine key value and formatted text. Then get new_attributes

4. Combine new_attributes and categories into combined_features

Use CountVectorizer's fit.tranform from sklearn.feature_extraction module to extract features and count the number of texts and store transformed matrix count_matrix into an array. Then calculate the cos θ for the two vectors in the count_matrix by cosine_similarity from sklearn.metrics.pairwise module to get a cosine_sim matrix, which is a numpy array consists of cosine similarity between each restaurants.

### 2.2.2 Model Evaluation

Use KFold from sklearn.model_selection module to split the dataset into 10 consecutive folds for train/test sets, and then calculate MAE and RMSE on each test set to get the average value and standard deviation.

Use time module to calculate trainning and test time.

## 2.3 Weighted Hybrid Filtering Model

### 2.3.1 Data Implement

1. Use SVD model to train the whole dataset and calculate the average predicted rating on each restaurant, which is set as the prediction score of collaborative filtering.

2. Use the prediction scores of content-based filtering which is calculated in section 2.2.

### 2.3.2 Model Evaluation

Use KFold from sklearn.model_selection module to split the dataset into 10 consecutive folds for train/test sets, and then calculate MAE and RMSE on each test set to get the average value and standard deviation.

Use time module to calculate trainning and test time.
