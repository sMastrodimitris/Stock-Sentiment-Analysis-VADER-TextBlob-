# Stock Sentiment Analysis with VADER & TextBlob

A simple yet effective sentiment analysis tool designed to predict stock market movements based on news sentiment.

This project leverages the concept of sentiment trading, focusing on the influence of weekend news on Monday morning stock price fluctuations. By analyzing the sentiment of news articles, it predicts potential market movements for major companies. The system retrieves news articles through the NewsAPI, performs sentiment analysis using Natural Language Processing (NLP), and validates the predictions by comparing them to actual stock market data.

## Features

- Retrieves recent news articles for specified companies.
- Applies NLP techniques (tokenization, stopword removal, lemmatization) for text preprocessing.
- Performs sentiment analysis on both raw and processed text.
- Calculates weighted sentiment scores based on article title, description, and content.
- Predicts potential market movements (UP, DOWN, NEUTRAL).
- Validates predictions against actual stock price changes.
- Generates detailed reports and summaries.

## Companies Analyzed

The tool retrieves news articles for the following 20 companies:

- Apple
- Microsoft
- Nvidia
- TSMC
- Tesla
- Walmart
- Visa
- JPMorgan
- Tencent
- United Health
- Costco
- Netflix
- Johnson & Johnson
- Novo Nordisk
- Alibaba
- SAP
- Hermes
- Nestle
- Cisco
- Palantir

## Validation Criteria

For a company to be included in the validation process:

- Must have at least 30 analyzed articles.
- Must have a non-NEUTRAL predicted sentiment (UP or DOWN).

## Text Processing

### Preprocessing Steps:
- Convert text to lowercase.
- Remove URLs, special characters, and numbers.
- Eliminate punctuation.
- Tokenize the text.
- Remove stopwords.
- Lemmatize words.

### Sentiment Analysis:
- VADER is used for raw text sentiment analysis.
- Processed text is also analyzed for sentiment.
- Weighted sentiment scores are calculated as follows:
  - Title: 50%
  - Description: 40%
  - Content: 10%

### Sentiment Classification:
- **Positive**: Sentiment score ≥ 0.1
- **Negative**: Sentiment score ≤ -0.1
- **Neutral**: Sentiment score between -0.1 and 0.1

## Market Movement Prediction

### VADER:
- **UP**: Combined sentiment score > 0.15
- **DOWN**: Combined sentiment score < -0.15
- **NEUTRAL**: Combined sentiment score between -0.15 and 0.15

### TextBlob:
- **UP**: Combined sentiment score > 0.1
- **DOWN**: Combined sentiment score < -0.1
- **NEUTRAL**: Combined sentiment score between -0.1 and 0.1

## Validation Process

- Converts company names to stock ticker symbols.
- Retrieves actual stock price data using `yfinance`.
- **For UP predictions**: Compares the close price before the period with the highest price after the period.
- **For DOWN predictions**: Compares the close price before the period with the lowest price after the period.
- Calculates prediction hit rate.

## Output

The tool generates the following outputs:

- Individual CSV files for each company containing detailed article analysis.
- A summary CSV file with aggregated results for all companies.
- Console output including:
  - Per-company sentiment summary.
  - Most positive and negative headlines.
  - Company comparison sorted by sentiment.
  - Market-wide sentiment.
  - Prediction validation results and hit rate.

## Limitations

- Relies on NewsAPI for article retrieval, subject to API rate limits (project development is limited by the free API usage).
- Prediction validation only considers a single day's price movement.
- General market crashes (e.g., February 10th, 2025) may not be detected accurately, resulting in a drop in prediction accuracy.
- TextBlob's sentiment analysis may not fully capture financial nuances compared to specialized models.
- Requires a minimum of 30 articles for prediction validation.

## Accuracy

After testing for five weekends, the tool achieved the following mean accuracy:

- **TextBlob**: 76%
- **VADER**: 73%

However, is completely blind at market crashes, like on February 10th, 2025, where accuracy dropped to 0% due to the inability to detect drastic market changes.

---



