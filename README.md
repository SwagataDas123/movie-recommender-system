# movie-recommender-system

##Project Summary
This project builds a movie recommendation system using machine learning, specifically employing content-based filtering and cosine similarity. The system analyzes movie attributes (genres, keywords, cast, crew, and overview) and user preferences to provide personalized movie recommendations.

###Code Explanation:
The code can be broken down into the following steps:

##Data Loading and Preprocessing:
Imports necessary libraries (pandas, numpy).
Loads movie and credit datasets from Google Drive.
Merges the two datasets based on the movie title.
Selects relevant columns (movie_id, title, overview, genres, keywords, cast, crew).
Handles missing values by dropping rows with nulls in the 'overview' column.
Removes duplicate entries.
Transforms data in the 'genres', 'keywords', 'cast', and 'crew' columns from strings of lists of dictionaries to lists of strings.
Converts the 'overview' column from string to a list of words.

##Data Transformation:
Creates a 'tags' column by combining data from 'overview', 'genres', 'keywords', 'cast', and 'crew' columns.
Converts all text to lowercase for consistency.
Applies stemming using nltk to reduce words to their root form (e.g., 'actions' to 'action'). This helps group similar words together.

##Text Vectorization:
Uses CountVectorizer from sklearn to convert the 'tags' column into numerical vectors. This involves:
Creating a vocabulary of the most frequent words in the 'tags' (excluding stop words).
Representing each movie as a vector, where each element corresponds to the frequency of a word from the vocabulary in the movie's tags.

##Cosine Similarity Calculation:
Calculates cosine similarity between all movie vectors using cosine_similarity from sklearn. This measures the angle between vectors, indicating the similarity between movies. Higher values indicate greater similarity.

##Recommendation Function:
Defines a function recommend that takes a movie title as input.
Finds the index of the input movie in the dataframe.
Retrieves the cosine similarity scores between the input movie and all other movies.
Sorts the movies based on similarity scores in descending order.
Returns the titles of the top 5 most similar movies (excluding the input movie itself).

In essence, the code processes movie data, transforms it into a numerical format, calculates similarity between movies based on their content, and provides a function to recommend similar movies given a movie title.
