# QSS20 final
## How does weather affect quarterback performance in the NFL?

### Introduction
We have seen our fair share of harsh weather games in the NFL. Games played in snow, games played in rain, games played in frigid conditions, and games played in harsh winds. We have been told to temper our expectations in situations of extreme weather. Is this really the case? Are there some quarterbacks that thrive in extreme weather? We employ a combination of linear models and gradient boosting decision trees to determine our answer. 

### Data
The data we will be using is from [nfl_data_py](https://pypi.org/project/nfl-data-py/) - a Python package that contains play-by-play NFL data. We will be looking at all quarterback performances from 2014-2023 inclusive.

There is a variable within the dataset called "weather" where we will look for certain words that resemble rainy/snowy/windy/cold weather.

How will we be measuring quarterback performance? We will be using the Expected Points Added (EPA) per game metric. This is a great way to see how a quarterback's performance directly contributes to the team's success and is a much better metric than a basic statistic like passing yards.

We will be splitting our project into three separate python files. File 1 and File 2 will produce an output csv that will then be imported into the next file. These csvs have been included in the data section of the repository.

### Script 1 - Data wrangling
[01_data_wrangling.py](https://github.com/Atuav10/QSS20_final/blob/main/code/01_data_wrangling.ipynb)
Loads in the play-by-play data from the nfl_data_py package. [Outputs](https://github.com/Atuav10/QSS20_final/blob/main/data/output01_input02.csv) a csv file containing every single QB performance and the standardized weather conditions associated with that performance. 

This file includes importing all of the variables and extracting weather, temperature, and wind speed from the "weather" column. There are also a couple basic statistics included like mean EPA for each weather condition and seeing how frequent each weather condition occurs.

We then aggregate the individual plays to the game level for each quarterback. Now each entry is a **game performance** for a given quarterback. This file is saved as a csv and will be the input for our next script

### Script 2 - Model - Creation, training/testing, and evaluation
[02_model.py](https://github.com/Atuav10/QSS20_final/blob/main/code/02_model.ipynb)
Loads in the output from script 1. [Outputs](https://github.com/Atuav10/QSS20_final/blob/main/data/output02_input03.csv) a csv file that contains the quarterback name, associated weather data, and our prediction based on the model output.

In this script, we begin by conducting three different linear regression models where the main predictors are rainy/sunny/cloudy, the outcome is EPA, and the main controls are temperature and wind speed. 

We then conduct an XGBoost model with all of our variables, trying to predict EPA. We split our data into training and testing and then institute the appropriate XGBoost parameters.

The final step is evaluating the model. We look at the major features, learning rate, error, and residual analysis for a holistic evaluation.

We combine the results of the training and testing data (predictions) and save this as a csv. This is the input to the final model.

### Script 3 - Applications
[03_applications.py](=https://github.com/Atuav10/QSS20_final/blob/main/code/03_applications.ipynb)
Loads in the output from script 2. No unique output.

In terms of applications, we create our "EPA Over Expected" metric based on the residuals of our predictions. We see who the best players are in terms of EPAOE in the different weather conditions. The final application is a visualization of how the top quarterbacks fluctuate in terms of EPAOE over expected in the different weather conditions.

### Concluding words
This model can be useful at providing context to a quarterback's performance in adverse weather conditions. **Disclaimer: we expect the error rate to be quite high. It is extremely shortsighted to believe that we can predict QB performance solely based on weather. However, the point of this model is to determine the best QBs by taking weather into account. Some players might play in more adverse weather conditions.**


