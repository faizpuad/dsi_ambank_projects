Project 3: Web APIs & NLP

### Problem Statement

As a career advisor, I am tasked to finding supporting materials to suggest to students for aiding them choosing a career path to venture program in a university. However, the problem I am facing with surveying and finding the differences between courses are : it is time consuming to find all available materials through manual and available means (reading online article,refer to readily available career guide etc) and also lack of depth knowledge to segregate a source is from what domain. This study is conducted in hope that nlp is available to break these problem's barrier.

### Methodology

1. Import dataset from excel files and change into dataframe

2. Explore the dataframe in term of its:-  
- shape(row & column)
- missing values

3. Do data cleaning from the exploration finding including:
- drop null value from dataset. This is focus on selftext columns and author name.
- drop NaN value if any occur in selftext or author column
- built custom function to remove unnnecessary symbol such as '?,/,!,@,#', remove hyperlink

4. Feature Engineering using Transformer
- Use count vectorizer and tfrid transformer to transform value in selftext column.
- Use Porter stemmer to conver word into its root form

5. Feature selection
- Drop some random rows in datascience dataset to balance target variable(column subreddit) for classifcation training

6. Initiate Model
- Do train test split between train data and test data.
- One estimator is use- Multinomial Naive Bayes and is compare with its application using count vectorize versus tfrid vectorizer.
- Compare evaluation metrics including accuracy, F1 score and classification metrics between model and choose the one with lowest false positive and false negative error (also can be seen from accuracy score of less overfit model)

### Conclusions And Recommendation
- Both application of Multinomial with count vectorizer and tfid vectorizer are found overfit.
- The best perform among the model tested where:
	+ accuracy score is 0.887 for train data and 0.885 for train data
	+ The model is slightly overfit
  + few possible reasons are:
    + train data is not enough. This is prove as I increase from initial data of 2000 to 6000, train score drop from 95% to 88% but increase test score from 80% to 88%
    + data still contain unnecessary symbol including emoji which cause inaccurate prediction
- Recommendation:
  - Model found to be useful for detecting sentiment and  classifying a post into category. Thus, it can be fitted generally to all industry such as marketing to promote their product.
  - Model results can be utilized as providing snapshot of a person to be filter for job application based on finding above.
  - Introduce more data to fight overfit issue and there is possibility model perform higher tha 90% using other model including random forest,adaboost

### Resources Use in The Project:

- Yadav, K. (2022, January 22). Cleaning & Preprocessing Text Data by Building NLP Pipeline. Medium.

    + source: https://towardsdatascience.com/cleaning-preprocessing-text-data-by-building-nlp-pipeline-853148add68a

- Varshney, P. (2021, December 14). Q-Q Plots Explained - Towards Data Science. Medium.

	+ Available at: https://towardsdatascience.com/q-q-plots-explained-5aa8495426c0

- How COVID-19 has pushed companies over the technology tipping point—and transformed business forever. (2021, February 18). McKinsey & Company.

  + Available at: https://www.mckinsey.com/business-functions/strategy-and-corporate-finance/our-insights/how-covid-19-has-pushed-companies-over-the-technology-tipping-point-and-transformed-business-forever#

- Statista. (2022, February 21). IT industry growth rate forecast worldwide from 2018 to 2023, by segment.

  + Available at: https://www.statista.com/statistics/967095/worldwide-it-industry-growth-rate-forecast-segment/

### Data Dictionary

| Column | Description | Datatype |
| ------ | ------ | ------- |
| author | name of author | String |
| author_fullname | full name of author | String |
| created_utc | Date and time of post created | integer |
| full_link | the link for the post | String |
| id | subreddit post id | integer |
| num_comments | number of comment in a post | integer |
| score | score rating of the post | integer |
| selftext | post description | string |
| subreddit | name of the subreddit | String |
| subreddit_id | id of subreddit | integer |
| subreddit_subscribers | number of subscriber for a user | integer |
| title | title of a post | String |
| upvote_ratio | ratio of user rating for a post | integer |
| url  | url included in a post | String |
