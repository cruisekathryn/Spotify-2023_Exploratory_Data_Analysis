# **Exploratory Data Analysis on Spotify 2023 Dataset**

## **Introduction**
Exploratory Data Analysis (EDA) is essential for understanding the relationships among different attributes and recognizing important variables within a dataset. It helps visualize the most significant aspects of the data, which supports making informed decisions regarding selecting an appropriate solution.

In this project, we will delve deeper into the Exploratory Data Analysis performed on '**Most Streamed Spotify Songs 2023 Dataset**' which is available on [Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023). As stated in the Dataset Description on Kaggle:
> "This dataset contains a comprehensive list of the most famous songs of 2023 as listed on Spotify. The dataset offers a wealth of features beyond what is typically available in similar datasets. It provides insights into each song's attributes, popularity, and presence on various music platforms. The dataset includes information such as **track name, artist(s) name, release date, Spotify playlists and charts, streaming statistics, Apple Music presence, Deezer presence, Shazam charts, and various audio features.**"

The objective of this analysis is to **analyze, visualize, and interpret the data** to extract meaningful insights.  <br />

## Most Streamed Spotify Songs 2023 Dataset Overview
This section presents the overview of the **Most Streamed Spotify Songs 2023 Dataset Overview** including the number of rows and columns that the dataset contains. The data type of each column is also stated in this section. Moreovr, existence of missing values are also checked.  
### A. Importing Libraries and Accessing .csv File
To start, we import the necessary libraries in manipulating the data and adding visualizations.
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```
We will then access the .csv file downloaded from Kaggle.
> [!CAUTION]
> Some .csv files are not written in the same encoding as Jupyter Notebook. In such cases, we may change the encoding by opening the .csv file on Notepad and saving it with the encoding 'UTF-8' which is compatible with Python 3.
```python
spotify_data = pd.read_csv('spotify-2023.csv')
spotify_data
```
<p align="center">
  <img src="https://github.com/user-attachments/assets/21c3118d-a71a-4e1f-9082-c0214692cf29" alt="Spotify 2023 Dataset"/>
</p>  

To show all rows and columns, the following commands may be implemented.
```python
pd.set_option('display.max_rows', None)
pd.set_option('display.max_columns', None)
```
<p align="center">
  <img src="https://github.com/user-attachments/assets/ca9ccd41-463d-465f-8c7a-e1d21f6afc24" alt="Spotify 2023 Complete Dataset"/>
</p>  

### C. Number of Rows and Columns
The number of rows and columns may be identified by using the `.shape` function.
```python
rows, columns = spotify_data.shape
print(f'Number of rows: {rows}')
print(f'Number of columns: {columns}')
```
The output for this code block is as follows.
```
Number of rows: 953
Number of columns: 24
```
### D. Checking of Data Type and Missing Values
To properly analyze the dataset, verifying the data typees and checking of missing values will be essential.
```python
print(spotify_data.info())
```
```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 953 entries, 0 to 952
Data columns (total 24 columns):
```

| #  |  Column              | Non-Null Count | Dtype  |
|:--:| :------              | :------------: | :----: |
| 0  | track_name           | 953 non-null   | object |
| 1  | artist(s)_name       | 953 non-null   | object |
| 2  | artist_count         | 953 non-null   | int64 |
| 3  | released_year        | 953 non-null   | int64 |
| 4  | released_month       | 953 non-null   | int64 |
| 5  | released_day         | 953 non-null   | int64 |
| 6  | in_spotify_playlists | 953 non-null   | int64 |
| 7  | in_spotify_charts    | 953 non-null   | int64 |
| 8  | streams              | 953 non-null   | object |
| 9  | in_apple_playlists   | 953 non-null   | int64 |
| 10 | in_apple_charts      | 953 non-null   | int64 |
| 11 | in_deezer_playlists  | 953 non-null   | object |
| 12 | in_deezer_charts     | 953 non-null   | int64 |
| 13 | in_shazam_charts     | 903 non-null   | object |
| 14 | bpm                  | 953 non-null   | int64 |
| 15 | key                  | 858 non-null   | object |
| 16 | mode                 | 953 non-null   | object |
| 17 | danceability_%       | 953 non-null   | int64 |
| 18 | valence_%            | 953 non-null   | int64 |
| 19 | energy_%             | 953 non-null   | int64 |
| 20 | acousticness_%       | 953 non-null   | int64 |
| 21 | instrumentalness_%   | 953 non-null   | int64 |
| 22 | liveness_%           | 953 non-null   | int64 |
| 23 | speechiness_%        | 953 non-null   | int64 |
