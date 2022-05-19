---
sidebar_position: 3
---

Get the latest 10 transfers for a collection including Sender, Receiver, Amount, Currency, Platform, Token Identifier, Collection Name, Timestamp

```
query MyQuery($collection: String = "0x23581767a106ae21c074b2276d25e5c3e136a68b") {
  transfers(
    where: {collection: $collection}
    ,first: 10
    ,orderBy: timestamp
    ,orderDirection: desc) {
    amount
    timestamp
    token {identifier}
    senderAddress {id}
    receiverAddress {id}
    collection {name,id}
    matchedSale {platform, currency {symbol}}
  }
}
```

Get the last the last 7 days metrics for a collection including: Total Sales, Total Volume, Average Sale Price, Highest Sale Price, Lowest Sale Price and Collection Name:

```
query MyQuery($collection: String = "0x23581767a106ae21c074b2276d25e5c3e136a68b") {
  dailyCollectionSnapshots(
     where: {collection: $collection}
    ,first: 7
    ,orderBy: timestamp
    ,orderDirection: desc) {
    dailyAvgSale
    dailyTransactions
    dailyVolume
    topSale
    bottomSale
    collection {name}
  }
}
```
