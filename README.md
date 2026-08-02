# Shot Volume or Shot Quality? A Machine Learning Approach to Explaining Expected Goals in Football

*Completion Date: 01/08/2026*

## Overview

This project explores how expected goals (xG) can be explained using increasingly detailed descriptions of the shots taken during a football match.

Starting from raw event-level data covering more than half a million shots, the data was cleaned, aggregated to match level, and validated against a separately structured match-level dataset.

A series of regression models were then used to measure how much of observed xG could be explained by:

- Total shot volume
- Shot outcomes
- Shot situations
- Home and away attacking performance

The objective was not to recreate the underlying xG model, but to investigate which observable shot characteristics contribute most strongly to a team's expected goals output.

## Key Features

- Cleaned and processed more than 500,000 shot events
- Aggregated event-level data into match-level features
- Validated the aggregation across more than 20,000 matches
- Created features for:
  - Shots on target
  - Shots off target
  - Blocked shots
  - Open-play shots
  - Corners
  - Set pieces
  - Direct free kicks
  - Penalties
- Compared progressively more detailed regression models
- Compared Linear Regression against Random Forest Regression
- Analysed home and away attacking performance separately
- Interpreted model coefficients in a football context

## Methods & Tools

- **Data Cleaning & Engineering:** pandas, NumPy, dataset merging, aggregation and feature engineering
- **Exploratory Data Analysis:** descriptive statistics, correlation analysis and visualisation
- **Visualisation:** matplotlib and seaborn
- **Modelling:** Linear Regression and Random Forest Regression
- **Model Evaluation:** R^2, Mean Absolute Error and Root Mean Squared Error
- **Validation:** comparison against separately structured match-level data

## Results

- Total shot volume alone explained approximately **30% of the variation in match xG**.
- Separating shots by outcome substantially improved performance:
  - Shots on target made the largest contribution to predicted xG.
  - Blocked shots contributed less than shots that missed the target.
- Adding information about the situation in which shots were taken improved the model further.
- Penalties and direct free kicks carried the largest individual xG weights for shot situation.
- The full Linear Regression model achieved an R^2 of approximately **0.49** for total match xG.
- Separate home and away models achieved R^2 values of approximately:
  - **0.56 for home xG**
  - **0.57 for away xG**
- Random Forest Regression did not outperform Linear Regression, which is consistent with the relationship between these shot metrics and xG being largely linear.
- A substantial proportion of xG remained unexplained, highlighting the importance of additional features such as:
  - Shot location
  - Body part
  - Defensive pressure
  - Goalkeeper positioning
  - Action before receiving the ball

## Data

The data used in this project was obtained from the following Kaggle dataset:

- Player Stats Per Game - Understat  
  https://www.kaggle.com/datasets/codytipton/player-stats-per-game-understat

The full datasets are not stored in this repository due to file size.

Small samples are included in the `data` folder to demonstrate the structure of the two files used:

- `game_events_sample.csv` - shot-level event data
- `general_game_stats_sample.csv` - match-level summary data

To reproduce the full analysis, download the complete dataset and ensure the files are named:

- `game_events.csv`
- `general_game_stats.csv`
