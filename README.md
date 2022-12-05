![](/image/nba_logo.png)
# NBA players salary prediction: Project Overview
- Built a model that can predict NBA players salaries based on their performances in the last season.
- Web scraped all the players stats and salary information from a website called [Basketball-Reference](https://www.basketball-reference.com/) and [HOOPSHYPE](https://hoopshype.com/salaries/players/2020-2021/)
- Cleaned stats data so that it is ready to be used for model training
- Optimized Linear and Random Forest Regressors by using RandomizedSearchCV and GridSearchCV to get the best model (failed but tried)

## Jump straight to each jupyter notebook

- [Web scraping](https://github.com/kaichiinoue/nba_salary_prediction/blob/eda/webscraper.ipynb)
- [Data cleaning](https://github.com/kaichiinoue/nba_salary_prediction/blob/eda/data_cleaning.ipynb)
- [EDA](https://github.com/kaichiinoue/nba_salary_prediction/blob/main/eda.ipynb)
- [Model building](https://github.com/kaichiinoue/nba_salary_prediction/blob/main/model_building.ipynb)

## Motivation
There are some superstarts in NBA who earn crazy amount of money every year. As a huge basketball fan, I got to think whether their performances are pure factors that determine their salary. If I train a model only based on their stats, would that model be able to accurately predict another player's salary? 

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
- 3P (3-Points Field Goals)
- 3PA (3-Points Field Goals Attempts)
- 3P% (3-Points Field Goals Percentage)
- 2P (2-Points Field Goals)
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
Looked at the distribution of the data and the value counts for most of the categorical variables. Also, checked the correlation value for each continuous variables and figured out most of the variables from players stats are heavily correlated each other. However, this is my first project, so I decided to just go with all the variables included for the model building process. Below are the some of the graphs from EDA.
![](/image/graph1.png)
![](/image/graph2.png)

## Model
As the first thing to do, I transformed categorical variables such as Pos(Position) and Tm(Team) into dummy variables. After that, I split the dataset into test set and training set. I set the portion of test set to be 20% and training set to be 80%.

For the models, I tried four different kinds of models: sklearn Multiple Liear Regression, Lasso Regression, Ridge Regression, Random Forest. I chose R-squared to evaluate each model performance. 
- **Multiple Linear Regression** - Baseline model
- **Lasso** - I thought Lasso would be a good model for this case because most of the continuous variables have skewed distribution. However, the optimal alpha value never diverges, so I decided not to include Lasso this time.
- **Ridge** - I am not too familiar with Lasso and Ridge so I wanted to also include this model here.
- **Random Forest** - I used GridSearchCV to get the best combination of hyper parameters, but somehow the default parameters gave me the best accuracy.

## Model Performance
The Random Forest with default hyper parameters outperformed other models on the test set. As evaluation metrics, I used R-squared.
- **Multiple Linear Regression**: R<sup>2</sup> = 0.479
- **Ridge**: R<sup>2</sup> = 0.534
- **Random Forest (default)**: R<sup>2</sup> = 0.770
- **Random Forest (best params)**: R<sup>2</sup> = 0.765
