# Risk-Return-Analysis

## RISK RETURN
*This notebook shows  ways to analyze the performace of select funds versus the S&P 500.*

## **Terms**

**Daily Return**
*The Daily Return is calculated by subtracting the current day's closing price, by the previous days closing price, and then dividing the sum.*
`daily_return=((current_close - prior_close) / prior close)`

**Cumulative Return**
*The Cumulative Return on an investment is the total return on that investment over a defined period of time. Think of it as an accumulation of return values for each day of the period multiplied one upon another. To calculate the Cumulative Return, we use the `cumprod` function.* `cumulative_returns = (1+ daily_return).cumprod()`

**Mean**
*To find the Mean (or average) of a set of numbers we sum the values in the Series and then divide the sum by the Series count. The following code shows an example:*'``python
stock_abc = pd.DataFrame({'close': [11.25, 11.98, 10.74, 11.16, 12.35, 12.87, 13.03]})
stock_abc_mean_1 = stock_abc['close'].sum() / stock_abc['close'].count()
stock_abc_mean_1
``

*Alternatively we can call the Pandas `mean` function and get the same result.*
`stock_abc_mean_2 = stock_abc['close'].mean()`

**Standard Deviation**
*The Standard Deviation measures the volatility of an asset's price compared to its historical mean over a particular time period. A small Standard Deviation indicates that the daily return values of hte asset don't move far from the average. A large Standard Dev indicates that the asset is quite volatile. To calculate the Standard Deviation, get the daily returns, and then just use the `std` function like so:*
`standard_deviation = daily_returns.std()`


**Sharpe Ratio**
*The Sharpe ratio analyzes the risk of an invetment in relation to the potential reward. To calculate the Sharpe ratio for an investment we subtract the risk free rate of that investment from it's average annual return, and then divide the result by the annualized standard deviation of the investment's return.*

*We calculate the daily returns, then annual returns*
``average_annual_return_portfolio_a_b = daily_returns_a_b.mean() * year_trading_days``

*Then annualized standard deviation*
``annual_std_dev_portfolios_a_b = daily_returns_a_b.std() * np.sqrt(year_trading_days)``

*Then divide the annualized asset return by the annualized standard deviation.*
``sharpe_ratios = average_annual_return_portfolio_a_b / annual_std_dev_portfolios_a_b``

**Variance**
*The Variance measures the risk of a single asset by considering how far the closing prices deviate from their mean value. Once we have the daily return, we use the `.var` function*

**Covariance**
*The Covariance considers the behavioral relationship between two assets (that is, whether the stock prices move in the same or the opposite direction). To measure the covariance between two assets, we can use the Pandas `.cov` function.*
`covariance = daily_returns_amzn_spx['AMZN'].cov(daily_returns_amzn_spx['S&P 500'])`

**Beta**
*Beta measures the directional relationship between a stock and the broader market. A Beta of 1 indicates that the asset's return value will likely be exactly the same as that of the market. Greater than 1 means it should be greater than the change in the market's return value. less than 1 indicates less. For example if AMZN has a Beta of 1.00, for every 1% change in the S&P 500, AMZN would likely change by 1%. if AMZN has a Beta of .50, for every 1% change in the S&P 500, the AMZN return would likely change by .5%. To calculate the Beta, we divide the Covariance of an asset (that is, the asset's relationship to the market) by the Variance of the market.*
`amzn_beta = daily_returns_amzn_spx['AMZN'].cov(daily_returns_amzn_spx['S&P 500']) / daily_returns_amzn_spx["S&P 500"].var()`

**Rolling Windows**
*If we want to look at a rolling dataset, we use  `.rolling(window=x)`and add that to whatever variable we're using. If we have a 60 day rolling variable, we won't see anything in our dataframe until day 60, but we'll see values for every day after.*

## **Team**
*Lucas Manning was helpful in reviewing my work*

## **Licenses**
*Anyone can use!*