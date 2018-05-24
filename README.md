# Ccxtex

Ccxtex provides easy Elixir/Erlang interop with python ccxt library that provides unified API to access hisorical data and trading operations for multiple cryptoexchanges.

## Installation


### Elixir

```elixir
def deps do
  [
    {:ccxtpy, github: "cyberpunk-ventures/ccxtex"}
  ]
end
```

### Python

You need [ccxt](https://pypi.org/project/ccxt/) python package installed for this module to work.

## Status

Ccxtex is usable, but is under active development, API is unstable and will change. Some exchanges do not support all methods, errors are common.

* Public APIs in progress

- [x] fetch_ticker
- [x] fetch_ohlcv
- [x] fetch_exchanges
- [x] fetch_markets
- [ ] fetch_trades
- [ ] fetch_order_book
- [ ] fetch_l2_order_book

* Developer experience improvements

- [] unified public API call option structs
- [] integrate python 3 async calls and remove a pid arg from module functions
- [] capture exceptions generated by ccxt python library and convert to elixir success tuples

* Private APIs under consideration

## Examples

Default process id (@pid) is Ccxtex.Port. You can always start and use another process with Ccxtex.Port.start_link/2

### Fetch exchanges

Usage:
`exchanges = fetch_exchanges(@pid)`


```
[
...
%{
has: %{
  cancel_order: true,
  cancel_orders: false,
  cors: false,
  create_deposit_address: true,
  create_limit_order: true,
  create_market_order: false,
  create_order: true,
  deposit: false,
  edit_order: true,
  fetch_balance: true,
  fetch_closed_orders: "emulated",
  fetch_currencies: true,
  fetch_deposit_address: true,
  fetch_funding_fees: false,
  fetch_l2_order_book: true,
  fetch_markets: true,
  fetch_my_trades: true,
  fetch_ohlcv: true,
  fetch_open_orders: true,
  fetch_order: "emulated",
  fetch_order_book: true,
  fetch_order_books: false,
  fetch_orders: "emulated",
  fetch_ticker: true,
  fetch_tickers: true,
  fetch_trades: true,
  fetch_trading_fees: true,
  private_api: true,
  public_api: true,
  withdraw: true
},
id: "poloniex",
timeout: 10000
}
]
```


### Fetch ticker

Usage:

```
exchange = "bitstamp"
symbol = "ETH/USD"
ticker = fetch_ticker(@pid, exchange, symbol)
```

Return value example:
```
%{
base: "ETH",
base_volume: 4234.62695691,
close: 731.16,
exchange: "bitfinex2",
high: 737.07,
low: 726,
open: 736.77,
quote: "USDT",
timestamp: ~N[2018-01-01 00:00:00.000]
}
```

### Fetch OHLCV

Usage:

```
exchange = "bitstamp"
symbol = "ETH/USD"
ticker = fetch_ticker(@pid, exchange, symbol)
```

Return value example:
```
%{
ask: 577.35,
ask_volume: nil,
average: nil,
base_volume: 73309.52075575,
bid: 576.8,
bid_volume: nil,
change: nil,
close: 577.35,
datetime: "2018-05-24T14:06:09.000Z",
high: 619.95,
info: %{
  ask: "577.35",
  bid: "576.80",
  high: "619.95",
  last: "577.35",
  low: "549.28",
  open: "578.40",
  timestamp: "1527170769",
  volume: "73309.52075575",
  vwap: "582.86"
},
last: 577.35,
low: 549.28,
open: 578.4,
percentage: nil,
previous_close: nil,
quote_volume: 42729187.26769644,
symbol: "ETH/USD",
timestamp: 1527170769000,
vwap: 582.86
}
```



Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at [https://hexdocs.pm/ccxtpy](https://hexdocs.pm/ccxtpy).
