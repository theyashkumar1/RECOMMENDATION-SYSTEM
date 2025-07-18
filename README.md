# RECOMMENDATION-SYSTEM

COMPANY: CodTech IT Solutions

NAME: Yash Kumar

INTERN ID: CT06DG602

DOMAIN: Machine Learning

DURATION: 6 Weeks

MENTOR: Neela Santosh

📂 Dataset

This project utilizes the MovieLens 100K dataset, a widely-used benchmark dataset provided by GroupLens Research. The dataset includes:

movies.csv:
Contains metadata about movies, including:

movieId: Unique ID for each movie

title: Movie title along with release year

genres: Pipe-separated list of genres (not used in this model)

ratings.csv:
Contains user ratings for movies:

userId: Unique user ID

movieId: ID of the movie rated

rating: Rating given by the user (0.5 to 5.0)

timestamp: Time of rating (not used here)

After merging these datasets, we drop unused columns (genres, timestamp) and focus on userId, title, and rating.



Movie Recommendation System using Collaborative Filtering

This project presents a personalized movie recommendation system built using collaborative filtering techniques. It utilizes the MovieLens dataset and applies item-item similarity based on Pearson correlation to recommend movies similar to those the user has rated in the past.

=>Objective

The primary goal of this project is to build a recommendation engine that can suggest movies to users based on their previous preferences. Instead of relying on content-based information like genres or actors, this system focuses on how users rate movies, identifying patterns and relationships between different movies through collaborative filtering. More specifically, this project implements memory-based item-item collaborative filtering.

=>How it Works

This recommendation system follows the principle of collaborative filtering, where recommendations are based on the idea that if users rate certain items similarly, they may have similar preferences for other items as well.

Here's a breakdown of the pipeline:

 1. Data Loading and Merging

The system uses two datasets:

ratings.csv: Contains user ratings for various movies.

movies.csv: Contains movie metadata such as movieId, title, and genres.

These datasets are merged to form a comprehensive dataset containing userId, movieId, title, and rating.

 2. Pivot Table Creation

The merged dataset is transformed into a pivot table with:

Rows as userId

Columns as movie titles

Values as the ratings given by users

This forms a user-movie matrix, which is essential for computing correlations between different movies.

 3. Filtering Sparse Data

To reduce noise and improve reliability:

Movies rated by fewer than 10 users are removed.

Remaining NaN values are filled with 0 to ensure consistent matrix structure.

This filtering step ensures that recommendations are based on reliable and sufficient data points.

 4. Similarity Calculation

Using the filtered pivot table, Pearson correlation is calculated between every pair of movies. This produces a correlation matrix, where each value indicates how similarly two movies are rated by users.

 5. User Preference Simulation

To simulate a real user, a list of movies and ratings is created manually,
action_lover = [
    ("2 Fast 2 Furious (2003)", 5),
    ("12 Years a Slave (2013)", 4),
    ("2012 (2009)", 3),
    ("(500) Days of Summer (2009)", 2)
]

Each movie’s similarity vector is adjusted by the rating given by the user (centered around 2.5), and all such vectors are aggregated to determine the most relevant movies.

 6. Generating Recommendations

All similarity vectors are concatenated and summed. The result is a ranked list of movie recommendations, with higher scores indicating stronger relevance to the user’s preferences.

For example, a user who enjoys action-packed or emotionally intense films may get recommendations like:

Fast & Furious

Crank

Wanted

Mission: Impossible III

=> Technologies Used
Python

Pandas: Data manipulation

NumPy: Numeric operations

scikit-learn: Similarity computation

=> Why Collaborative Filtering?

Collaborative filtering offers the advantage of not needing metadata like genres or actor lists. Instead, it learns patterns purely from user behavior, making it flexible and adaptive to different domains. This model is particularly useful when:

You have a large number of users and items.

You want recommendations based on crowd behavior.

Conclusion
 
This project provides a practical and understandable implementation of collaborative filtering using real-world data. By analyzing user ratings and movie similarities, it successfully recommends movies tailored to individual tastes without requiring content metadata. It’s a simple yet powerful demonstration of how user behavior can be leveraged to build intelligent systems.
