# FinQual Package

This is a work in progress package that enables users to programmatically access the SEC EDGAR API database to retrieve financial information such as income statement, balance sheet or cash flow statement.

## Features
Ability to call the income statement, balance sheet or cash flow statement for any company on the within EDGAR, the SEC's Electronic Data Gathering, Analysis, and Retrieval system.

This has two key features that enable better programmatic access compared to other providers:
- Ability to call upto 10 requests per second
- No restriction on the number of calls within a certain timeframe

## Functions
First, import the package using:
```
from FinQual import FinQual as fq
```
From there, use a "Ticker" class to call the desired stock and the desired financial statement. For example:
```
fq.Ticker("TSLA").income(2020,2022)
fq.Ticker("TSLA").balance(2020,2022, quarter = True)
fq.Ticker("TSLA").cashflow(2020,2022)
```

Note that the financial statement function takes a mandatory timeframe input and then an optional input to return the quarterly results within that timeframe (default to annual results if not inputted).

## Limitations
Currently, there are several known limitations that I am aware of from my own testing. These are still to be looked at:

- Missing data values for companies, this is mostly due to companies using custom tags that are not accessible via the SEC database, and quite prevalent for quarterly reports as well
- More comprehensive mappings from known tags 
- No built-in way to restrict requests to 10 per second yet