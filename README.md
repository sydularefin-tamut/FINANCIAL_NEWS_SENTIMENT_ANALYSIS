## Financial-News-Analysis-and-Stock-Price-Prediction

Project Overview

This project analyzes financial news articles and their impact on stock price prediction. The tasks include performing exploratory data analysis (EDA), extracting stock tickers using NLP, retrieving financial data, forecasting stock prices, and correlating news content with stock performance.

# Dataset
The dataset used in this project consists of financial news articles.

Download the reuters.headlines file from the following link:
https://www.kaggle.com/datasets/notlucasp/financial-news-headlines?select=reuters_headlines.csv

# Requirements
**pandas , numpy,  matplotlib,  nltk,  spacy, scikit-learn,  yfinance,  statsmodels,  tensorflow,  requests,  tqdm**

# Task 1: Exploratory Data Analysis (EDA)

**Objective**: Perform EDA on financial news headlines and descriptions to understand the dataset and identify key trends.

Steps

**Load Dataset:** Place the reuters_headlines.csv file in the appropriate directory and load it using Pandas.

**Clean Dataset:** Remove duplicates and handle invalid values in the Time column.

**Visualize Trends:** Create a line plot of the number of articles over time.

Analyze word frequency and generate a word cloud.

**Output:** Summary statistics and cleaned dataset stored in a DataFrame.

Visualizations saved or displayed inline.

## TASK 2 Stock Ticker Extraction

**Goal:**  
*To extract company names or stock tickers from news articles, map the extracted company names to their respective stock tickers using an API or reliable dataset. A dataset from Kaggle (S&P 500 companies) is downloaded, providing a list of stock tickers with corresponding company names.*


**Data Collection**
- **News Sources:** News headlines and descriptions are loaded from `reuters_headlines.csv`.
  - A dataset of S&P 500 companies (`sp500_companies.csv`) is used as the mapping source.

**Named Entity Recognition (NER)**
- **Model Used:** SpaCy’s NER model is utilized to extract organization names from article descriptions.
- **Data Cleaning:**
  - Extracted names are cleaned to remove possessives, brackets, and quotes.

**Mapping to Tickers**
- **Mapping Process:** Extracted company names are mapped to S&P 500 tickers using a dictionary that includes both short and long company names.
- **Fuzzy Matching:**
  - Fuzzy matching (via `rapidfuzz`) ensures accurate mapping even with slight variations in company names.

**Final Output**
- **Filtered Articles:**
  - Articles are filtered to retain only those with successfully matched tickers.
- **Resulting Dataset:**
  - The resulting dataset includes **headlines**, **descriptions**, **extracted company names**, **matched company names**, and **stock tickers**.

### Task 3 Financial Data Retrieval

**Objective:** Retrieve key financial metrics and historical stock prices for identified companies.

**Load Dataset:** Read unique_stock_companies.csv for stock tickers.

**Fetch Financial Metrics:** Use Yahoo Finance API to retrieve market capitalization and P/E ratio.

Store results in a DataFrame.

**Fetch Historical Prices:** Retrieve the past year’s daily closing prices for all tickers.

**Save Outputs:** Save financial metrics in stock_financial_data.csv.

Save historical prices in historical_prices.csv.

**Visualizations:** Create line plots for historical stock prices.

Display metrics distributions (e.g., market capitalization).

## Task 4: Stock Price Prediction
**Import Libraries:**
Ensure all necessary libraries are imported, such as numpy, pandas, yfinance, tensorflow, matplotlib, seaborn, and scikit-learn.

**Set Parameters:**
Define the stock ticker (ticker), start date (start_date), and forecast horizon (forecast_steps). These parameters control which stock's data is fetched and for how long predictions are made.

**Fetch Historical Data:**
Use the get_stock_data function to download historical stock price data for the specified ticker. Focus on key columns such as Open, High, Low, Close, and Volume.

**Visualize Historical Data:**
Plot the closing prices and trading volumes over time using matplotlib and seaborn to understand trends and patterns in the data.

**Data Preprocessing:**

Normalize the data using MinMaxScaler to scale values between 0 and 1.
Split the dataset into training and testing subsets.
Prepare input (X) and output (y) sequences for multi-step forecasting.

**Build and Train the LSTM Model:**
Use the build_lstm_model function to define an LSTM model with layers tailored for sequential data.
Train the model on the prepared training dataset for a specified number of epochs and batch size.

**Make Predictions:**
Generate predictions for the test dataset using the trained model.
Inverse scale the predictions to restore them to the original price range.

**Evaluate the Model:**

Compute performance metrics such as RMSE and MAE for each forecast step.
Print the metrics to assess the model's accuracy.

**Visualize Predictions:**

Plot actual vs. predicted prices for a selected forecast step to evaluate the model's performance visually.
Overlay predictions for all forecast steps to analyze overall trends.

**Analyze and Interpret Results:**
Examine the performance metrics and visualizations to determine how well the model predicts future stock prices and identify areas for improvement.

## TASK 5 News Analysis and Impact Evaluation (Code has Issues and is Not Working Properly)

**Prepare the News Data**
- Ensure that the news dataset contains columns like **Headlines**, **Description**, and **Time**.

**Perform Sentiment Analysis**
- Apply **VADER** sentiment analysis to classify headlines into sentiment categories.

**Extract Company Names**
- Use **SpaCy** to extract potential company names from the news descriptions.

**Validate Stock Tickers**
- Check the extracted company names against valid stock tickers using **yfinance**.

**Retrieve Stock Prices**
- Fetch the next-day stock closing price for the associated tickers using **yfinance**.

**Analyze and Visualize**
- **Correlate** the sentiment categories with stock price changes.
- Create visualizations, such as **boxplots**, to show the relationships.

**Save Results**
- Export the processed data to a CSV file for record-keeping.
