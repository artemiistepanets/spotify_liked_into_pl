# spotify_liked_into_pl
Sorting Spotify Likes into Playlists Based on Genre

Directions to create a Spotify Developer Account
    Go to the Spotify Developer Dashboard at https://developer.spotify.com/dashboard/ and log in with your Spotify account.
    Click the "Create An App" button and fill in the required information, such as the name and description of your app.
    Once your app is created, you will be taken to the app dashboard. Here, you can find your Client ID and Client Secret, which you will need to authenticate your app with the Spotify API.
    Click on the "Edit Settings" button and add a Redirect URI. This is the URI where the user will be redirected after they grant permission to your app to access their Spotify account. You can use any valid URI for this, such as "http://localhost:8000/callback".
    Save your changes and take note of your Client ID and Client Secret, as well as your Redirect URI.
    
required to use this api in python: pip install spotipy


Then, you will need to authenticate your app with the Spotify API using your Client ID, Client Secret, and Redirect URI. You can do this using the SpotifyOAuth object from Spotipy, like this:

import spotipy
from spotipy.oauth2 import SpotifyOAuth

# Set up the Spotify API client
scope = "user-library-read playlist-modify-private" 

sp = spotipy.Spotify(auth_manager=SpotifyOAuth(scope=scope))

In this example, scope is a string that represents the permissions that your app requires to access the user's Spotify account. You can find a list of available scopes in the Spotify API documentation.

Once you have set up the Spotify API client, you can use the various methods provided by Spotipy to interact with the Spotify API, such as retrieving information about the user's playlists and adding or removing tracks from a playlist.
