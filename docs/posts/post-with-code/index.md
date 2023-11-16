# Classification of Spotify songs into genres
Shrikar Banagiri
2023-11-11

- [**Introduction**](#introduction)
- [Importing the dataset](#importing-the-dataset)

## **Introduction**

This [Spotify song
dataset](https://www.kaggle.com/datasets/joebeachcapital/30000-spotify-songs/?select=spotify_songs.csv)
contains 30,000 songs from artists of different genres. Each song has
specific attributes which help the user discern its genre. These
attributes include `danceability`, `energy`, `loudness`, `key`, `mode`,
`speechiness`, `acousticness`, `instrumentalness`, `liveness`,
`valence`, and `tempo`.

The problem statement is to classify the songs (based on the above
attributes) into six genres: `pop`, `rock`, `latin`, `EDM`, `rap`, and
`R&B`.

## Importing the dataset

First, we import the libraries required to perform the initial data
analysis. The dataset, hosted on [Kaggle](https://www.kaggle.com/), is
imported and stored in the variable `spotify_songs`.

``` python
# Import the libraries

import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
import urllib.request
from pathlib import Path
import os
import zipfile

# Downloading and opening the dataset

csv_path = Path('datasets/archive.zip') # store the dataset in a local folder
url = 'https://www.kaggle.com/datasets/joebeachcapital/30000-spotify-songs/download?datasetVersionNumber=2' # url to download the dataset

if not csv_path.is_file(): # check if the dataset directory exists. 
  Path("datasets").mkdir(parents=True,exist_ok=True) # Create the directory
  urllib.request.urlretrieve(url, csv_path)
  with zipfile.ZipFile(csv_path) as spotify_file:
    spotify_file.extractall(path='datasets')
    
spotify_songs = pd.read_csv(Path('datasets/spotify_songs.csv')) # Store the dataset in a variable
```
