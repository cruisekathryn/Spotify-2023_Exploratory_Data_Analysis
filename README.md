<p align="center">
  <img src="https://github.com/user-attachments/assets/a6d3ebe0-a6f5-4d3d-9700-50b0e80008ff" alt="Header"/>
</p>  

# **Exploratory Data Analysis on Most Streamed Spotify Songs 2023 Dataset**

## **Introduction**
Exploratory Data Analysis (EDA) is essential for understanding the relationships among different attributes and recognizing important variables within a dataset. It helps visualize the most significant aspects of the data, which supports making informed decisions regarding selecting an appropriate solution.

In this project, we will delve deeper into the Exploratory Data Analysis performed on '**Most Streamed Spotify Songs 2023 Dataset**' which is available on [Kaggle](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023). As stated in the Dataset Description on Kaggle:
> "This dataset contains a comprehensive list of the most famous songs of 2023 as listed on Spotify. The dataset offers a wealth of features beyond what is typically available in similar datasets. It provides insights into each song's attributes, popularity, and presence on various music platforms. The dataset includes information such as **track name, artist(s) name, release date, Spotify playlists and charts, streaming statistics, Apple Music presence, Deezer presence, Shazam charts, and various audio features.**"

The objective of this analysis is to **analyze, visualize, and interpret the data** to extract meaningful insights.  <br />

<p align="center">
  <img src="https://github.com/user-attachments/assets/01321be0-dcfa-40dc-90c4-c7034e978c7b" alt="Music Notes"/>
</p>  

## Most Streamed Spotify Songs 2023 Dataset Overview
This part presents the overview of the **Most Streamed Spotify Songs 2023 Dataset Overview** including the number of rows and columns that the dataset contains. The data type of each column is also stated in this part. Moreovr, existence of missing values are also checked.  

### <ins>A. Importing Libraries and Accessing .csv File</ins>
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

### <ins>B. Number of Rows and Columns</ins>
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
### <ins>C. Checking of Data Type and Missing Values</ins>
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

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Basic Descriptive Statistics
This part provides the basic descriptive statistics of the Spotify Dataset. First, the mean, median, and standard deviation of the 'streams' column were calculated in order to gain an understanding on the central tendency of the data. The distribution of the 'released_year' and 'artist_count' columns were also examined to identify trends and patterns within the dataset.

### <ins>A. Mean, Median, and Standard Deviation of the Streams</ins>
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

### <ins>B. Distribution of Released Year and Artist Count<ins>
Similar to how the was treated in the previous part, the columns in this section will also be converted to numeric.
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

### _**Key Observations**_

In the resulting values of mean and median, it can be observed that differences between the mean and median values suggests a skewed distribution of streams. This sometimes occurs when few tracks receive an exceptionally high number of streams, pulling the mean higher, while those tracks that receive relatively lower streams remain in the middle value, thus the median. It is also noticeable that the value of the standard deviation is also large, which signifies a more spread out data around the mean. This indicates that the tracks vary widely in popularity.

The histogram of 'Distribution of Release Year' shows a large increase in tracks starting the year 2020. This suggests that there was a significant concentration of tracks releases in the 2020s while the earlier years have low frequencies potentially due to smaller audiences and less platforms.

Furthermore, the histogram of 'Distribution of Artist Count' shows that majority of th tracks released involve single artists. A significant amount of track releases can also be seen around two and three artists. Meanwhile, for tracks with four to eight artists, the frequency is very low. This distribution highlights a trend towards solo artist and small groups and less tracks on bigger groups.

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p>

## Top Performers

This part presents the top performers in the dataset. First, tracks with the highest number of streams were examined. Then, the top five most frequent artists are identified based on their respective number of tracks in th dataset. These insights will be helpful in understanding musical preferences.

### <ins>A. 5 Most Streamed Tracks</ins>
Sorting will be necessary in this given scenario. Using the function `.sort_value()`, the spotify tracks will be sorted according to desired order. In this case, the dataset should be in a descending order.
```python
# Sort the spotify data from highest to lowest
sorted_tracks = spotify_data.sort_values(by='streams', ascending=False)

# Display the top 5 most streamed tracks
top_5_tracks = sorted_tracks.head()
top_5_tracks.loc[:,['track_name','artist(s)_name','streams']]
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/e1ac4385-e94a-4808-afb2-636b45c5737b" alt="5 Most Streamed Tracks"/>
</p>  

### <ins>B. 5 Most Frequent Artists Based on Tracks Count</ins>
The dataset contains solo artists and multiple artists. To count all tracks, it is necessary to separate the multiple artists into solo artists before counting and sorting the track count. `.str` and `.split()` are simultaneously used to perform the separation process. Other functions used include `.explode()`, `.value_counts()`, and `.head()`.
```python
# Split artist(s)_name into lists of artists for tracks with multiple artists
artist_data = spotify_data['artist(s)_name'].str.split(', ')

# Explode the lists into separate rows
exploded_data = artist_data.explode().value_counts().head()

# Convert the Series to a DataFrame
top_5_artists = exploded_data.reset_index()
top_5_artists.columns = ['Artist', 'Track Count']

top_5_artists
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/1400648f-c6a6-4175-ba7d-7c04829f3837" alt="5 Most Frequent Artists"/>
</p>  

### _**Key Observations**_  
The data suggests that there is little to no relationship between the most streamed tracks and the most frequent artists, except for The Weeknd. It shows that the number of tracks does not guarantee a spot in the top streams. Nevertheless, 'Blinding Lights' by The Weeknd ranked first in the most streamed track, and Bad Bunny leads in the most frequent artists based on tracks with his 40 track releases.

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 


## Temporal Trends

This part examines the temporal trends in music releases in the industry over time. The number of tracks released per year is plotted in this section. The number of releases per month is also observed to highlight any particular pattern that may stand out. This analysis can help uncover whether certain times of the year consistently see higher activity in music releases.

### <ins>A. Tracks Released per Year</ins>
A new dataframe is created in this section by grouping two columns, 'released_year' and 'track_count', to show the number of tracks released each year.
```python
# Group by release_year and count the number of tracks
tracks_per_year = spotify_data.groupby('released_year').size().reset_index(name='track_count')

# Create a bar plot to trace the trends over time
plt.figure(figsize=(10, 6))
sns.barplot(data=tracks_per_year, x='released_year', y='track_count', color='darkblue')
plt.title("Number of Tracks Released per Year")
plt.xlabel("Year")
plt.ylabel("Number of Tracks")
plt.xticks(rotation=90)
plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/c031296b-f7c9-465d-b077-0a67f398c335" alt="Number of Tracks Released per Year"/>
</p> 


### <ins>B. Tracks Released per Month</ins>
Similar to the previous section, a new dataframe is created in this section by grouping two columns, 'released_month' and 'track_count', to show the number of tracks released each month.
```python
# Group by release_year and count the number of tracks
tracks_per_month = spotify_data.groupby('released_month').size().reset_index(name='track_count')

# Create a bar plot to trace the trends over time
plt.figure(figsize=(10, 6))
sns.barplot(data=tracks_per_month, x='released_month', y='track_count', color='skyblue')
plt.title("Number of Tracks Released per Month")
plt.xlabel("Month")
plt.ylabel("Number of Tracks")
plt.xticks(rotation = 45, ticks=range(12), labels=['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'])
plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/77bfd4f4-e814-4cc2-ac88-479c0a090716" alt="Number of Tracks Released per Month"/>
</p> 

### _**Key Observations**_  

The first bar chart, titled "Number of Tracks Released per Year," shows a significant increase in the number of tracks released over recent years. The year 2022 peaks with the highest number of tracks, followed by years 2023 and 2022. This trend likely reflects the rise in digital music production and streaming platforms, which have made it easier for artists to publish music. This may also be influenced by the COVID-19 pandemic as artists had more time to release tracks.

The second bar chart, titled "Number of Tracks Released per Month," reveals seasonal patterns in music releases. January and May is shown to have the highest number of tracks relases, while August have relatively fewer releases. This suggests a trend of peak streaming periods at the beginning of the year and the start of summer.

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Genre and Music Characteristics
This part examines the correlation between streams and musical attributes like beats per minute (BPM), danceability, and energy to observe attributes that influence streams the most. Additionally, a correlation between different musical attributes like danceability, energy, valence, and acousticness.

### <ins>A. Correlation between Streams and Musical Attributes</ins>
Cleaning the data in this section is essential to ensure that the correlation between the streams and attributes will be accurately calculated. 
```python
# Convert columns to numeric, coercing errors to NaN
columns_to_convert = ['streams', 'bpm', 'danceability_%', 'valence_%', 'energy_%', 'acousticness_%', 'instrumentalness_%', 'liveness_%', 'speechiness_%']
for col in columns_to_convert:
    spotify_data[col] = pd.to_numeric(spotify_data[col], errors='coerce')
    
# Correlation between streams and musical attributes
correlation = spotify_data[columns_to_convert].corr()

# Heat map of the correlation between streams and musical attributes
plt.figure(figsize=(8, 6))
sns.heatmap(correlation, annot=True, cmap='coolwarm', center=0)
plt.title('Correlation between Streams and Musical Attributes')
plt.xticks(rotation=45)
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/4113da52-eccd-4ca5-803d-d7ab74d2e722" alt="Correlation between Streams and Musical Attributes"/>
</p> 

### <ins>B. Correlation between 'Danceability and Energy' and 'Valence and Acousticness'
The correlation between the musical attributes revealed in the previous section a positive correlation between danceability and energy with a correlation value of 0.2. On the other hand, it was revealed that there is a negative correlation between valence and acousticness with a correlation value of -0.081. To further analyze the data, scatter plots are plotted.

```python
# Set up the figure grid for scatter plots
fig, axes = plt.subplots(1, 2, figsize=(20,6))
fig.suptitle('Scatter Plots of Various Musical Attributes', fontsize=23)

# Scatterplot to visualize correlation between danceability_% and energy_%
sns.scatterplot(data=spotify_data, x='danceability_%', y='energy_%', ax=axes[0], color='green')
axes[0].set_title('Danceability vs. Energy', fontsize = 20)
axes[0].set_xlabel('Energy (%)')
axes[0].set_ylabel('Danceability (%)')

# Scatterplots to visualize correlation between valence_% and acousticness_%
sns.scatterplot(data=spotify_data, x='valence_%', y='acousticness_%', ax=axes[1], color='orange')
axes[1].set_title('Acousticness vs. Valence', fontsize = 20)
axes[1].set_xlabel('Acousticness (%)')
axes[1].set_ylabel('Valence (%)')

plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/3d02fc6d-4313-41f1-897b-339deffd9e91" alt="Scatter Plots of Streams vs. Musical Attributes"/>
</p> 

### _**Key Observations**_  

The heatmap shows the correlation between streams and musical attributes. It reveals that all musical attributes have a negative correlation with the number of streams. However, it can be observed that BPM and acousticness have the highest values of correlation among all the given musical attributes, indicating that these factors still have an impact on streaming popularity, albeit small.

On the other hand, danceability and energy revealed a correlation value of 0.2 which indicates a weak positive relationship. This means that songs with generally higher danceability tends to have higher energy. Simply said, tracks suitable for dancing are more intense and active.

Furthermore, valence and acousticness revealed a correlation value of -0.081 indicating a weak negative relationship. This means that songs with generally higher valence will have slightly lower acousticness. However, it's important to note that this relationship is very weak and many exceptions to this trend likely exist.

Some worth noting relationships includes **danceability and valence** and **valence and energy** with a moderately positive correlation of 0.41 and 0.46 respectively. Conversely, the relationship between **energy and acousticness** shows a moderate negative correlation with a correlation value of -0.58.

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Platform Popularity
This part examines the popularity of tracks across different streaming platforms like Spotify, Deezer, and Apple Music playlists. The number of playlists in each platform will be counted to identify which platforms favor the most popular tracks.

### <ins>Comparison of Track Counts Across Spotify, Deezer, and Apple Music</ins>
Data cleaning is essential in this section to ensure that the data to be plotted will be accurate. A bar plot is used to visualize the comparison of data across the different platforms.
```python
# Attempt to convert columns to numeric, setting errors='coerce' to convert non-numeric values to NaN
for column in ['in_spotify_playlists', 'in_apple_playlists', 'in_deezer_playlists']:
    spotify_data[column] = pd.to_numeric(spotify_data[column], errors='coerce')

# Sum of tracks on different platforms
platform_popularity_data = spotify_data[['in_spotify_playlists', 'in_apple_playlists', 'in_deezer_playlists']].sum().reset_index()

# Renaming for better clarity
platform_popularity_data.columns = ['platform', 'track_count']

# Plotting the comparison on Spotify Playlists, Deezer Playlists, and Apple Playlists
plt.figure(figsize=(8, 5))
sns.barplot(data=platform_popularity_data, x='platform', y='track_count')
plt.title("Comparison of Track Counts Across Spotify, Deezer, and Apple Music")
plt.xlabel("Platform")
plt.ylabel("Number of Tracks")
plt.xticks(ticks = range(3), labels = ['Spotify Playlists','Deezer Playlists', 'Apple Playlists'])
plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/0c55b6d7-91b0-4109-a45f-d72e6aa0b6e2" alt="Comparison of Track Counts Across Spotify, Deezer, and Apple Music"/>
</p> 

### _**Key Observations**_  
Spotify is a clearly dominates the Deezer and Apple Music based on the number of playlists. This suggests that Spotify has a more extensive and diverse range of playlists where a larger user base might be a strong factor.  While Deezer and Apple Music may be good in other aspects, Spotify's extensive playlist library makes it the leading platform for music discovery and consumption.

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Advanced Analysis
This part explores the potential patterns among tracks with the same key or mode (major vs. minor) and its streaming performance. Additionally, genres or artists that consistently appears in playlists and charts will be identified. An analysis will also be performed to compare the most frequently featured artists across various playlists and charts.

### <ins>A. Average Streams by Musical Key</ins>
A new dataframe is created in this section by grouping column 'key' and selecting only the 'streams' column from the grouped data. The average streams will then be calculated. The key_streams will result to a dataframe with two columns. A bar plot is used to visualize the data.
```python
# Mean of streams grouped by key
key_streams = spotify_data.groupby('key')['streams'].mean().reset_index()
key_streams.columns = ['Key', 'Average Streams']

# Plot average streams by key using bar plot
plt.figure(figsize=(10, 5))
sns.barplot(data=key_streams, x='Key', y='Average Streams', hue='Key', legend=False, palette='Blues')
plt.title("Average Streams by Musical Key")
plt.xlabel("Musical Key")
plt.ylabel("Average Streams")
plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/ccd236f9-0d29-4694-9d09-13dbe360bed6"/>
</p>

### <ins>B. Average Streams by Mode (Major vs. Minor)
A new dataframe is created in this section by grouping column 'mode' and selecting only the 'streams' column from the grouped data. The average streams will then be calculated. The mode_streams will result to a dataframe with two columns. A bar plot is used to visualize the data.
```python
# Mean of streams grouped by mode
mode_streams = spotify_data.groupby('mode')['streams'].mean().reset_index()
mode_streams.columns = ['Mode', 'Average Streams']

# Plot average streams by mode
plt.figure(figsize=(8, 5))
sns.barplot(data=mode_streams, x='Mode', y='Average Streams', hue='Mode', legend=False, palette=['coral', 'skyblue'])
plt.title("Average Streams by Mode (Minor or Major)")
plt.xlabel("Mode")
plt.ylabel("Average Streams")
plt.tight_layout()
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/7f7babe4-8702-4a53-b5e7-f4ec83f5c6c6" alt="Average Streams by Mode"/>
</p> 

### <ins>C. Average Streams Grouped by Key and Mode</ins>
A new dataframe is created in this section by grouping columns 'mode' and 'key' and selecting only the 'streams' column from the grouped data. The average streams will then be calculated. The mode_streams will result to a dataframe with two columns. A grouped bar plot is used to visualize the data.

```python
# Mean of streams grouped by key and mode
key_mode_streams = spotify_data.groupby(['key', 'mode'])['streams'].mean().reset_index()

# Plotting average streams by key and mode using a grouped bar plot
plt.figure(figsize=(12,5))
sns.barplot(data=key_mode_streams, x='key', hue = 'mode', y='streams', palette = ['skyblue', 'gray'])
plt.title('Average Streams Grouped by Key and Mode')
plt.ylabel('Average Streams')
plt.xlabel('Key and Mode')
plt.legend(title='Mode')
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/1311d423-c5c8-475b-bd7b-ab83da9597bd" alt="Average Streams by Key and Mode"/>
</p> 

### <ins>D. 20 Most Frequently Featured Artists in Playlists and Charts</ins>
A new dataframe is created in this section by first identiifying the columns involving the playlists and charts across various streaming platforms. Then, the dataframe will be grouped by artists and selecting only the columns on playlists and charts. The artist's total appearance will be calculated and sorted in order to identify the most frequently featured artists in playlists and charts. 
```python
# List of the columns that relates to platform appearances
platform_columns = ['in_spotify_playlists', 'in_spotify_charts', 
                    'in_apple_playlists', 'in_apple_charts', 
                    'in_deezer_playlists', 'in_deezer_charts']

# Group by artist(s)_name and sum the values of the platform columns
artist_counts = spotify_data.groupby('artist(s)_name')[platform_columns].sum().sum(axis=1).sort_values(ascending=False)

# Get the top 10 most frequently appearing artists
frequently_appearing = artist_counts.head(20).reset_index()
frequently_appearing.columns = ['Artist', 'Appearances']

# Plotting the top 10 artists
plt.figure(figsize=(14, 7))
sns.barplot(data=frequently_appearing, x='Appearances', y='Artist')
plt.title('20 Most Frequently Featured Artists in Playlists and Charts', fontsize=21)
plt.xlabel('Appearances in Playlists or Charts', fontsize=15)
plt.ylabel('Artist', fontsize=15)
plt.tight_layout() 
plt.show()
```

<p align="center">
  <img src="https://github.com/user-attachments/assets/ea1dcb57-32b1-4a2f-985d-92a9b0da5f26" alt="20 Most Frequently Featured Artists in Playlists and Charts"/>
</p> 

### _**Key Observations**_


<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Conclusion
The Exploratory Data Analysis performed on '**Most Streamed Spotify Songs 2023 Dataset**'


<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Summary of Essential Functions used in the Project
| Functions | Descriptions |
|:---:|---|
| `pd.set_option('display.max_rows', None)` | Displays the max rows |
| `pd.set_option('display.max_columns', None)` | Displays the max columns |
| `pd.read_csv('spotify-2023.csv')` | Reads a .csv file |
| `pd.to_numeric(df['column'], errors='coerce')` | Converts a column to a numeric and errors will be set to NaN |
| `.size()` | Returns the number of elements in given data set |
| `.sum()` | Computes for the sum of the given data set |
| `.shape` | Returns the dimensionality of the DataFrame |
| `.mean()` | Computes for the mean of the given data set |
| `.mode()` | Computes for the mode of the given data set |
| `.std()` | Computes for the standard deviation of the given data set |
| `.corr()` | Computes for the correlation of given columns |
| `.groupby()` | Splits a DataFrame into groups |
| `.info()` | Prints the information about the DataFrame |
| `.isnull()` | Returns a specified value of missing or null values |
| `.sort_values()` | Sorts the DataFrame by specifying the column and order |
| `.head()` | Returns the first five rows |
| `.split()` | Splits a string into a list |
| `.explode()` | Converts each element of a column into a row |
| `.dropna()` | Drops all null values |
| `.reset_index()` | Resets the index of the DataFrame |

<p align="center">
  <img src="https://github.com/user-attachments/assets/47c1f2d6-f32e-4ae9-9616-779921c510f3" alt="Music Notes"/>
</p> 

## Summary of Essential Functions in Visualizing the Plots in the Project
| Functions | Descriptions |
|:---:|---|
| `plt.subplots()` | Initializes a figure and subplot axes |
| `plt.figure()` | Initializes a figure |
| `plt.title()` | Specifies the title of a figure |
| `plt.xlabel` | Specifies the label on the x-axis of the figure |
| `plt.ylabel` | Specifies the label on the y-axis of the figure |
| `plt.tight_layout()` | Minimizes the spacing in the figure layout |
| `plt.show()` | Shows the figure |
| `plt.legend()` | Adds a legend to the figure |
| `plt.xticks()` | Sets tick locations and labels on the x-axis |
| `plt.yticks()` | Sets tick locations and labels on the y-axis |
| `sns.histplot()` | Plots a histogram |
| `sns.barplot()` | Plots a bar plot |
| `sns.heatmap()` | Plots a heatmap |
| `sns.scatterplot()` | Plots a scatter plot |
