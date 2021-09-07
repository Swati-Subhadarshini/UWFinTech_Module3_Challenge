# UWFinTech_Module3_Challenge
## Arbitrage Opportunities for Bitcoin on two Exchanges.

This project is designed to find any arbitrage opportunies exist for the Bitcoin on two different exchanges Bitstamp and Coinbase by applying three phases of financial analysis (collect the data, prepare the data and analyse the data)

---

## Technologies Used

Leveraging Jupyter Notebook
Gitbash CLI is used to pull and push the code from local repository to remote repository
Code written with the help of Jupyter Notebook.

---

## Libraries and Dependencies

panda library
pathlib library
numpy library
matplotlib library

---

## Data Collection:

Data collection is done by importing the bitstamp and coinbase csv files by codes

``` 
bitstamp = pd.read_csv(Path("Resources/bitstamp.csv"), index_col="Timestamp", parse_dates=True, infer_datetime_format=True)
```

```
coinbase = pd.read_csv(Path("Resources/coinbase.csv"), index_col="Timestamp", parse_dates=True, infer_datetime_format=True)
```

## Data Preparation

### For the bitstamp DataFrame, replace or drop all NaNs or missing values in the DataFrame
`bitstamp = bitstamp.dropna()`
`coinbase = coinbase.dropna()`

### Use the str.replace function to remove the dollar sign, $ from the "Close" column
`bitstamp.loc[:, "Close"] = bitstamp.loc[:, "Close"].str.replace("$","")`
`coinbase.loc[:, "Close"] = bitstamp.loc[:, "Close"].str.replace("$","")`

### Review the data for duplicate values, and drop them if necessary
`bitstamp.duplicated().sum()`
`coinbase.duplicated().sum()`

## Data Analysis

### Data analysis with the help of getting the data summary and plot visualization

### Generate the summary statistics for the bitstamp DataFrame
`bitstamp.describe()`
`coinbase.describe()`

### ploting the dataframes by plot()

`bitstamp.plot(figsize=(15, 7), title="Bitstamp", color= "green")`
`coinbase.plot(figsize=(15, 7), title="Coinbase", color= "red")`

## Calculating the Arbitrage Profit
### By using the below mentioned example which is done for the early date of the dataset we can get the calculation for middle and late dates of the dataset too and can review the profit and arbitrage opportunities exist in the datasets.

```arbitrage_spread_early = bitstamp['Close'].loc['2018-01-05'] - coinbase['Close'].loc['2018-01-05']
spread_return_early= arbitrage_spread_early[arbitrage_spread_early>0] / coinbase['Close'].loc['2018-01-05']
profitable_trades_early = spread_return_early[spread_return_early > 0.01]
profit_early = profitable_trades_early * coinbase['Close'].loc['2018-01-05']
profit_per_trade_early = profit_early.dropna()
profit_per_trade_early.plot()
cumulative_profit_early = profit_per_trade_early.cumsum()
cumulative_profit_early.plot(figsize= (10,7), title="Cumulative Crypto Profits")
```
The Jupyter notebook contains the analysis report of the project with data and visulization.

## Contributors

This project is designed by Swati Subhadarshini 
Emaid id: sereneswati@gmail.com
LinkedIn link: https://www.linkedin.com/in/swati-subhadarshini-89a8a538?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BhUCLlUYCSc2jK4x4khPVUQ%3D%3D

---