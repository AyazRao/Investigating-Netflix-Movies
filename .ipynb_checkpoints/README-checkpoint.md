# Investigating-Netflix-Movies

![projectimage](images/redpopcorn.jpg)

Apply the foundational Python skills you learned in Introduction to Python and Intermediate Python by manipulating and visualizing movie data.

# Netflix Movie Duration Analysis

## Project Description
In this project, the goal is to apply Python skills to answer a real-world question about Netflix movies. The objective is to determine if Netflix's movies are getting shorter over time by utilizing Python tools such as lists, loops, pandas, and matplotlib for exploratory data analysis. The dataset `netflix_data.csv` is provided, and the analysis will involve manipulating raw data and drawing conclusions from plots generated during the analysis.

## Netflix Overview
Netflix, founded in 1997 as a DVD rental service, has evolved into one of the largest entertainment and media companies globally. With a vast library of movies and series, this project provides an opportunity to explore the entertainment industry and analyze trends in movie durations.

## The Data
The dataset `netflix_data.csv` contains the following columns:

- `show_id`: The ID of the show
- `type`: Type of show
- `title`: Title of the show
- `director`: Director of the show
- `cast`: Cast of the show
- `country`: Country of origin
- `date_added`: Date added to Netflix
- `release_year`: Year of Netflix release
- `duration`: Duration of the show in minutes
- `description`: Description of the show
- `genre`: Show genre

## Getting Started
```bash
git clone https://github.com/AyazRao/What-and-Where-are-the-World-s-Oldest-Businesses.git
cd What-and-Where-are-the-World-s-Oldest-Businesses
```

## Project Instructions

### 1. Load the Data
```
Load the `netflix_data.csv` file and store it as `netflix_df`.

import pandas as pd

netflix_df = pd.read_csv("netflix_data.csv")
```
###  2. Data Filtering
   
Remove TV shows and create a subset named netflix_subset.
```
netflix_subset = netflix_df[netflix_df["type"] == "Movie"]
```
###  3. Data Investigation

Create a new DataFrame netflix_movies with the columns "title", "country", "genre", "release_year", "duration".
```
netflix_movies = netflix_subset[['title', 'country', 'genre', 'release_year', 'duration']]
```
###  4. Identify Short Movies

Filter netflix_movies to find movies shorter than 60 minutes and save as short_movies.
```
short_movies = netflix_movies[netflix_movies['duration'] < 60]
```
###  5. Genre Color Assignment

Use a for loop and if/elif statements to iterate through the rows of netflix_movies and assign colors to four genre groups ("Children", "Documentaries", "Stand-Up", and "Other").
```
colors = []

for label, row in netflix_movies.iterrows():
    if row["genre"] == "Children":    
        colors.append("red")        
    elif row["genre"] == "Documentaries":    
        colors.append("blue")        
    elif row["genre"] == "Stand-Up":    
        colors.append("green")        
    else:    
        colors.append("black")
```
###  6. Scatter Plot Creation

Initialize a figure object called fig and create a scatter plot for movie duration by release year using the colors list.
```
import matplotlib.pyplot as plt

fig = plt.figure(figsize=(12,8))
plt.scatter(netflix_movies.release_year, netflix_movies.duration, c=colors)
plt.title("Movie Duration by Year of Release")
plt.xlabel("Release year")
plt.ylabel("Duration (min)")
plt.show()
```
###  7. Answer the Question

Inspect the plot and answer the question "Are we certain that movies are getting shorter?" by assigning either "yes", "no", or "maybe" to the variable answer.
![Result](images/Result.png)

***answer = "maybe"***
