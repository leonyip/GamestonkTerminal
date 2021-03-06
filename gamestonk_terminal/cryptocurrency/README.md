# CRYPTOCURRENCY

This menu aims to explore crypto world, and the usage of the following commands along with an example will be exploited below.

Note that we have added the ability to look at technical analysis in the ta menu.  Data loaded from CoinGecko has no candle data,
so indicators that rely on anything other than close will fail with an error.

[COINGECKO](#COINGECKO)
* [load](#load)
  * load a given coin vs a given currency [CoinGecko]
* [view](#view)
  * plot the loaded crypto data
* [trend](#trend)
  * show top 7 trending coins

[COINMARKETCAP](#COINMARKETCAP)
* [top](#top)
  * view top coins from coinmarketcap [coinmarketcap.com]

[BINANCE](#BINANCE)
* [select](#select)
  * select coin/currency to use
* [book](#book)
  * show order book
* [candle](#candle)
  * get klines/candles and plot
* [balance](#balance)
  * show coin balance

[MENUS](#Menu)
* [> ta](technical_analysis/README.md)
  * **technical analysis  for selected tickers**

# COINGECKO <a name="COINGECKO"></a>
## load  <a name="load"></a>

````
usage: load [-c --coin] [-d --days] [--vs]
````

Load a given coin vs a given currency. Currently only retrieves price, not volume or MarketCap. The current crypto  data is [Powered by CoinGecko API](#https://www.coingecko.com/en), which is an awesome service that currently requires no API Key!

* -c/--coin The coin you wish to load.  This can either be the symbol or the name.  `load -c btc` and `load -c bitcoin`
  will load.  The -c flag is optional,  the above is equivalent to `load btc`.
* -d/--days The number of days to look.  Defaults to 30 days.  As per the API: Minutely data will be used for duration within 1 day,
  Hourly data will be used for duration between 1 day and 90 days, Daily data will be used for duration above 90 days.
* --vs The currency to look against.  Defaults to "usd".


## view  <a name="view"></a>

````
usage: view
````

Plot the loaded crypto data.

![crypto_view](https://user-images.githubusercontent.com/25267873/115787452-20889a80-a3ba-11eb-9216-f7fd1ffc98cf.png)


## trend  <a name="trend"></a>
````
usage: trend
````
Print the top 7 trending coins from coingecko.

<img width="1004" alt="Captura de ecrã 2021-05-03, às 15 07 15" src="https://user-images.githubusercontent.com/25267873/116886674-45cea180-ac21-11eb-9951-ff10271df370.png">


# COINMARKETCAP <a name="COINMARKETCAP"></a>

## top <a name="top"></a>

````
top [-n] [-s --sort SORTBY] [--descend]
````

This command displays the top n cryptocurrencies from coinmarketcap.com.

* -n: Number of coins to look at (after sort).  Defaults to 10.
* -s/--sort : Column to sort by. One of {Symbol,CMC_Rank,LastPrice,DayPctChange,MarketCap}. Defaults to sorting by the CMC rank.
* --descend : Flag to change the sorting order.  Sorts in ascending order (since default order is the Rank which starts at 1).

<img width="990" alt="crypto" src="https://user-images.githubusercontent.com/25267873/115787544-4746d100-a3ba-11eb-9433-b7cb9142404a.png">

# BINANCE <a name="BINANCE"></a>

## select  <a name="select"></a>
````
usage: select [-c --coin] [-q --quote] [-i --interval] [-l --limit]
````

Select a coin/currency to the current object and load in the price dataframe.  Note that in binance, the exchange "ticker" is usually COINCURR, such as BTCEUR for BTC to EURO.  There is no USD, but it uses a coin tethered to the USD (USDT), which is the default. Some symbols are a combination of coins, as `ETHBTC` is a valid symbol
* -c/--coin Coin to load. If not specified, BTC will be loaded to prevent errors later.
* -q/--quote  Quote currency.  Defaults to `USDT` (which is 1-to-1 with USD)
* -i/--interval. Interval for candles.  One of [1day,3day,1hour,2hour,4hour,6hour,8hour,12hour,1week,1min,3min,5min,15min,30min,1month]. Defaults to 1day.
* -l/--limit.  Number of candles to get.  Defaults to 100.

## book  <a name="book"></a>
````
usage: book -l/--limit
````

Gets and shows the order book for the given coin/currency.  Shows the cumulative amount of orders.

* -l/--limit Number of orders to get on each side.  One of [5,10,20,50,100,500,1000,5000].  Defaults to 100.

![orderbook](https://user-images.githubusercontent.com/25267873/116886857-84fcf280-ac21-11eb-9803-5baa8bceca05.png)


## candle  <a name="candle"></a>
````
usage: candle
````

Show candle chart for loaded coin/currency.


![candle](https://user-images.githubusercontent.com/25267873/116886993-abbb2900-ac21-11eb-9ff8-b6a8131fdac5.png)


## balance  <a name="balance"></a>
````
usage: balance
````

Shows the current holding balance in your account.
