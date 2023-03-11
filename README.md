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