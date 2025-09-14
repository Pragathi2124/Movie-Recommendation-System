# Movie_Recommendation_System

# Content-Based Movie Recommendation System

**🎬 Project Overview**
This project implements a content-based movie recommendation system. The system is designed to suggest movies to users based on the content and attributes of a movie they have already watched and liked. By analyzing key features such as genres, keywords, cast, and crew, the model identifies and recommends other movies with similar characteristics.

The core of this recommendation engine is the use of Natural Language Processing (NLP) to convert textual information into numerical vectors, followed by the application of Cosine Similarity to measure the likeness between movies. This approach allows for effective and contextually relevant recommendations, demonstrating a practical application of vector space models in building intelligent systems.

**💾 Dataset**
This project utilizes the TMDB 5000 Movie Dataset, which is publicly available on Kaggle. The dataset is split into two CSV files:
movies.csv: Contains detailed information for approximately 5,000 movies, including budget, genres, keywords, overview, title, and more.
credits.csv: Contains the cast and crew information for each movie, linked by a unique movie ID.

**⚙️ Methodology**
The recommendation system was built by following these key steps:

**Data Loading and Merging:** The movies.csv and credits.csv datasets were loaded into pandas DataFrames and then merged into a single DataFrame based on the movie title. This consolidation creates a unified dataset containing all relevant movie information.

**Feature Selection:** To build a content-based model, the most descriptive features were selected: movie_id, title, overview, genres, keywords, cast, and crew. All other columns were dropped to streamline the dataset.

**Data Preprocessing and Cleaning:**
Missing values were handled by dropping any rows with null entries to ensure data quality.
Helper functions were created to parse the stringified JSON in the genres, keywords, cast, and crew columns. These functions extract the relevant names (e.g., genre names, top 3 actors, director's name).
To treat multi-word names (like "Sam Worthington") as a single entity, all spaces were removed from the extracted names (e.g., "SamWorthington").

**Feature Engineering:** A new tags column was engineered by concatenating the cleaned overview, genres, keywords, cast, and crew columns. This tags column serves as a comprehensive textual summary of each movie.

**Text Vectorization:**
The tags column was converted into a corpus of text.
The CountVectorizer from Scikit-learn was used to transform this text into a numerical vector space using the Bag-of-Words model. This process was limited to the top 5,000 most frequent words (features) and excluded common English stop words.

**Similarity Calculation:**
Cosine Similarity was calculated between all movie vectors. This metric measures the cosine of the angle between two vectors, providing a score of their similarity (a score closer to 1 means more similar).
This resulted in a similarity matrix where each movie is compared against every other movie in the dataset.

**Recommendation Function:** A final function, recommendationsystem(movie), was built to productionize the model. This function takes a movie title as input, retrieves its similarity scores against all other movies, sorts them in descending order, and returns the titles of the top 5 most similar movies.


**✨ Technologies Used**
Python
Pandas: For data manipulation and analysis.
NumPy: For numerical operations.
Scikit-learn: For implementing the CountVectorizer and calculating cosine_similarity.
Jupyter Notebook: For interactive development and code presentation.

