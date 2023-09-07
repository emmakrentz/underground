# Underground Music Recommendations
Spotify had a catalogue of over 100 million songs by the end of 2022, and while this number continues to grow so does the barrier for new artists to gain recognition and streams. This is partly due to the vast amount of music available, but also because of the item cold-start problem in collaborative filtering systems: if a song has only a few hundred streams, there's simply not enough listening data available for it yet to be accurately recommended to users.

This is where content-based filtering comes in. By taking popular songs a user already likes and mapping them to songs that share similar audio features, we can recommend songs to users that they would not have otherwise heard and increase the voices of new artists in the music scene.

This is not a new idea - Spotify even has a personalized Underground Mix playlist created for each user. Mine, however, includes songs with tens of millions of streams from artists with millions of monthly listeners. If we want true underground recommendations, we'll need to do it ourselves.

For the purposes of this project, we will perform content-based filtering and nearest-neighbour calculations on the audio features of songs provided by Spotify. The basic methodology is as follows: 

1. Plot each of the songs in our underground dataset in 9-dimensional space according to the 9 audio features we've chosen to use (danceability, energy, speechiness, acousticness, instrumentalness, liveness, valence, tempo, loudness). This is our neighbourhood.

2. Pull a user's top 10 tracks from the Spotify API and plot these in the same 9-dimensional neighbourhood as above.

3. For each of the user's top 10 tracks, pull the nearest point to it  in the neighbourhood using Euclidean distance and append it to a playlist. Recommend this playlist of 10 songs to the user.
