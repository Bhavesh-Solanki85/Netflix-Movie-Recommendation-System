# Building a Netflix Movie Recommendation System with Cosine Similarity

# Introduction
The movie recommendation system is a sophisticated application of data science aimed at providing users with personalized movie suggestions. 
It leverages various techniques such as data processing, text vectorization, and similarity calculation to analyze user preferences and recommend relevant movies. 
This system is vital in enhancing user experience and engagement on movie streaming platforms by offering tailored recommendations that align with individual tastes and interests. 
By employing advanced algorithms, the movie recommendation system sifts through vast amounts of movie data, extracting meaningful insights to deliver accurate and useful recommendations to users. 
Text vectorization plays a crucial role in converting textual movie attributes into numerical representations, facilitating efficient analysis and recommendation generation.
Additionally, similarity calculation measures the likeness between movies, ensuring that recommendations are relevant and appealing to users. 
In essence, the movie recommendation system revolutionizes the way users discover and enjoy movies, offering a personalized and enriching viewing experience.

Below is a detailed breakdown of each component along with the underlying theory and steps involved:


# 1. Data Processing
The initial part of the code involves processing the movie data, specifically the "cast" and "crew" columns, to remove spaces from the strings.

# Theory:
The "cast" and "crew" columns contain lists of actors and crew members involved in each movie.
The goal is to remove spaces from the names to ensure uniformity and facilitate further analysis.
# Steps:
1. Define a function collapse(L) to remove spaces from the strings in a given list L.
2. Apply the collapse() function to the "cast," "crew," "genres," and "keywords" columns using the apply() function.
3. Display the modified DataFrame using the head() method to observe the changes.


# 2. Tag Creation
After processing the data, the code creates tags by combining information from various columns like "overview," "genres," "keywords," "cast," and "crew."

# Theory:
Tags are textual representations of movie attributes or features that will be used for similarity calculation.
By combining different columns, we create comprehensive tags that capture various aspects of each movie.
# Steps:
1. Split the "overview" column into individual words using the split() method applied within a lambda function.
2. Concatenate the split words from "overview," "genres," "keywords," "cast," and "crew" columns to create tags.
3. Use a lambda function along with the join() method to concatenate and separate tags with a space.
4. Display the modified DataFrame with the new "tags" column using the head() method.


# 3. Vectorization
Once tags are created, the code converts them into numerical vectors using the CountVectorizer.

# Theory:
CountVectorizer is a method used to convert text data into numerical vectors.
It tokenizes the text, counts the occurrences of each token, and creates a sparse matrix representing the frequency of each word in the dataset.
# Steps:
1. Import the CountVectorizer class from scikit-learn.
2. Create an instance of CountVectorizer with specified parameters like max_features and stop_words.
3. Use the fit_transform() method to transform the "tags" column into a matrix of token counts (vector).
4. Display the shape of the resulting matrix (vector) to understand the dimensions.


# 4. Similarity Calculation
After vectorization, the code calculates the cosine similarity between movie vectors.

# Theory:
Cosine similarity is a metric used to measure the similarity between two non-zero vectors.
It calculates the cosine of the angle between the vectors, indicating how similar they are irrespective of their magnitude.
# Steps:
1. Import the cosine_similarity function from scikit-learn.
2. Compute the cosine similarity between vectors, resulting in a similarity matrix (similarity).


# 5. Movie Recommendation
Finally, the code recommends similar movies based on an input movie.

# Theory:
Movie recommendation is based on the similarity between movies calculated using their feature vectors.
It involves identifying movies with high similarity scores to the input movie and presenting them as recommendations.
# Steps:
1. Define a function recommend(movie) to recommend similar movies based on the input movie.
2. Retrieve the index of the input movie in the DataFrame.
3. Sort similarity scores between the input movie and all other movies.
4. Print the top 5 similar movies (excluding the input movie itself).


# 6. Pickling
As a concluding step, the code stores the modified DataFrame and similarity matrix as pickle files.

# Theory:
Pickling is a process of serializing Python objects into a byte stream.
It allows for storing complex data structures in a file, preserving their state for future use.
# Steps:
1. Use the pickle.dump() function to store the modified DataFrame (new) and similarity matrix (similarity) as pickle files.
2. Save the pickle files with appropriate names for easy retrieval and reuse of data.

