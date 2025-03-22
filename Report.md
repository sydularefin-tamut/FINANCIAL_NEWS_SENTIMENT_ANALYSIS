## Exploratory Data Analysis (EDA) Findings
**Summary of the exploratory data analysis results:**

### Basic Properties
- **Dataset Shape:** The dataset contains 32,770 entries with 3 columns: `Headlines`, `Time`, and `Description`.
- **Unique Articles:** There are 32,575 unique headlines.
- **Duplicate Rows:** Identified 55 duplicate rows.
- **Invalid Time Values:** There are no invalid time values.
- **Data Types:** All columns are of `object` data type.
## Trends Over Time
Analyzed the volume of articles over time, there is a strong emphasis on geopolitical and economic events with words like "trade," "billion," "deal," and "china" frequently appearing, highlighting ongoing discussions around trade agreements and economic impact. The prevalence of days of the week suggests frequent reporting on daily events, possibly indicating regular news cycles or financial reporting. The appearance of "coronavirus" [COVID_19] which caused the pandemic, indicates a significant focus on health-related news, reflecting the widespread impact of the pandemic. Additionally, the names "trump" and "united" imply coverage related to political figures and entities, pointing toward political news being a major topic of discussion.

## TASK 2

**Goal:** *To extract company names or stock tickers from news articles, map the extracted company names to their respective stock tickers using an API or reliable dataset. A dataset from Kaggle (S&P 500 companies) is downloaded, providing a list of stock tickers with corresponding company names.*

### Data Collection
- **News Sources:**
  - News headlines and descriptions are loaded from `reuters_headlines.csv`.
  - A dataset of S&P 500 companies (`sp500_companies.csv`) is used as the mapping source.

### Named Entity Recognition (NER)
- **Model Used:**
  - SpaCy’s NER model is utilized to extract organization names from article descriptions.
- **Data Cleaning:**
  - Extracted names are cleaned to remove possessives, brackets, and quotes.

### Mapping to Tickers
- **Mapping Process:**
  - Extracted company names are mapped to S&P 500 tickers using a dictionary that includes both short and long company names.
- **Fuzzy Matching:**
  - Fuzzy matching (via `rapidfuzz`) ensures accurate mapping even with slight variations in company names.

### Final Output
- **Filtered Articles:**
  - Articles are filtered to retain only those with successfully matched tickers.
- **Resulting Dataset:**
  - The resulting dataset includes **headlines**, **descriptions**, **extracted company names**, **matched company names**, and **stock tickers**.

### TASK 3
The purpose of this task is to retrieve financial data for stock tickers extracted from the previous step, specifically:

- **Historical Price Data:** Closing prices for the past year.
- **Key Financial Metrics:** Market capitalization, P/E ratio.

## Why:
- **Historical Data:** Analyzing stock trends and price fluctuations over time is crucial for understanding market behavior and making informed decisions.
- **Financial Metrics:** Metrics like market capitalization, P/E ratio, and dividend yield provide insights into the financial health and valuation of a company, helping assess investment opportunities.
- **Automation:** Fetching data programmatically ensures scalability and accuracy, enabling regular updates.

### Data Source:
- **Yahoo Finance (yfinance):** Used to retrieve both historical price data and financial metrics.

### Data Retrieval:
- **Historical Prices:** Closing prices for all stock tickers are fetched for the past year, stored in a structured format.
- **Financial Metrics:** Information like market capitalization, P/E ratio, and dividend yield is extracted for each stock ticker.

### Error Handling:
- Ensures robustness by handling missing data or API errors during retrieval.

### Visualization:
- **Market Capitalization Distribution:** Plotted to show the range and concentration of company sizes.
- **Historical Price Trends:** Displayed using line plots for selected stocks.

### Output:
- Data is saved in CSV files for further analysis or reporting.

### Financial insights and forecasting results.
## Model Performance Results

The results show that the model performs better for **short-term predictions (1-3 days)**. As the forecast horizon increases, both **RMSE** and **MAE** grow, indicating larger errors. This is typical in stock price forecasting, as longer-term predictions are more uncertain due to market volatility.

- **Step 1 (next day)** shows relatively accurate predictions:
  - **RMSE** = 10.82
  - **MAE** = 8.96

- **Step 7 (7 days ahead)** shows higher errors:
  - **RMSE** = 15.17
  - **MAE** = 12.29

### Key Causes:
- **Stock market volatility.**
- **Limited features** (only historical prices and volume).
- **Model complexity** (LSTM with two layers).

### Improvement Suggestions:
- **Add more features** (e.g., technical indicators).
- **Use deeper or hybrid models.**
- **Incorporate external factors** like news sentiment.

# Correlation of News with Stock Performance

News plays a significant role in influencing stock prices by shaping investor sentiment and expectations. **Positive news** (e.g., strong earnings, mergers) typically drives stock prices up, while **negative news** (e.g., lawsuits, missed earnings) often leads to declines.

The provided code attempts to analyze this relationship by:

## Sentiment Analysis
- Classifies news headlines into **positive**, **negative**, or **neutral** using **VADER**.

## Named Entity Recognition (NER)
- Extracts company names mentioned in news articles with **SpaCy**.

## Stock Data Retrieval
- Maps companies to stock tickers and fetches next-day closing prices using **yfinance**.

## Impact Analysis
- Correlates sentiment with stock price changes and visualizes the results.

