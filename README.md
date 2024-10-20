# Updating the README.md content based on the new input

updated_readme_content = """
# Nifty 50 Trend Prediction Using Machine Learning

This project involves predicting the Nifty 50 stock market index trends using historical data obtained from Yahoo Finance. The machine learning model used is a Random Forest Classifier, with feature engineering applied to create rolling averages and trend indicators. The aim of the project is to predict whether the Nifty 50 index will rise or fall the following day.

## Table of Contents
- [Introduction](#introduction)
- [Dataset](#dataset)
- [Feature Engineering](#feature-engineering)
- [Model](#model)
- [Evaluation](#evaluation)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction
Stock market prediction has long been a challenging task due to the complex and volatile nature of financial markets. This project uses machine learning to predict the next day's Nifty 50 stock market trend (whether the index will go up or down) based on past trends and rolling average features. The model provides a probabilistic output, which is converted into binary predictions based on a threshold.

## Dataset
The dataset used in this project is sourced from Yahoo Finance through the yfinance Python library. The historical data for Nifty 50 (Ticker: ^NSEI) is fetched, which includes the following attributes:
- Date
- Open
- High
- Low
- Close
- Volume
- Dividends
- Stock Splits

After preprocessing, the dividends and stock splits columns are removed, and the Close price is used for prediction.

## Feature Engineering
Several new features are created to help the model capture trends over different time horizons. These features include:
- **Close_Ratio_{horizon}**: The ratio of the current close price to the rolling average of close prices over the given horizon.
- **Trend_{horizon}**: The sum of target values (whether tomorrow’s close price is higher than today’s) over the horizon.

The target variable `Target` is a binary indicator of whether the next day's close price will be higher than today’s close price.

## Model
We utilize the Random Forest Classifier from the sklearn library. The model is trained on historical data to predict whether the Nifty 50 index will rise (1) or fall (0) on the next day. The following steps are performed:
- **Train-Test Split**: The dataset is divided into a training set and test set based on a sliding window approach.
- **Backtesting**: The model is evaluated over several periods using backtesting. This method trains the model on increasing subsets of the dataset and tests it on subsequent data, simulating real-world predictions.
- **Random Forest Parameters**:
  - `n_estimators = 200`
  - `min_samples_split = 50`
  - `random_state = 1`

## Evaluation
The model predictions are evaluated using the following metrics:
- **Confusion Matrix**: A matrix showing the count of true positives, false positives, true negatives, and false negatives.
- **Precision Score**: The proportion of predicted upward movements that were correct.
- **Market Up Percentage**: The proportion of time the market actually increased, providing a baseline for comparison.

The model's performance is visualized using a bar chart, displaying both the precision score of the model and the percentage of time the stock actually increased.

## Results

- **Model Accuracy**: The Random Forest model's predictions are evaluated for precision, which measures the proportion of predicted upward trends that were correct.
- **Market Up Percentage**: A baseline indicating how often the market actually went up, providing a comparison for the model's performance.

The bar chart visualization shows the comparison between model precision and market up percentage.

## Contributing

We welcome contributions to this project. If you have suggestions for improvements or new features, feel free to:

- Fork the repository.
- Create a new branch for your feature or bugfix.
- Submit a pull request with a detailed description of the changes.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

