# QSS20 final
## How does weather affect quarterback performance in the NFL?

### Introduction
We have seen our fair share of harsh weather games in the NFL. Games played in snow, games played in rain, games played in frigid conditions, and games played in harsh winds. We have been told to temper our expectations in situations of extreme weather. Is this really the case? Are there some quarterbacks that thrive in extreme weather? We employ a combination of linear models and gradient boosting decision trees to determine our answer. 

### Data
The data we will be using is from nfl_data_py - a Python package that contains play-by-play NFL data. We will be looking at all quarterback performances from 2014-2023 inclusive.

There is a variable within the dataset called "weather" where we will look for certain words that resemble rainy/snowy/windy/cold weather.

How will we be measuring quarterback performance? We will be using the Expected Points Added (EPA) per game metric. This is a great way to see how a quarterback's performance directly contributes to the team's success and is a much better metric than a basic statistic like passing yards.

### Introductory Data Analysis
We will be comparing mean EPA in the certain situations of extreme weather. We will then conduct linear regressions to simply determine associations/perceived increase or decrease in EPA given the weather.

### Model
We have trained an XGBoost model on the data at a 80:20 training:testing split. We have then fit our model to predict EPA based on the weather conditions. **Disclaimer: we expect the error rate to be quite high. It is extremely shortsighted to believe that we can predict QB performance solely based on weather. However, the point of this model is to determine the best QBs by taking weather into account. Some players might play in more adverse weather conditions.**


