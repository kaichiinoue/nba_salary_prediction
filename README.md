![](/image/nba_logo.png)
# NBA players salary prediction: Overview
- Built a model that can predict NBA players salaries based on their performances in the last season.
- Web scraped all the players stats from a website called [Basketball-Reference](https://www.basketball-reference.com/) and [HOOPSHYPE](https://hoopshype.com/salaries/players/2020-2021/)

## jump to each jupyter notebook
- [Web scraping](https://github.com/kaichiinoue/nba_salary_prediction/blob/eda/webscraper.ipynb)
- [Data cleaning](https://github.com/kaichiinoue/nba_salary_prediction/blob/eda/data_cleaning.ipynb)
- [EDA](https://github.com/kaichiinoue/nba_salary_prediction/blob/main/eda.ipynb)
- Model building

## motivation
There are some superstarts in NBA who earn crazy amount of money every year. As a huge basketball fan, I got to think whether their performances from the last season is the pure factors that determine their salary of the next season. 

## Web Scraping
Webscraped all the palyers data from a website called [Basketball-Reference](https://www.basketball-reference.com/), a site that has all data of professional basketball including not only NBA but also G League and WNBA. For salary information, there was a problem with getting salary data from Basketball Reference, so I used another website called [HOOPSHYPE](https://hoopshype.com/salaries/players/2020-2021/) to get salary data for every player.
As a stat for each player, we got the following:
- Pos (Position)
- Age (Player's age on February 1st of the season)
- Tm (Team)
- G (Games)
- GS (Games that a player was in starting member)
- MP (Minutes played)
- FG (Field Goals)
- FGA (Field Goals Attempts)
- FG% (Field Goals Percentage)
- 3P (3-Points Field Gaols)
- 3PA (3-Points Field Goals Attempts)
- 3P% (3-Points Field Goals Percentage)
- 2P (2-Points Field Gaols)
- 2PA (2-Points Field Goals Attempts)
- 2P% (2-Points Field Goals Percentage)
- eFG% (Effective Field Goals Percentage)
- FT (Free Throws)
- FTA (Free Throws Attempts)
- FT% (Free Throws Percentage)
- ORB (Offensive Rebounds)
- DRB (Defensive Rebounds)
- TRB (Total Rebounds)
- AST (Assits)
- STL (Steals)
- BLK (Blocks)
- TOV (Turnovers)
- PF (Personal Fouls)
- PTS (Points)
- Salary
## Data Cleaning
Before doing some EDA, I needed to do some data cleaning. To-Dos are the followings:
- Deal with columns with missing values: columns with missing values - 'FG%', '3P%', '2P%', 'eFG%', 'FT%', 'Salary'
- Take out the $ sign from Salary column
- There are several players with two positions so replace them with single position, so choose the first position appears for Pos column
- There are players who play in multiple teams during a season. Delete the rows for different teams and keep a row which 'Tm' column has value 'TOT' because that aggregates the information of stats for both team.
<br />(The order here is not the order I cleaned each column)
- get rid of comma from Salary column

## EDA
![](/image/graph1.png)
![](/image/graph2.png)


## Model

## Model Performance
