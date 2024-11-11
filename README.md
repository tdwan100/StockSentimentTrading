# Sentiment-Based Stock Trading Bot

A stock trading bot that leverages sentiment analysis from news articles and social media posts to make buying and selling decisions. This bot integrates sentiment analysis on Facebook-related posts and evaluates market trends to execute trading strategies. It uses Backtrader for strategy implementation and Yahoo Finance data for backtesting.

## Features

- **Sentiment Analysis**: Scrapes news articles and social media posts and uses Vader for sentiment analysis.
- **Custom Lexicon Integration**: Integrates stock market and other domain-specific lexicons for enhanced sentiment accuracy.
- **Backtesting**: Uses historical stock data to simulate trading strategies and visualize results.
- **Automated Trading Strategy**: Implements a moving average-based trading strategy, with buy and sell signals influenced by sentiment shifts.

## Getting Started

### Prerequisites

Make sure you have the following libraries installed:

- `nltk` for sentiment analysis
- `BeautifulSoup` for web scraping
- `Backtrader` for backtesting trading strategies
- `pandas`, `datetime`, `urllib`, and other standard libraries

Install dependencies:
```bash
pip install nltk beautifulsoup4 backtrader pandas
```

Download `vader_lexicon`:
```python
import nltk
nltk.download('vader_lexicon')
```

### Installation

1. Clone this repository:
    ```bash
    git clone https://github.com/your-username/sentiment-trading-bot.git
    cd sentiment-trading-bot
    ```

2. Set up a data directory for lexicons and Yahoo Finance data.

3. Import any additional lexicons or data files as required.

### Data Files

- **Lexicons**: Place custom lexicons in `lexicon_data/`.
- **Historical Stock Data**: Place stock data files (e.g., `BABA.csv` for Alibaba) in the project root directory.

## Usage

1. **Initialize Sentiment Analyzer**:  
   This bot uses NLTK's `SentimentIntensityAnalyzer` to process text and produce sentiment scores. Additional stock lexicons are loaded to refine the sentiment output.

2. **Run the Trading Bot**:
    ```bash
    python main.py
    ```

3. **Scrape Data**:  
   This bot scrapes articles from Business Times to analyze sentiment on Facebook-related news. The results are stored in `date_sentiments`.

4. **Run Backtesting**:  
   Once the sentiment data is collected, the bot backtests using Backtrader on Yahoo Finance data with a moving average strategy.

## Bot Strategy

The bot buys and sells based on sentiment shifts:
- **Buy** if the stock's close price is above the simple moving average (SMA) and sentiment has increased by 0.5 or more since the previous day.
- **Sell** if the close price is below the SMA and sentiment has decreased by 0.5 or more.

## Example Output

Starting Portfolio Value: $100,000  
Final Portfolio Value: *Calculated after backtesting*

Sample trade logs:
```
2022-09-01, BUY EXECUTED, Price: 250.5, Cost: 2505.0, Comm 0.25
2022-09-02, SELL EXECUTED, Price: 255.0, Cost: 2505.0, Comm 0.25
```

## Customization

You can modify several parameters to adjust strategy performance:
- Change sentiment thresholds for buy/sell decisions.
- Customize moving average periods.
- Add more sentiment lexicons or adjust the lexicon weights.

## Visualization

To visualize trading results, set up `matplotlib` for plotting. Backtrader will generate charts showing price and sentiment-based trades.

```bash
pip install matplotlib
```

## License

This project is licensed under the MIT License.
