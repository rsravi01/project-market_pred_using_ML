
Stock Market Prediction with S&P 500 Data
This project is a basic stock market prediction model using the historical S&P 500 index data and a Random Forest Classifier. The purpose is to predict whether the S&P 500 index will increase the next day based on past data. The code uses rolling averages and other features to improve prediction accuracy.

Features
Historical Data Retrieval: Downloads the maximum period historical data for the S&P 500 index from Yahoo Finance (using yfinance) and saves it locally as sp500.csv for future use.

Data Preprocessing:

Removes unnecessary columns such as Dividends and Stock Splits.
Creates a target variable, Target, which indicates if the Close price will increase the next day.
Utilizes data from 1990 onwards.
Feature Engineering: Adds rolling averages and trend indicators based on different horizons (e.g., 2, 5, 60, 250, and 1000 days) to capture long-term and short-term trends.

Model Training and Testing:

Trains a RandomForestClassifier model on historical data.
Splits the data into training and test sets for validation.
Provides backtesting across multiple intervals to evaluate performance.
Evaluation:

Measures model accuracy using precision_score.
Provides a graphical representation of predictions vs. actual values.
Requirements
Python 3.x
Required packages:
bash
Copy code
pip install yfinance pandas scikit-learn matplotlib
Code Walkthrough
Data Loading:

If sp500.csv exists locally, it loads the historical data. Otherwise, it fetches the data from Yahoo Finance and saves it as sp500.csv.
Data Preprocessing:

Converts the index to DateTime for proper handling of date ranges.
Creates Tomorrow and Target columns to predict if the next day's Close will be higher than the current day's.
Model Definition:

A RandomForestClassifier is defined with specific hyperparameters (n_estimators=100, min_samples_split=100, random_state=1).
Training and Testing:

Splits the data into training and testing sets.
Uses the training data to fit the model, and evaluates predictions on the test data using precision score.
Backtesting Function:

The backtest function iterates through the dataset in steps to simulate real-world conditions by training the model on data up to a given point and testing on subsequent data.
Returns concatenated predictions across all backtest intervals.
Additional Feature Engineering:

Calculates rolling averages and trends over different horizons to capture market patterns.
Adds new predictors to improve model performance.
Enhanced Model:

Uses an updated predict function that applies a probability threshold (0.6) to filter predictions.
Fits the enhanced model on the training data, performs backtesting, and evaluates with precision score.
Usage
Run the Code: Execute the script to train the model on historical S&P 500 data and generate predictions.
Modify Parameters: Customize horizons, model parameters, or the probability threshold to experiment with different configurations.
View Results: Results, including prediction counts and precision score, will be printed in the console. Graphs of the predictions and trends will also be displayed.
Example Output
Prediction Counts: The number of days the model predicts the S&P 500 will go up or down.
Precision Score: The accuracy of the model in predicting the direction of the S&P 500 for the next day.
Graphs: Plots comparing actual vs. predicted trends.
Limitations
This model is purely for educational purposes and should not be used for real trading.
Performance may vary based on model parameters and data preprocessing choices.
License
This code is open-source and available for modification.
