# Web3-Trading-Insights
# Junior Data Scientist - Trader Behavior & Market Sentiment Insights

## Project Overview

This project explores the intricate relationship between trader performance and market sentiment in the Bitcoin market, leveraging historical trader data from Hyperliquid and a Bitcoin Fear & Greed Index dataset. The primary objective is to uncover hidden patterns and deliver actionable insights that can drive smarter trading strategies within the Web3 trading space.

## Problem Statement

In the volatile world of crypto trading, understanding how market psychology (sentiment) influences trader behavior and profitability is crucial. This assignment aims to analyze if and how different market sentiments (Fear, Greed, Neutral, Extreme) correlate with trader success and specific trading actions (BUY vs. SELL).

## Data Sources

Two primary datasets were utilized:
1.  **Bitcoin Market Sentiment Data (`fear_greed_index.csv`):** Contains daily classifications of market sentiment (e.g., Fear, Greed, Extreme Greed) with corresponding sentiment values. - https://drive.google.com/file/d/1PgQC0tO8XN-wqkNyghWc_-mnrYv_nhSf/view?usp=sharing
2.  **Historical Trader Data (`historical_data.csv`):** Comprehensive dataset including individual trade details such as `account`, `execution price`, `size`, `side`, `closedPnL`, and timestamps. - https://drive.google.com/file/d/1IAfLZwu6rJzyWKgBToqwSmmVYU6VbjVs/view?usp=sharing

## Methodology

The analysis was structured into the following key phases:

1.  **Data Loading & Preprocessing:**
    * Loading CSV files into Pandas DataFrames.
    * Converting relevant columns (`Date`, `Timestamp IST`) to `datetime` objects.
    * Extracting daily trade dates for merging.
    * Handling duplicate entries.
2.  **Data Merging:**
    * Performed a left merge of trader data with sentiment data on respective daily date columns to enrich trade records with sentiment context.
3.  **Exploratory Data Analysis (EDA):**
    * Descriptive statistics and value counts for key numerical and categorical features.
    * Initial visualizations of PnL distribution and sentiment trends over time.
4.  **Sentiment-Performance Analysis:**
    * Calculated average `Closed PnL` and total trade volume for each sentiment classification.
    * **Crucially, analyzed average `Closed PnL` broken down by both market sentiment *and* trade side (BUY/SELL) to uncover directional profitability biases.**
5.  **Uncovering Hidden Patterns (Enhanced Analysis):**
    * Visualized detailed PnL distributions using violin plots across sentiment categories to understand the spread and density of profits/losses.
    * Identified top-performing accounts by total `Closed PnL` and analyzed their individual PnL distribution across different sentiment conditions to discern advanced trader behaviors.

## Key Findings & Actionable Insights

Our analysis revealed significant patterns that can inform smarter trading strategies:

* **Average PnL Varies by Sentiment Extremes:** The highest average `Closed PnL` was observed during "Extreme Greed" and "Fear" periods, suggesting that market extremes can offer more profitable opportunities than neutral conditions.
* **Optimal Trade Direction is Sentiment-Dependent:**
    * **SELL into Greed/Extreme Greed:** Trades initiated as **SELLs during "Greed" and "Extreme Greed"** showed substantially higher average profitability. This indicates a strong advantage in selling into periods of market euphoria or overextension.
    * **BUY into Fear:** Conversely, **BUY trades during "Fear"** sentiment periods yielded better average returns, supporting a contrarian "buy the dip" approach.
* **Fear Drives Market Activity:** "Fear" sentiment periods were associated with the highest overall trading volume and trade count, indicating increased market participation and volatility.
* **Top Traders Leverage Outliers:** While most individual trades yield small PnL, top-performing accounts appear to derive their significant total profits from successfully capturing large, outlier winning trades rather than consistent small gains. Their strategies may involve capitalizing on specific, high-impact opportunities aligned with sentiment extremes.

## Smarter Trading Strategies Derived:

1.  **Contrarian Execution at Extremes:**
    * **Strong Sell Signal in Greed:** Traders should consider initiating **SELL positions (shorting or profit-taking on longs)** when sentiment reaches **"Greed" or "Extreme Greed."**
    * **Strong Buy Signal in Fear:** Conversely, prioritize **BUY positions (going long)** when market sentiment is in **"Fear."**
2.  **Sentiment-Filtered Decision Making:** Use market sentiment as a critical filter for trade direction, aligning actions with historical profitability biases.
3.  **Focus on Capturing High-Impact Trades:** Develop strategies that aim to capitalize on rare, high-magnitude opportunities, especially during sentiment extremes, rather than solely pursuing frequent small gains.
4.  **Dynamic Risk Management:** Adapt risk levels based on sentiment-driven volatility; for example, being prepared for higher volatility during "Fear" periods.

## Technologies Used

* Python
* Pandas (for data manipulation and analysis)
* Matplotlib (for data visualization)
* Seaborn (for enhanced statistical data visualization)

## How to Run This Project

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/vnscka/Web3-Trading-Insights.git](https://github.com/vnscka/Web3-Trading-Insights.git)
    cd Web3-Trading-Insights
    ```
2.  **Place Data:** Ensure `fear_greed_index.csv` and `historical_data.csv` are placed directly in the root after downloading them.
3.  **Install Dependencies:**
    ```bash
    pip install pandas matplotlib seaborn
    ```
4.  **Run the Notebook:** Open the `web3insights.ipynb` file in a Jupyter environment (Jupyter Lab, Jupyter Notebook, VS Code with Jupyter extension).
