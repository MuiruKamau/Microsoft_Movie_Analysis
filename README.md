# Leveraging Movie Trends for Microsoft's New Studio

**Authors:** Muiru Kamau

***

![microsoft](images/msft-microsoft-logo-2-3.webp)

## Overview

The objective of this project is to analyze the current trends in the movie industry and identify the key success factors for creating box office hits. Microsoft has decided to enter the movie industry and launch a new movie studio, but lacks the necessary expertise in movie production. This project aims to provide actionable insights into the types of films that are currently performing well at the box office, and to help Microsoft determine what type of films they should create in order to achieve commercial success.

The project will begin by conducting a thorough analysis of data from Box office Mojo, IMDb and The movie Database for the 2014 - 2019 period, including revenue, genre. These insights will be used to develop a set of recommendations for Microsoft's new movie studio

***

## Business Problem



Business Problem: "Cracking the Code to Box Office Success: Genre Selection for Microsoft's New Movie Studio"

The objective of this business problem is to determine the optimal genre(s) for Microsoft's new movie studio to produce in order to achieve commercial success at the box office.

* Which genres have historically generated the highest average gross earnings?

 * Which genres have received the highest average ratings from audiences and critics?

* Which genres have the highest total gross earnings overall?

* Which movie genre has the highest number of movies produced?

***


## Data Understanding

We are going to be working with movie datasets from three sources

1. [TheMovieDB](https://www.themoviedb.org/):We are only intrested in two columns only <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">title</span> and <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">vote_average.</span>


2. [Box office mojo](https://www.boxofficemojo.com/): Every record represents a movie, containing details about that particular film such as its <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">domestic_gross.</span>


 3. [IMDB](https://www.imdb.com/) : the database contains multiple tables relating to movie attributes, eg ratings.<span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;"> Movie_basics</span> and  <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">movie_ratings</span> will be useful.

Box office mojo and The Movie DB are csv files we can open using <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">pd.read_csv</span>. IMDB is located in a zipped SQlite database, we must unzip and then query using SQlite.

***

We also have two other datasets that I won't be exploring but were provided for this analysis
 
   1. [The Numbers](https://www.the-numbers.com/)

 2. [Rotten Tomatoes](https://www.rottentomatoes.com/)

## Data Preparation

The process consist of :

* Importing the libraries and modules

* Accessing and reading each dataframe

* Joining SQL tables

* Merging datasets

* Dropping missing values

* Creating new columns

* Creating new datasets

* Dropping uneccessary data and columns.

***

For The Movie DB Dataset we are only interested in only two columns.

Also for the Box office Mojo Dataset we are interested in two columns that is <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">title</span> and <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">domestic_gross.</span> We are going to create a new column <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">gross_mil</span> which is earning per million and will be replacing our <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">domestic_gross.</span>

We are going to be merging the two SQL tables that is <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">movie_basics</span> and <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">movie_ratings</span> and form a new table <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">imdb_ratings_basics.</span>

We are going to merge three dataframes that is our newly formed <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">imdb_ratings_basics</span>, <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">tmdb_movies</span> and <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">movie_gross</span> using the <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">title</span> column as our key index to form our new dataframe namely <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">Movies.</span>

We are going to calculate the average rating of movies based on ratings from two different sources, IMDb and The Movie Database (TMDb), and stores the result in a new column called <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">average_rating.</span>.

`We created a subset called movies_mini. which I'm going to work with hence forth in my analysis. This new, smaller DataFrame contains only the most successful and well-received movies released in recent years.In particular, the 'movies_mini' DataFrame only contains movies with a rating of at least 7.0, gross earnings of at least 30 million dollars, and a release year after 2013. By filtering for these specific criteria, We can focus my analysis on the most profitable and critically acclaimed movies of recent years.`

## Preparing our data for every question for modelling

### Question one: Prepare average gross earning data


We created a DataFrame called <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">top_gross</span> that shows the average gross earnings for each movie genre in the movies_mini DataFrame.

***
### Question two: Prepare average rating data


We created a DataFrame called <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;">genre_ratings </span> that shows the average rating for each movie genre in the movies_mini DataFrame. The DataFrame only includes genres that have 7 or more ratings.

***
### Question three: Prepare total gross earnings data

We filtered the movies_mini DataFrame to only include movies with gross earnings greater than 150 million dollars and a release year after 2013. Then, we grouped the remaining data by genre and calculated the sum of gross earnings in millions for each genre. The resulting DataFrame was sorted by gross earnings in descending order and converted to display earnings in billions. Finally, we dropped the start_year column and displayed the updated gross_earnings DataFrame.

***
### Question four: Prepare No of movies data

We created a new DataFrame called <span style="background-color: #3d3d3d; color: #ffffff; padding: 2px 5px; border-radius: 3px;"> top_genre</span> by extracting only the 'genres' and 'title' columns from the movies_mini DataFrame. We then grouped the data by genre and counted the number of unique movie titles in each genre to get an idea of the number of movies in each genre. The resulting DataFrame was sorted by the number of movies in descending order. This information can help us understand the popularity of each genre and how well-represented each genre is in our dataset.

***
