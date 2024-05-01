# RhythmRadar
# Project Title: Music Recommendation System

## Team Members
- Olindi Mallika Appuhamilage
- Mahek Cheema
- Bea Alyssandra Castro
- Kelsang Tsomo

## Date
Wednesday, March 08, 2023

## Problem Description and Research Question

### Overview of Background
Spotify is the world’s most popular audio streaming platform with over 11 million artists and creators and almost 500 million users. With over 100 million tracks from various genres on the platform, the app allows users to not only listen to their favorite music but also allows users to create and save playlists based on their preferences. In order to suggest new tracks to users, Spotify’s current recommendation integrates collaborative filtering with content-based filtering. To create user-tailored recommendations, collaborative filtering examines a user's listening history. On the other hand, content-based filtering suggests music based on the features of a track, akin to mood, genre, and danceability (Marius, 2021).

### Context for Problem and Motivation
Due to the platform’s large catalogue of songs, it can make users feel overwhelmed and increase the difficulty of discovering new music and artists. Regardless of Spotify’s endeavors to curate personalized music recommendations, it can nevertheless be difficult for Spotify users to find new music, specifically from underground musicians. The primary reason for this is due to the platform’s recommendation algorithm being built to give preference to popular mainstream music and artists to attract a wider audience. For instance, many of Spotify’s playlist recommendations are created by the platform’s team or influential users, which tend to give the spotlight to well-established artists. The exposure and publicity of a track on Spotify is significantly influenced by these playlists in addition to the recommendation algorithm especially. Hence, underground and new artists are underrepresented on the platform, as it is difficult to get their music featured on these curated playlists, due to fewer resources and finances, which limits their possibilities of reaching new listeners (Mitchell, 2022).

### Project Question
To address this issue, we seek to develop a music recommendation system that curates playlists from the users preferred playlist while simultaneously putting emphasis on underground songs to support small and emerging musicians. The new algorithm will suggest a playlist of songs by lesser-known artists using a myriad of song features, such as key, danceability, tempo, popularity, and instrumentalness from the user's current playlist.

## Computational Plan

### Dataset and Graph Representation

#### Graph Representation
In our recommendation system, we will use a graph to model a song from the user’s input and the songs recommended by the program based on our computations. Each song from the user’s playlist will be the item attribute for each vertex in the graph, while the similar songs will be represented by the neighbors attribute. The similar songs will be a Spotify track from the dataset which can be accessed through Kaggle. To give the user a playlist containing 10 songs by underground artists in their most played genres, we will return the neighbor of each song with the lowest similarity score. From the dataset, we will use the ‘popularity,’ ‘danceability,’ and ‘valence’ features to calculate the similarity score.

#### Datasets
- **data.csv**: This Spotify data file contains up to 170,654 songs, with columns named ‘year’, ‘id’, ‘artists’, ‘popularity’, ‘danceability’, ‘instrumental’, ‘name’, ‘release date’, ‘valence’ and more. Some sample data in this dataset with the relevant data for our program is shown below:

| id | artists | valence | popularity | danceability |
|----|---------|---------|------------|--------------|
| 4BJqT0PrAfrxzM OxytFOIz | ['Sergei Rachmaninoff', 'James Levine', 'Berliner Philharmoniker'] | 0.0594 | 4 | 0.279 |

This data is accessible on [Kaggle Datasets](https://www.kaggle.com/code/vatsalmavani/music-recommendation-system-using-spotify-dataset/input).

### Computations
We plan to perform a computation to obtain the “similarity” between the user’s top genres. First, we will parse through the public playlist given by the user to collect the most recurring genres in the playlist. Then, the most popular song of each genre in the user’s playlist will be plotted on a scatter plot, where the x and y axis will be the “danceability” and “valence” attributes, respectively. These coordinates will be stored as tuples. The attributes chosen are “danceability” and “valence” because they seem to be proportional to each other (Ashrith, 2018). Next, the dataset will be filtered to only contain songs from the same genres as in the user’s playlist. These filtered songs are then plotted as tuples according to their “danceability” and “valence” attributes. We can use the variable current_user_song to represent the most popular song in the current genre that we are looking at. To search for similar songs, we will create a function that measures the distance between the coordinates of the most popular song in each of the genres in the user’s playlist and the coordinates of the songs in the matching genres from the dataset. The Euclidean distance formula will be used to calculate the similarity score between current_user_song and the songs from the dataset and store it as a float; the smaller the distance, the more similar the recommended song is to the song from the user’s playlist.

## References
- Mitchell, Tay. “Spotify’s Algorithm: Helping or Hurting Musicians?” Arts Management & Technology Laboratory, 28, Apr. 2022, [AMT-Lab](https://amt-lab.org/blog/2022/4/spotifys-algorithm-helping-or-hurting). Accessed 6 Mar. 2023.
- Marius, Hucker. “Uncovering How the Spotify Algorithm Works.” Towards Data Science, 23 Nov. 2021, [Towards Data Science](https://towardsdatascience.com/uncovering-how-the-spotify-algorithm-works-4d3c021ebc0). Accessed 6 Mar. 2023.
- “Web API.” Spotify for Developers. [Spotify for Developers](https://developer.spotify.com/documentation/web-api/). Accessed 6 Mar. 2023.
- Lamere, Paul. “Welcome to Spotipy!” spotipy, 2014, [Spotipy Documentation](https://spotipy.readthedocs.io/en/2.22.1/). Accessed 6 Mar. 2023.
- Watts, Cameron. “Extracting Song Data From the Spotify API Using Python.” Towards Data Science, 17 Dec. 2021, [Towards Data Science](https://towardsdatascience.com/extracting-song-data-from-the-spotify-api-using-python-b1e79388d50). Accessed 6 Mar. 2023.
- Ashrith. “What Makes a Song Likeable? - towards Data Science.” Medium, Towards Data Science, 4 Dec. 2018, [Towards Data Science](https://towardsdatascience.com/what-makes-a-song-likeable-dbfdb7abe404). Accessed 7 Mar. 2023.
