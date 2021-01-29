# cppi
Constant Proportion Portfolio Insurance
# Summary
I am calculating industry indixes from S&P500 stocks, modeling CPPI and comparing with industry returns
# Results
CPPI allows to calculate allocations to risky and "safe" assets based on the risk appetite and industry performance and change these allocations dynamically.

![image info](./riskysafe.png)
<br>
![image info](./riskyalloc.png)

# Performance Comparison
Dynamic reallocation to STIP ETF reduced max drawdown by 17% and 38% for Transportation and Energy Minerals respectfully
### Bond + Equity combination
| Industry | Annualized Return | Annualized Vol | Sharpe Ratio | Max Drawdown |
|--------------|---|---|---|---|
|Transportation| 0.004125  |  0.029184 | -0.862939	  |  -0.17508 |
|Energy Minerals| -0.007116	  | 0.022741	  | -1.588453	  |-0.21078   |

### Pure Equity portfolio
| Industry | Annualized Return | Annualized Vol | Sharpe Ratio | Max Drawdown |
|--------------|---|---|---|---|
|Transportation| 0.009863	  |  0.079046 | -0.248029	  |  -0.348676 |
|Energy Minerals| -0.016292	  | 0.126969	  | -0.354979	  |-0.586560   |

# Quick Example
I used "robin_stocks" library to pull the prices for each stock in S&P500, their corresponsing sectors and capitalization. I found robin_stocks to be the most stable and reliable tool for pulling data for a large list of securities. <br>
In this example I want to give a quick example of how to perform CPPI algorithm only using free publickly available libraries such as "yfinance" and "yahoo_fin"

## Dependencies
```python
import pandas as pd
from datetime import date
import yahoo_fin.stock_info as si
import matplotlib.pyplot as plt
%matplotlib inline
import yfinance as yf
```
## Getting prices
As our risky assets we'll use SPDR S&P 500 ETF (SPY), which tracks performance of S&P500. We'll compare it to WisdomTree EM Quality Dividend Growth Fund (DGRE) to get a sence of exposure to Emerging Markets.<br>
We'll use Vanguard Short-Term TIPS ETF as our "safe" asset. We will increase allocation to TIPS as long as SPY and DGRE are dropping.
```python
sp2 = yf.Ticker('SPY').history(period='max') #S&P500
hqualem_eq = yf.Ticker('DGRE').history(period='max') #WisdomTree EM Quality Dividend Growth Fund
tips = yf.Ticker('VTIP').history(period='max') #Vanguard Short-Term TIPS ETF
```





