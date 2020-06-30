# Movie Recommendation with ALS and Spark APIs
[Notebook](https://nbviewer.jupyter.org/github/bb-li/Movie-Recommendation-with-ALS-and-Spark-APIs/blob/master/Moive_data_MLbased.ipynb)

Use an Alternating Least Squares (ALS) algorithm with Spark APIs to predict the ratings for the movies.

When we are doing online shopping or visiting video websites, like Amazon and Hulu, we always see a list named “You may also like”. I am very curious about how the online shopping or video platform come up with this list. And I want to use the data analysis technique to recommend products to different users and find out the similar products for the specific products.

1. At first, I download the movie data and create four data frames, movies_df, ratings_df, links_df and tags-df. And I use some basic methods to give a brief glance of the data.
2. After that, I used spark SQL to do OLAP of the data. I found out the total number of users is 610 and the total number of movies is 9742. After some SQL operation, we can see there are around 20 movies which have no rating. And I also used spark SQL to build a table with lists of all movies for each category.
3. Then we used park ALS to train the movie data and hopefully we can use this model to predict all the ratings for all users and find out the similar movies. First, we import the evaluator, ALS and the tuning packages. Then we create test and train set. After that, we turn the model using paramGridBuilder. Then we fit the model by cross validation. Then we extract best model, generate predictions and evaluate using RMSE. After model testing, we apply the model to see the performance.
4. Finally, we can use the model to recommend the movies to specific users. Most importantly, using the dot production from the features matrix, which we extracted from the ALS models, we can find out the similarities among diferent movie items. This feature is very useful when customers want to explode the similar products based on their existing favorite products.

This ALS model can be useful to recommend movie to a current user. However, it has a coldstart issue and it is not applicable for a new user with no former information.
