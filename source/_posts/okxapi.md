---
title: 使用 OKX API 接口获取价格信息
date: 2026-01-28 13:40:19
---
### 效果图

![img](/pic/api_okx.png)


### 代码实现
```
import requests
import pandas as pd
from datetime import datetime

def get_single_tricker_data(symbol):

    ticker_url = f'https://www.okx.com/api/v5/market/ticker?instId={symbol}-SWAP'
    response_object  = requests.get(ticker_url)

    json_object = response_object.json()
    raw_df = pd.DataFrame(json_object)

    raw_df = pd.json_normalize(json_object,record_path=['data'])  # 将内嵌的数据完整的解析出来

    ticker_df = pd.DataFrame(index=[0],columns=['datetime','symbol','last'])
    ticker_df['datetime'] = pd.to_datetime(datetime.utcnow())
    ticker_df['symbol'] = symbol.replace('-','/').lower()
    ticker_df['last'] = raw_df['last']

    return ticker_df

def get_tickers_data(symbols):

    tickers_df = pd.DataFrame()
    for symbol in symbols:
        ticker_df = get_single_tricker_data(symbol)
        tickers_df = tickers_df.append(ticker_df)

    return tickers_df

def main():

    # symbol = 'BTC-USDT-SWAP'
    # tricker_df = get_single_tricker_data(symbol)
    # print(tricker_df)

    symbols = ['BTC-USDT','ETH-USDT','YGG-USDT','1INCH-USDT','DYDX-USDT','CRV-USDT',
                'UNI-USDT','ENS-USDT'
            ]
    tickers_df = get_tickers_data(symbols)
    print(tickers_df)


if __name__ == '__main__':
    main() 

```