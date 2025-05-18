# **Exploratory Data Analysis (EDA) of My Spotify Listening History**
## **1 Introduction**

The present analysis draws upon my own spotify listening data downloaded from Spotify's "Extended Streaming History" request, consisting of JSON files covering the period from 2018 to 2025. Additionay, the main streaming data was combined with my 'liked' playlist data that I downloaded using Exportify, in order to enrich the main dataset with track features such as duration, energy, da,ceability, addition date, etc.

The primary objective of this EDA is to **uncover patterns, anomalies, and potential insights** within my extended listening history. The approach involves understanding the data structure and identifying trends, then generating further questions for deeper analysis based on observed patterns. The process includes data loading, cleaning, feature engineering, performing basic statistics, data aggregation, and visualization.

### **1.1 Purpose of the Analysis**

The analysis aims to address a variety of specific questions and provide insights into different aspects of the listening history. Below is a more readable and organized version of the objectives:

##### **A. Understanding the Dataset**
This section focuses on exploring the structure, quality, and characteristics of the Spotify dataset:
- **Structure and Features**  
  - What is the structure of the downloaded Spotify data (e.g., features, missing values, distributions)?  
  - What is the total number of listening records and features in the dataset?  

- **Data Quality**  
  - Where are the missing values located in the initial data?  
  - How does merging with liked songs data affect the dataset dimensions and missing values?  
  - Which columns are irrelevant for music streaming analysis and should be removed?  
  - What is the impact of data cleaning steps (e.g., dropping rows with missing timestamps or track names) on the dataset size?  

- **Anomalies and Errors**  
  - Are there extremely short playbacks that might indicate logging errors?  
  - Are there instances of implausible playback durations within an hour, suggesting overlapping entries?

 

##### **B. Identifying Temporal Listening Trends**
This section examines how listening behavior evolves over time:
- **Yearly Trends**  
  - How have total listening hours evolved year-over-year?  
  - Which year was the most active for listening?  

- **Monthly Trends (2020)**  
  - How did listening vary month-to-month in the most active year (2020)?  
  - Which months had the most listening in 2020?  
  - Were there seasonal patterns or spikes in 2020 listening?  
  - How evenly was Spotify used throughout 2020?  

- **Monthly Trends (All Years)**  
  - How does listening behavior vary by month when aggregating data from all years?  
  - Are there consistent seasonal patterns in listening across multiple years?  
  - How does monthly listening compare when averaged across multiple years?  
  - How did monthly listening habits change year-over-year from 2018 to 2025?  
  - Did the same months consistently stand out for listening each year?  

- **Daily and Hourly Patterns**  
  - How does listening activity distribute across the days of the week?  
  - Which hours of the day have the peak engagement periods?  
  - Which hours have the lowest listening frequency?  

- **Sequential Analysis**  
  - What long-term trends are visible when viewing listening hours sequentially by month (`month_sequential_n`)?  
  - What short-term fluctuations and patterns are evident when viewing listening hours sequentially by day (`day_sequential_n`)?  
  - What patterns exist when viewing listening hours sequentially by hour (`hour_sequential_n`)?


##### **C. Investigating Song Curation Habits**
This section explores how new songs were added to the liked songs library:
- **Timeline of Additions**  
  - When were new songs added to the liked songs library?  
  - Which years saw the most song additions?  

- **Monthly and Yearly Rates**  
  - What was the rate of new song additions by month for each year?  

- **Genre Analysis (2022)**  
  - What genres were most represented in the new songs added in 2022?  

- **Overall Statistics**  
  - What are the overall statistics (total, max, min, mean, std) for new songs added per month across all years?  

- **Curation Spikes**  
  - Are there specific periods (e.g., certain months or years) that show intense curation spikes or declines?

##### **D. Analyzing Genre and Artist Preferences**
This section dives into genre and artist preferences based on listening behavior:
- **Genre Preferences**  
  - Which music genres have been listened to the most based on total hours played?  
  - How diverse or focused is the overall music taste?  
  - How much time was spent listening to the top genres?  

- **Artist Contributions**  
  - Which artists contributed most to the listening time in the top genre ("post-rock, dream pop")?  
  - Which specific tracks by the dominant artist (Sigur Rós) in that genre were listened to most?  

- **Artist Rankings**  
  - Which artists have been listened to the most based on total playback hours?  
  - Which artists have been played most frequently based on play count?  
  - How do artists compare in terms of total playback hours vs. play count?
##### **E. Understanding Song Engagement and Popularity**
This section identifies the most popular and frequently played songs:
- **Most Played Songs**  
  - Which songs are the most frequently played?  
  - Which songs have been played across the most unique years?  
  - Which songs have been played on the most unique days?  
  - Which songs have appeared in the most unique hourly listening sessions?  

- **Peak Engagement Hours**  
  - What are the peak hours of the day for the top 3 most engaged songs?
### **1.2 Dataset Overview** 
- **Source**: Downloaded from [Spotify's "Extended Streaming History" data request](https://www.spotify.com/us/account/privacy/). and Exportify website.
- **Format**: The main streeming dataset is in JSON format (`endsong_*.json`) while the liked playlist is a csv file.
- **Period**: 2018-2025
- **Expected Variables**:  
  - Timestamps, track/artist names, play duration, skipped tracks, etc.  

### **1.3. Approach** 
The workflow for the exploratory data analysis (EDA) of the Spotify listening history begins by **loading and combining multiple JSON files containing streaming data from 2018 to 2025 into a single dataset**. Initial data inspection involves checking dimensions and identifying missing values, followed by **cleaning steps such as removing irrelevant podcast/audiobook columns** **and dropping rows with missing timestamps or track names**. The dataset is then **merged with liked songs data**, and **features are engineered to extract time-based information, calculate play metrics, and add sequential temporal identifiers**. Further data quality checks include filtering out extremely short playbacks and addressing anomalies like overlapping entries, before proceeding with various analyses on listening patterns by time, artists, genres, and song engagement.
