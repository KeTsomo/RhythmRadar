# RhythmRadar

\documentclass[fontsize=11pt]{article}
\usepackage{amsmath}
\usepackage[utf8]{inputenc}
\usepackage[margin=0.75in]{geometry}
\usepackage{graphicx}
\usepackage{tabularx}

\author{Olindi Mallika Appuhamilage, Mahek Cheema, Bea Alyssandra Castro, Kelsang Tsomo}
\date{Wednesday, March 08, 2023}

\begin{document}
\maketitle

\section*{Problem Description and Research Question}

\begin{enumerate}
\item \textbf{Overview of Background} \newline
  Spotify is the world’s most popular audio streaming platform with over 11 million artists and creators and almost 500 million users. With over 100 million tracks from various genres on the platform, the app allows users to not only listen to their favourite music, but also allows users to create and save playlists based on their preferences. In order to suggest new tracks to users, Spotify’s current recommendation integrates collaborative filtering with content-based filtering. To create user-tailored recommendations, collaborative filtering examines a user's listening history. On the other hand, content-based filtering suggests music based on the features of a track, akin to mood, genre and danceability (Marius, 2021). \newline

  \item\textbf{ Context for problem and motivation} \newline
  Due to the platform’s large catalogue of songs, it can make users feel overwhelmed and increase the difficulty of discovering new music and artists. Regardless of Spotify’s endeavors to curate personalized music recommendations, it can nevertheless be difficult for Spotify users to find new music, specifically from underground musicians. The primary reason for this is due to the platform’s recommendation algorithm being built to give preference to popular mainstream music and artists to attract a wider audience. For instance, many of Spotify’s playlist recommendations are created by the platform’s team or influential users, which tend to give spotlight to well-established artists. The exposure and publicity of a track on Spotify is significantly influenced by these playlists in addition to the recommendation algorithm especially. Hence, underground and new artists are underrepresented on the platform, as it is difficult to get their music featured on these curated playlists, due to fewer resources and finances, which limits their possibilities of reaching new listeners (Mitchell, 2022). \newline

  \item \textbf{Project question} \newline
  To address this issue, we seek \textbf{to develop a music recommendation system that curates playlists from the users preferred playlist while simultaneously putting emphasis on underground songs to support small and emerging musicians.} The new algorithm will suggest a playlist of songs by lesser-known artists using a myriad of song features, such as key, danceability, tempo, popularity, and instrumentalness from the user's current playlist. \newline


\end{enumerate}

\section*{Computational Plan}

\begin{enumerate}
\item \textbf{Dataset and Graph Representation} \newline

\textbf{Graph Representation} \newline
In our recommendation system, we will use a graph to model a song from the user’s input and the songs recommended by the program based on our computations. Each song from the user’s playlist will be the item attribute for each vertex in the graph, while the similar songs will be represented by the neighbours attribute. The similar songs will be a Spotify track from the dataset which can be accessed through Kaggle. To give the user a playlist containing 10 songs by underground artists in their most played genres, we will return the neighbour of each song with the lowest similarity score. From the dataset, we will use the ‘popularity,’ ‘danceability,’ and ‘valence’ features to calculate the similarity score. \newline

\textbf{Datasets}

\begin{itemize}
  \item data.csv \newline
This Spotify data file contains up to 170,654 songs, with columns named ‘year’, ‘id’, ‘artists’, ‘popularity’, ‘danceability’, ‘instrumental’, ‘name’, ‘release date’, ‘valence’ and more. Some sample data in this dataset with the relevant data for our program is shown below:
 \newline

  \begin{tabularx}{1\textwidth} { 
  | >{\centering\arraybackslash}X 
  | >{\centering\arraybackslash}X 
  | >{\centering\arraybackslash}X 
  | >{\centering\arraybackslash}X 
   | >{\centering\arraybackslash}X 
  | >{\centering\arraybackslash}X }

 \hline

 id & artists & valence & popularity & danceabilitiy  \\
 \hline
4BJqT0PrAfrxzM
OxytFOIz  & ['Sergei Rachmaninoff', 'James Levine', 'Berliner Philharmoniker'] & 0.0594 & 4 & 0.279 \\
\hline
\end{tabularx} \newline

This data is accessible on Kaggle Datasets, https://www.kaggle.com/code/vatsalmavani/music-recommendation-system-using-spotify-dataset/input \newline

\end{itemize}

  \item\textbf{Computations} \newline
We plan to perform a computation to obtain the “similarity” between the user’s top genres. First, we will parse through the public playlist given by the user to collect the most recurring genres in the playlist. Then, the most popular song of each genre in the user’s playlist will be plotted on a scatter plot, where the x and y axis will be the “danceability” and “valence” attributes, respectively. These coordinates will be stored as tuples. The attributes chosen are “danceability” and “valence” because they seem to be proportional to each other (Ashrith, 2018). Next, the dataset will be filtered to only contain songs from the same genres as in the user’s playlist. These filtered songs are then plotted as tuples according to their “danceability” and “valence” attributes. We can use the variable current\_user\_song to represent the most popular song in the current genre that we are looking at. To search for similar songs, we will create a function that measures the distance between the coordinates of the most popular song in each of the genres in the user’s playlist and the coordinates of the songs in the matching genres from the dataset. The Euclidean distance formula will be used to calculate the similarity score between current\_user\_song and the songs from the dataset and store it as a float; the smaller the distance, the more similar the recommended song is to the song from the user’s playlist. 


  \item \textbf{Visualization/Interactive Model} 

\includegraphics[width=.5\textwidth]{Start.png}
\includegraphics[width=.5\textwidth]{Display.png}
\newline
\newline Our program will display a starting page and ask the user to input the link to a public Spotify playlist with songs they like. It will then use the playlist and access the song’s categories, such as genre, danceability, valence, and popularity. Using these categories, we can calculate a similarity score by comparing it with other songs in our data set, and return the ones with the lowest popularity. Our program will then display a list of ten songs for the user based on their inputted playlist and have an option to “like” or “dislike” based on the user's opinion of the songs. These reviews will help our program improve its recommendation system. Our background visuals will be created using pygame.Surface, which will create the various shapes like boxes and circles, fill in the colour and create the text. Furthermore, to manage human interactions like mouse clicks and keyboard strokes, we can also use Pygame's event module. Using pygame.event for the button the user can click ‘Like’ or ‘Dislike’ on the recommended song, and also click the option to make another playlist if the user would like to input another Spotify playlist of their liking. 
 \newline 



   \item \textbf{Python Libraries} \newline
\textbf{Pandas} is a toolkit for data manipulation and analysis that offers simple data structures and methods for working with organized and structured data. This Python library will be used for the filtering, processing and manipulation of the playlist data provided by the user and the Spotify API data. We can combine and consolidate the datasets based on various features, such as key, danceability, tempo, popularity etc, and use Pandas methods to manage missing values, such as when the genre of the song in the data is missing. Moreover, the groupby() function will be used to group tracks according to their characteristics such as genre, and to calculate statistics and central tendency. \newline


\textbf{PyGame} is used for developing video games and multimedia applications. For our song recommendation system, we plan to use the Pygame library to create a graphical user interface. In particular, we'll make an interface for human interaction with the system using Pygame's display module. \newline\newline\newline

\textbf{Spotipy} allows us to readily access the Spotify Web API where we can obtain information about artists, albums, playlists and tracks. This Python library will be used to gather necessary data about the songs found in the user's playlist and songs in Spotify’s database that will be recommended to users, specifically the song characteristics akin to key, danceability, popularity, valence, tempo and more. Spotipy features the following function, sp.audio\_features(tracks=[]), which returns the audio features for a list of songs. The public playlist inputted from the user can provide us with a catalogue of track IDs that we can pass into the function. \newline 

\end{enumerate}

\section*{References} 
Mitchell, Tay. “Spotify’s Algorithm: Helping or Hurting Musicians?” Arts Management \& Technology Laboratory, 28, Apr. 2022, https://amt-lab.org/blog/2022/4/spotifys-algorithm-helping-or-hurting. Accessed 6 Mar. 2023. \newline

Marius, Hucker. “Uncovering How the Spotify Algorithm Works.” Towards Data Science, 23 Nov. 2021, https://towardsdatascience.com/uncovering-how-the-spotify-algorithm-works-4d3c021ebc0. Accessed 6 Mar. 2023 \newline

“Web API.”  Spotify for Developers. https://developer.spotify.com/documentation/web-api/. Accessed 6 Mar. 2023. \newline

Lamere, Paul. “Welcome to Spotipy!” spotipy, 2014, https://spotipy.readthedocs.io/en/2.22.1/. Accessed 6 Mar. 2023. \newline

Watts, Cameron. “Extracting Song Data From the Spotify API Using Python.” Towards Data Science, 17 Dec. 2021, https://towardsdatascience.com/extracting-song-data-from-the-spotify-api-using-python-b1e79388d50. Accessed 6 Mar. 2023. \newline


Ashrith. “What Makes a Song Likeable? - towards Data Science.” Medium, Towards Data Science, 4 Dec. 2018, towardsdatascience.com/what-makes-a-song-likeable-dbfdb7abe404. Accessed 7 Mar. 2023.\newline

% NOTE: LaTeX does have a built-in way of generating references automatically,
% but it's a bit tricky to use so we STRONGLY recommend writing your references
% manually, using a standard academic format like APA or MLA.
% (E.g., https://owl.purdue.edu/owl/research_and_citation/apa_style/apa_formatting_and_style_guide/general_format.html)

\end{document}
