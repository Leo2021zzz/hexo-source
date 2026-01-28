---
title: 使用 web3.py 进行转账
---
### 使用 web3.py 无需钱包软件即可实现转账

![img](/pic/web3transfereth.png)

```
from web3 import Web3, HTTPProvider

address = ''
rpc = ''

web3 = Web3(HTTPProvider(rpc))
balance = web3.fromWei(web3.eth.getBalance(address), "ether")
print(balance)
```