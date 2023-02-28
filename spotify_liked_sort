import os
import spotipy
from spotipy.oauth2 import SpotifyOAuth

# Set up the Spotify API client
scope = "user-library-read playlist-modify-private"
sp = spotipy.Spotify(auth_manager=SpotifyOAuth(scope=scope))

# Get the user's liked tracks playlist
playlists = sp.current_user_playlists()
liked_songs = None
for playlist in playlists["items"]:
    if playlist["name"] == "Liked Songs":
        liked_songs = playlist
        break
if not liked_songs:
    print("Liked Songs playlist not found.")
    exit()

# Get the tracks in the playlist and their genre information
tracks = sp.playlist_items(liked_songs["id"], fields="items.track(id,name,artists,album,genres)")
tracks = [item["track"] for item in tracks["items"] if item["track"] is not None]

# Create playlists for each genre and add the tracks to the appropriate playlist
genre_playlists = {}
for track in tracks:
    genres = track.get("genres", [])
    if len(genres) == 0:
        continue
    for genre in genres:
        if genre not in genre_playlists:
            playlist = sp.user_playlist_create(user=os.environ["SPOTIPY_USER"], name=genre + " Songs", public=False)
            genre_playlists[genre] = playlist["id"]
        sp.playlist_add_items(genre_playlists[genre], [track["id"]])

# Print the names of the created playlists
print("Created playlists:")
for genre in genre_playlists:
    print(genre + " Songs")
