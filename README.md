# Recommendations with IBM

In this project I have analyzed the interactions that users have with articles on the IBM Watson Studio platform, and have made recommendations to them about new articles we think they will like. 

## Table of contents

I. Exploratory Data Analysis<br>
II. Rank Based Recommendations<br>
III. User-User Based Collaborative Filtering<br>
IV. Content Based Recommendations (EXTRA - NOT implemented)<br>
V. Matrix Factorization<br>
VI. Extras & Concluding

First, we explore the data sets. We have two csv files: _user-item-interactions.csv_ and _articles_community.csv_. The former include users (indicated by their emails) and the article ids and article titles that each of them had interacted with. The latter, on the othar hand has the detailed information (such as the document body or body text, description, etc) regarding each of the articles on the IBM. 

Then we move on to ranked-based recommendaion, which can be considered as the first stepping stone towards building a recommendation engine. Results of such recommendation can be used for any user including the new users that have no history of interaction on the platform to be used for a more personalised recommendation.

A user-user based collaboraborative filtering works on finding the most similar (cosine similarity) users and recommending their highest-interacted articles that are not read by our user. 

The matrix factorization uses SVD for recommendation. To test how this recommendation system works we separated our data to two sets: training and testing datasets. The U, S, and V matrices are then computed using the training set and are used for prediction on testing dataset. As this resommendation system cannot be used for new users, we first separate the common users between the testing and training datasets and then make the recommendation for those users in the testing dataset who also exist in the training dataset. 

# Files and folders descriptions

- data folder: this folder includes two csv files:
	- user-item-interactions.csv
	- articles_community.csv
- Recommendations_with_IBM.ipynb: a Jupyter notebook where I have analyzed the data and wnet through each step as listed in the _Table of Contents_
- Recommendations_with_IBM: a html file created from the Recommendations_with_IBM.ipynb
- project_tests.py:  pyhton code including test functions used throughout the Jupyter notebook to test different functions and results. 
- top_5.p, top_10.p, top_20.p: top 5, 10, 20 articles to be used in testing if our `get_top_articles` function works correctly.
- user_item_matrix.p: a complete user-item matrix that is read in the fifth part of the notebook (Matrix Factorization).

# Results and conclusion

In this notebook, I analyzed the data regarding the interactions that users have with articles on the IBM Watson Studio platform. I used three methods of recommendations namely, Ranked-based recommendation, user-user (neighborhood) collaborative filttering, and model-based (Matrix Factorization - SVD) collaborative filtering to recommend new articles we think the users will like. The Ranked-based recommendation is suitable for new users to the platform, whom we do not have any history of interaction with the platform to make a more personalized recommendation. The user-user collaborative filtering works in this way that it finds the most similar users to our candidate and then, among all the articles that the neighbor user has interacted with, we recommend the most interacted articles to our candidate. This method is one step towards making a more personalized recommendation, however it is not suitable for dealing with new users. With the model-based collaborative recommendation we use matrix factorization (SVD in this case), which not only helps us with making a more personalized recommendation (due to the latent featurs that are related to the articles and users) we can measure how well our prediction works by splitting our data to train and test datasets. However, again this method cannot handle new users, therefore our evaluation is restricted to users and articles that are shared between train and test datasets. To deal with new users (cold start), my suggestions would be using the ranked based technique and/or a combination of knowledge-based (not implemented here) + content-based (not implemented here) + ranked-based recommendations.

To evaluate how well our recommendation engine is working we can run an A/B testing. We will need two groups: control and test groups. Users will be randomly assigned to each group. The control group will interact with the platform using the default recommendations while the test group will see the version of the platform that uses our designed recommendation engine. Then we can measure the performance and the improvement to the system by using evaluation metrics, such as click through rate (CTR) of recommended articles and/or the average reading duration of the recommended articles.

# Packages and libraries

The code runs with Python3 and need the libraries as listed:
- `pandas`
- `numpy` 
- `matplotlib.pyplot`
- `project_tests` (cutom written python code included here)
- `pickle`

 

 
