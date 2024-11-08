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
The output for this code block is as follows:
```
Number of rows: 953
Number of columns: 24
```
### D. Checking of Data Type and Missing Values
To properly analyze the dataset, verifying the data types and checking of missing values will be essential.
```python
print('Overview of the Spotify Data Information:\n')
print(spotify_data.info())
```
The output for this code block is as follows:
```python
Overview of the Spotify Data Information:

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 953 entries, 0 to 952
Data columns (total 24 columns):
 #   Column                Non-Null Count  Dtype 
---  ------                --------------  ----- 
 0   track_name            953 non-null    object
 1   artist(s)_name        953 non-null    object
 2   artist_count          953 non-null    int64 
 3   released_year         953 non-null    int64 
 4   released_month        953 non-null    int64 
 5   released_day          953 non-null    int64 
 6   in_spotify_playlists  953 non-null    int64 
 7   in_spotify_charts     953 non-null    int64 
 8   streams               953 non-null    object
 9   in_apple_playlists    953 non-null    int64 
 10  in_apple_charts       953 non-null    int64 
 11  in_deezer_playlists   953 non-null    object
 12  in_deezer_charts      953 non-null    int64 
 13  in_shazam_charts      903 non-null    object
 14  bpm                   953 non-null    int64 
 15  key                   858 non-null    object
 16  mode                  953 non-null    object
 17  danceability_%        953 non-null    int64 
 18  valence_%             953 non-null    int64 
 19  energy_%              953 non-null    int64 
 20  acousticness_%        953 non-null    int64 
 21  instrumentalness_%    953 non-null    int64 
 22  liveness_%            953 non-null    int64 
 23  speechiness_%         953 non-null    int64 
dtypes: int64(17), object(7)
memory usage: 178.8+ KB
```

On the other hand, the following code block count the number of null elements in each table.
```python
print('\nTotal number of missing values: \n\n', spotify_data.isnull().sum())
```

The output for this code block is as follows:
```python
Total number of missing values:
 
track_name               0
artist(s)_name           0
artist_count             0
released_year            0
released_month           0
released_day             0
in_spotify_playlists     0
in_spotify_charts        0
streams                  0
in_apple_playlists       0
in_apple_charts          0
in_deezer_playlists      0
in_deezer_charts         0
in_shazam_charts        50
bpm                      0
key                     95
mode                     0
danceability_%           0
valence_%                0
energy_%                 0
acousticness_%           0
instrumentalness_%       0
liveness_%               0
speechiness_%            0
dtype: int64
```

For better viewing, you may view it in the summarized table below.

| #  |  Column              | Non-Null Count | Null Count | Data Type  |
|:--:| :------              | :------------: | :----: | :------------: | 
| 0  | track_name           | 953 non-null   |  0  | object |
| 1  | artist(s)_name       | 953 non-null   |  0  | object |
| 2  | artist_count         | 953 non-null   |  0  | int64 |
| 3  | released_year        | 953 non-null   |  0  | int64 |
| 4  | released_month       | 953 non-null   | 0  |  int64 |
| 5  | released_day         | 953 non-null   |  0  | int64 |
| 6  | in_spotify_playlists | 953 non-null   |  0  | int64 |
| 7  | in_spotify_charts    | 953 non-null   |  0  | int64 |
| 8  | streams              | 953 non-null   |  0  | object |
| 9  | in_apple_playlists   | 953 non-null   |  0  | int64 |
| 10 | in_apple_charts      | 953 non-null   |  0  | int64 |
| 11 | in_deezer_playlists  | 953 non-null   |  0  | object |
| 12 | in_deezer_charts     | 953 non-null   | 0  |  int64 |
| 13 | in_shazam_charts     | 903 non-null   |  50  | object |
| 14 | bpm                  | 953 non-null   |  0  | int64 |
| 15 | key                  | 858 non-null   | 95  | object |
| 16 | mode                 | 953 non-null   |  0  | object |
| 17 | danceability_%       | 953 non-null   |  0  | int64 |
| 18 | valence_%            | 953 non-null   |  0  | int64 |
| 19 | energy_%             | 953 non-null   |  0  | int64 |
| 20 | acousticness_%       | 953 non-null   |  0  | int64 |
| 21 | instrumentalness_%   | 953 non-null   |  0  | int64 |
| 22 | liveness_%           | 953 non-null   |  0  | int64 |
| 23 | speechiness_%        | 953 non-null   | 0  |  int64 |

## Basic Descriptive Statistics
This section provides the basic descriptive statistics of the Spotify Dataset. First the mean, median, and standard deviation of the 'streams' column were calculated in order to gain an understanding on the central tendency of the data. The distribution of the 'released_year' and 'artist_count' columns were also examined to identify trends and patterns within the dataset.

### A. Mean, Median, and Standard Deviation of the Streams
Before calculating the mean, median, and standard deviation, it is crucial to clean the data to avoid inaccuracies in the values. To do so, the 'streams' column shall be converted to numeric.
```python
# Convert 'streams' column to numeric
spotify_data['streams'] = pd.to_numeric(spotify_data['streams'], errors='coerce')

# Remove rows where 'streams' is not convertible to a number
spotify_data = spotify_data.dropna(subset=['streams'])
```

After cleaning the data, the calculation for mean, median, and standard deviation may now proceed. The code block is as follows:

```python
mean_streams = spotify_data['streams'].mean()
median_streams = spotify_data['streams'].median()
std_streams = spotify_data['streams'].std()

print(f'Mean: {mean_streams}')
print(f'Median: {median_streams}')
print(f'Standard Deviation: {std_streams}')
```
The resulting values are:
```python
Mean: 514137424.93907565
Median: 290530915.0
Standard Deviation: 566856949.0388832
```
### B. Distribution of Released Year and Artist Count
Similar to how the was treated in the previous section, the columns in this section will also be converted to numeric.
```python
# Convert 'artist_count' and 'released_year' columns to numeric
for column in ['artist_count', 'released_year']:
    spotify_data[column] = pd.to_numeric(spotify_data[column], errors='coerce')

# Remove rows where 'artist_count' and 'released_year' are not convertible to a number
spotify_data = spotify_data.dropna(subset=['released_year', 'artist_count'])
```

After cleaning the data, the plot can now be created using the following commands.

```python
# Create a figure with two subplots side by side
fig, axes = plt.subplots(1, 2, figsize=(14, 6))

# Plot histogram for 'released_year' on the first subplot
sns.histplot(spotify_data['released_year'], bins=20, kde=True, ax=axes[0], color='lightgreen')
axes[0].set_title("Distribution of Release Year")
axes[0].set_xlabel("Release Year")
axes[0].set_ylabel("Frequency")

# Plot histogram for 'artist_count' on the second subplot
sns.histplot(spotify_data['artist_count'], bins=10, kde=True, ax=axes[1], color='pink')
axes[1].set_title("Distribution of Artist Count")
axes[1].set_xlabel("Artist Count")
axes[1].set_ylabel("Frequency")

# Adjust layout for better spacing
plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/2350414b-c321-46e5-8ada-472b52812272" alt="Number of Tracks Released per Month"/>
</p>  



## Summary of Essential Functions used in this Project
| Functions | Description |
| :--: | :--- |
| `pandas.DataFrame.space` | Returns the dimensionality of the data frame |
