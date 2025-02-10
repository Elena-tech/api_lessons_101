### **📌Creating a Spotify Playlist Analyzer (Step-by-Step)**  

#### **Title:** *Step-by-Step Guide to Analyzing Spotify Playlists*  

#### **Content:**  
✅ **Goal:** Retrieve and analyze user playlists from the **Spotify API**.  
✅ **Tech Stack:** Python (`spotipy`), OAuth authentication, and JSON parsing.  

### **🔹 Step 1: Get Spotify API Credentials**  
- Sign up at [Spotify Developer Dashboard](https://developer.spotify.com/dashboard).  
- Create a new app and **copy the following credentials**:  
  - **Client ID**  
  - **Client Secret**  
  - **Redirect URI** (Set this to `"http://localhost:9090"` in Spotify settings).  

### **🔹 Step 2: Install and Authenticate with Spotipy**  
- **Install Spotipy** (if not installed):
  ```bash
  pip install spotipy
  ```
- **Authenticate and Fetch User Playlists**:
  ```python
  import spotipy
  from spotipy.oauth2 import SpotifyOAuth

  # Set up authentication
  sp = spotipy.Spotify(auth_manager=SpotifyOAuth(client_id="YOUR_CLIENT_ID",
                                                 client_secret="YOUR_CLIENT_SECRET",
                                                 redirect_uri="http://localhost:9090",
                                                 scope="playlist-read-private"))

  # Get user playlists
  playlists = sp.current_user_playlists()
  for playlist in playlists['items']:
      print(playlist['name'])
  ```

### **🔹 Step 3: Extract Playlist Data**  
- Retrieve **playlist name, total tracks, and owner details**.
- Example JSON response:
  ```json
  {
      "name": "Chill Vibes",
      "tracks": {
          "total": 50
      },
      "owner": {
          "display_name": "John Doe"
      }
  }
  ```
- Print key details in a user-friendly format:
  ```python
  for playlist in playlists['items']:
      print(f"Playlist: {playlist['name']}, Tracks: {playlist['tracks']['total']}")
  ```

### **🔹 Step 4: Analyze Song Features (Danceability, Energy, Tempo)**  
- Use **`sp.audio_features()`** to fetch song metadata.
- Example:
  ```python
  track_id = "3n3Ppam7vgaVa1iaRUc9Lp"  # Example track ID
  features = sp.audio_features([track_id])[0]
  print(f"Danceability: {features['danceability']}, Energy: {features['energy']}")
  ```

### **🔹 Step 5: Bonus - Visualize Playlist Statistics**  
- Use **Matplotlib or Streamlit** to display:
  - **Top songs by energy level** 🎵⚡  
  - **Danceability trends in a playlist** 💃  
  - **Playlist duration & track distribution** 📊  

```python
import matplotlib.pyplot as plt

danceability = [0.8, 0.6, 0.75, 0.9, 0.5]  # Sample danceability scores
plt.bar(range(len(danceability)), danceability)
plt.title("Danceability of Playlist Songs")
plt.xlabel("Song Index")
plt.ylabel("Danceability Score")
plt.show()
```

#### **Activity:**  
🛠️ Students:  
   - Fetch their **Spotify playlists** and analyze track details.  
   - Find their **most danceable or energetic song** in the playlist.  
   - Plot a **graph of tempo vs danceability**.  

