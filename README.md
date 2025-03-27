# Stock-Sentiment-Analysis-VADER-TextBlob-
A Short &amp; Sweet sentiment Analysis Project



This project is based on the idea of sentiment trading and on the reinforced impact of any weekend news on the Monday morning daily maximum prices.
This tool analyzes news sentiment for major companies and predicts potential stock market movements based on the sentiment of recent news articles. The system retrieves news articles using the NewsAPI, performs natural language processing and sentiment analysis, and then validates predictions against actual stock market data.
Features
•	Retrieves recent news articles for specified companies
•	Processes text using NLP techniques (tokenization, stopwords removal, lemmatization)
•	Performs sentiment analysis on both raw and processed text
•	Calculates weighted sentiment scores based on article title, description, and content
•	Predicts potential market movements (UP, DOWN, NEUTRAL)
•	Validates predictions against actual stock price changes
•	Generates detailed reports and summaries

We use NewsAPI to draw articles for 20 companies:
•	Apple
•	Microsoft
•	Nvidia
•	TSMC
•	Tesla
•	Walmart
•	Visa
•	JPMorgan
•	Tencent
•	United Health
•	Costco
•	Netflix
•	Johnson & Johnson
•	Novo Nordisk
•	Alibaba
•	SAP
•	Hermes
•	Nestle
•	Cisco
•	Palantir


  

Validation Criteria
For a company to be included in the validation process:
•	Must have at least 30 articles analyzed
•	Must have a non-NEUTRAL predicted movement (UP or DOWN)

Text Processing
Text preprocessing: 
o	Convert to lowercase
o	Remove URLs, special characters, numbers
o	Remove punctuation
o	Tokenize text
o	Remove stopwords
o	Lemmatize words

Sentiment analysis: 
o	Raw text sentiment analysis using VADER
o	Processed text sentiment analysis
o	Weighted sentiment calculation (title: 50%, description: 40%, content: 10%)

Sentiment Classification
•	Positive: Sentiment score ≥ 0.1
•	Negative: Sentiment score ≤ -0.1
•	Neutral: Sentiment score between -0.1 and 0.1

Market Movement Prediction for VADER
•	UP: Combined sentiment score > 0.15
•	DOWN: Combined sentiment score < -0.15
•	NEUTRAL: Combined sentiment score between -0.15 and 0.15
Market Movement Prediction for TextBlob
•	UP: Combined sentiment score > 0.1
•	DOWN: Combined sentiment score < -0.1
•	NEUTRAL: Combined sentiment score between -0.1 and 0.1


Validation
•	Converts company names to stock ticker symbols
•	Retrieves actual stock price data using yfinance
•	For UP predictions: Compares before-period close price with after-period high price
•	For DOWN predictions: Compares before-period close price with after-period low price
•	Calculates prediction hit rate

Output
The script generates the following outputs:
•	Individual company CSV files with detailed article analysis
•	Summary CSV file with aggregated results for all companies
•	Console output showing: 
o	Per-company sentiment summary
o	Most positive and negative headlines
o	Company comparison sorted by sentiment
o	Market-wide sentiment
o	Prediction validation results and hit rate

Limitations
•	Relies on NewsAPI for article retrieval (API limits). This project would be far more developed if not for the limited free use
•	Prediction validation is based on a single day's price movement
•	General Crases pass below the radar.
•	TextBlob sentiment analysis may not capture financial nuances as well as specialized models
•	Requires a minimum number of articles (30) for prediction validation


Accuracy
After 5 weekends of testing the mean accuracy was 76% for TextBlob and 73% for VADER. 
The problem was that when the market crashes ( e.g. 10th of February 2025) the analysis falls flat and is unable to detect the future movement, as a result it achieves 0% accuracy for that day 



