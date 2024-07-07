# Spotify Power BI Analysis

## Overview

This project is a comprehensive analysis of a real-world Spotify dataset using Power BI. The objective was to clean the data, create calculated measures, and develop insightful visualizations to understand the performance of explicit and non-explicit songs on Spotify.

## Project Highlights

- **Data Cleaning**: Addressed unrecognized characters and mixed date formats to ensure accurate analysis.
- **Calculated Measures**: Created various metrics to analyze song performance, including total views, average views per song, and more.
- **Visual Insights**: Developed interactive dashboards showcasing top artists, albums, and track popularity.

## Data Cleaning Process

Data cleaning was a crucial part of this project to ensure the accuracy and reliability of the analysis. The following steps were taken:

1. **Unrecognized Characters**: Cleaned artist names to remove any unrecognized characters that could interfere with data processing.
2. **Date Formatting**: Fixed mixed date formats by creating helper columns:
   - Separated dates in MM/DD/YYYY format.
   - Extracted and rearranged day and month components to standardize to DD/MM/YYYY.

### Date Formatting Steps:

- **Helper Column 1**: `=IF(ISNUMBER(SEARCH("/", D2)), 1, D2)` to identify dates in MM/DD/YYYY format.
- **Helper Column 2**: `=IF(E2=1, MID(D2, 1, FIND("/", D2) - 1), D2)` to extract the day component.
- **Helper Column 3**: `=IF(E2=1, MID(D2, FIND("/", D2) + 1, FIND("/", D2, FIND("/", D2) + 1) - FIND("/", D2) - 1), D2)` to extract the month component.
- **Helper Column 4**: `=IF(E2=1, CONCAT(G2, "/", F2, "/", RIGHT(D2, 4)), D2)` to concatenate day, month, and year in DD/MM/YYYY format.

## Calculated Measures

- **% of Explicit Songs**: `[Total Explicit Song Count] / [Total Explicit + Non Explicit Count] * 100`
- **% of Explicit Song Views**: `[Explicit Song Spotify Views] / [Explicit + Non Explicit Song Views] * 100`
- **Average View Per Explicit Song**: `[Explicit Song Spotify Views] / [Total Explicit Song Count]`
- **Average Views per Non-Explicit Song**: `[Total Non-Explicit Song View] / [Total Non-Explicit Song Count]`
- **Explicit + Non Explicit Song Views**: `[Explicit Song Spotify Views] + [Total Non-Explicit Song View]`
- **Explicit Song Spotify Views**: `CALCULATE([Total Spotify Views], Sheet1[Explicit Track] = 1)`
- **Total Explicit + Non Explicit Count**: `[Total Explicit Song Count] + [Total Non-Explicit Song Count]`
- **Total Explicit Song Count**: `CALCULATE(COUNTA(Sheet1[Track]), Sheet1[Explicit Track] = 1)`
- **Total Non-Explicit Song Count**: `CALCULATE(COUNTA(Sheet1[Track]), Sheet1[Explicit Track] = 0)`
- **Total Non-Explicit Song View**: `CALCULATE([Total Spotify Views], Sheet1[Explicit Track] = 0)`
- **Total Playlist Reach**: `SUM(Sheet1[Spotify Playlist Count])`
- **Total Spotify Views**: `SUM(Sheet1[Spotify Streams])`
- **Total Youtube Views**: `SUM(Sheet1[YouTube Views])`

## Visual Insights

- **Top 10 Artists by Popularity**
- **Top 10 Albums by Views**
- **Distribution of Spotify Popularity Index**
- **Views on Songs by Release Year (Line Chart)**
- **Top 5 Explicit Content Songs by Views**
- **Top 10 Tracks by Popularity**

## Summary and Analysis

### Proportions:

- **Percentage of Explicit Song Views**: 36.52%
- **Percentage of Explicit Songs**: 35.90%
- **Percentage of Non-Explicit Song Views**: 63.48%
- **Percentage of Non-Explicit Songs**: 64.10%

### Average Views:

- **Average Views per Explicit Song**: 443 million
- **Average Views per Non-Explicit Song**: 432 million

### Conclusion:

- **Performance Comparison**:
  - Explicit songs have a slightly higher average views per song (443 million) compared to non-explicit songs (432 million).
  - Explicit songs attract more views per song, and their proportion of total views is slightly higher than their proportion of the total number of songs.

## How to Use This Repository

1. Clone the repository.
2. Open the Power BI file to explore the visualizations.
3. Review the data cleaning steps and calculated measures to understand the analysis process.

## Feedback

Your feedback and thoughts are most welcome! Feel free to open an issue or reach out if you have any questions or suggestions.

## Contact

- **Email**: vikassharma.kaushik@gmail.com
- **LinkedIn**: [Vikas Sharma](https://www.linkedin.com/in/vikassharma/)
