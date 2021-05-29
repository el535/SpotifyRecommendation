# SpotRec: A Spotify Recommendation System

A Spotify Song Recommendation System that utilizes both content-based filtering and collaborative filtering. The recommendation system provides the user the opportunity to select what audio feature of the song they prefer in order to provide a more personal song recommendation.

## Data
Two datasets are used to build the recommendation system: Spotify Million Playlist Dataset (MPD) and 160K Track Playlist taken from the Spotify API. 

Spotify Million Playlists Dataset contains one million playlists created between 2010 and 2017 by Spotify users in the U.S. The dataset is 33GB, and contains 1,000 JSON files, each consisting of 1,000 playlists. Each playlist contains:
- Playlist meta-data: id, name, description, # of albums, # of artists, # of tracks, # of followers, duration, etc...
- Track: url, name, artist, album, duration, the position in the playlist, etc...

Statistics for the playlist are here:

![Playlist Stats](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Playlist_Stats.JPG)

The 160K Track playlist is collected using the Spotify API. This dataset consists of 169909 songs with release dates between 1921 and 2020. Each song contains:
- Song Description: Song Artist(s), Track ID, Song Name, Genre, Released Date, Released Year, and Song Popularity
- Audio Features: Acousticness, Danceability, Energy, Duration (ms), Instrumentalness, Valence, Tempo, Liveness, Loudness, Speechiness, Key, Mode, Song Key, and Explicit Content

## EDA
Here are some plots to show the distribution of the MPD metadata:
![Playlist Bar](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Playlist_info.JPG)
![Playlist_Histo](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Playlist_Histo.JPG)

Here is a bar graph showing some of the top tracks, albums, and artists in the MPD dataset:

![Playlist_Top](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Playlist_Top.JPG) 

Audio Features make up most of the metadata for the 160K Track Playlist. Here are the histograms of all the audio features in the dataset:
![Histo](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Spotify_Histogram.JPG)

## Results
The MPD dataset is used to create the collaborative filtering part of the recommender system, while the 160K Track Playlist Dataset is used to create the content-based filtering part of the system. 

Here are some sample outputs of the collaborative filtering part:
![Colab_Filtering_Recs](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Colab_Filtering_Recs.JPG)

Here are some sample outputs of the content-based filtering part:
![Content_Filtering_Recs](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Content_Recs.JPG)

Weights on audio features are implemented to allow the user to have more control over the recommendations. Here are some sample outputs for the same input as before, but with different audio feature weights:
![Content_Filtering_Weights](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Content_Recs_Weights.JPG)

In order to combine the collaborative filtering part and the content-based filtering part, an 'alpha' weight is assigned to control how much of each part is used in the combined recommendation system. The alpha weight value is deturmined by the highest R-precision value of the recommender system per alpha value, deturmined to be more weighted towards the collaborative filtering part:
![Alpha](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Weights_Precision.JPG)

Here are some sample outputs of the combined recommendation system:
![Combined](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Combined_Recs.JPG)

## Evaluation
To quantify how well the recommendation system work, R-precision value is used. R-precision values are shown here:
![R-precision](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/Precision.JPG)

## UI
The user can input a song and adjust the audio feature sliders on the UI to recieve personalized song recommendations. Here are some screenshots of the UI and its recommendations:
![UI_Input](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/UI_Song_Input.JPG)
![UI_Recs](https://github.com/el535/SpotifyRecommendation/blob/main/Project_Images/UI.JPG)
