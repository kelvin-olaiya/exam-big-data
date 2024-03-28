# Big data Project @ UniBo a.y. 2023/2024

## Project Description

The project is based on [Spotify Million Playlist Dataset Challenge](https://www.aicrowd.com/challenges/spotify-million-playlist-dataset-challenge).

## Preprocessing

### Normalization and JSON to CSV

The first step of the preprocessing is to normalize the `JSON` files and convert them to `CSV` files. The normalization is done by `preprocessing.ipynb` that takes as input the JSON files and outputs the normalized CSV files.

In addition many properties are discarded during the process.

This is the *E/R* schema of the dataset:

```mermaid
erDiagram
    Track {
        string uri PK
        string name
        int duration
        string artist_uri FK
        string album_uri
        string album_name
    }
    Playlist {
        int pid PK
        string name
        int num_followers
    }
    Track_in_Playlist {
        int pid PK, FK
        string track_uri PK, FK
        int pos PK
    }
    Artist {
        string uri PK
        string name
    }

    Track only one to zero or more Track_in_Playlist : in
    Playlist only one to zero or more Track_in_Playlist : in
    Track zero or more to only one Artist : write
```
