---
sidebar_position: 2
---

# Entities
- account
- token 
- collection
- accountCollection
- transaction
- transfer
- sale
- currency
- hourlyCollectionSnapshot
- dailyCollectionSnapshot
- weeklyCollectionSnapshot

## account
### Description: The Wallet Address / User / Owner of an NFT
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | The wallet address for a user|
| tokens | [token!]! | The NFT’s owned by an account. |
| transfersFrom | [transfer!]! | The transfers that were sent by an account. |
| transfersFrom | [transfer!]! | The transfers that were to an account. |
| accountCollection | [accountCollection!]! | The collections for the NFT that an account owns with the total count of NFT’s for a specific collection. |

## token 
### Description: ERC721 Token / The NFT
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | Ethereum / Collection Addrress - Token Id (formatted to play nice with OpenSea) |
| collection | collection! | The collection address |
| identifier | BigInt! | The id of the NFT |
| owner | account | The address the currently owns the token |
| transfers | [transfer!]! | Transfers involving this token |


## collection
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | The address of the collection |
| name | String | The name of the collection |
| symbol | String | The symbol for the collection |
| totalSupply | BigInt | Total Supply of Tokens. As the NFTs of a collection are minted, this increments by 1. |
| mintPrice | BigDecimal | General Mint Price (does not factor discounted rates or team mints) |
| tokens | [token!]! | Tokens for the collection |
| supportsMetadata | Boolean | Collection supports metadata |
| totalSales | Int! | Total sales for the collection (transfer event + indexed sale event |
| totalVolume | BigDecimal! | Total volume (ETH and WETH only) |
| topSale | BigDecimal! | The largest ETH/WETH sale for the collection |
| hourlyCollectionSnapshot | [hourlyCollectionSnapshot!]! | Hourly info about the collection |
| dailyCollectionSnapshot | [dailyCollectionSnapshot!]! | Daily info about the collection |
| weeklyCollectionSnapshot | [weeklyCollectionSnapshot!]! | Weekly info about the collection |
| accountCollection | [accountCollection!]! | M:M relationship for Accounts and Collections |


## accountCollection
Important Note: If an address sells it's last NFT in the collection, the record will be removed from this entity.
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | Account Id - Collection Id |
| account | account! | Address of the account |
| collection | collection! | Address of the NFT Collection |
| tokenCount | Int! | Count of NFT's owned in a collection by the Address |


## transaction
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | the hash of the tx |
| timestamp | Int! | Timestamp for block |
| blockNumber | Int! | Block Number |
| transactionFrom | Bytes! | Address who initiated the transaction |
| transfers | [transfer!]!  | Transfers that occured within the transaction |
| sales | [sale!] | Sale events that occured within the transaction |
| unmatchedTransferCount | Int!  | Count of how many transfers were not matched to a sale. Used internally for transfer & sale matching |
| gasPrice | BigInt | *currently unstable* |
 

## transfer
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | Block Number and Event Id in which the transfers event occured |
| transaction | transaction! | Transaction hash in which the transfer event occured |
| collection | collection! | The collection address |
| token | token! | The collection addrress - The token id |
| senderAddress | account | The sender address |
| receiverAddress | account | The receiver address |
| timestamp | Int! | Timestamp for block |
| blockNumber | Int! | Block Number |
| amount | BigDecimal! | The amount of ETH paid |
| matchedSale | sale | matched sale event for the transfer |


## sale
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | Block Number and Event Id in which the sale event occured |
| transaction | transaction! | Transaction that the sale occured in |
| currency | currency | The currency that the sale was paid in |
| amount | BigDecimal! | the amount of the sale |
| timestamp | Int! | Timestamp for block |
| blockNumber | Int! | Block Number |
| platform | String | The name of the marketplace where the sale occurred |


## currency
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | The currency address. If unknown ERC20 due to lack of event info: '0xbadfeed000000000000000000000000000000000' |
| decimals | Int | The number of decimals used for the currency |
| name | String! | The currency name (eg Ether, Wrapped Ether) |
| symbol | String! | The currency symbol (eg ETH, WETH) |


## hourlyCollectionSnapshot
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | The collection address - The hour |
| timestamp | Int | Unix Week (Timestamp / 3600 * 3600) |
| collection | collection! | The collection address |
| hourlyVolume | BigDecimal! | The hourly volume |
| hourlyTransactions | Int | Number of hourly transactions |
| hourlyAvgSale | BigDecimal! | Average sale amount for the hour |
| topSale | BigDecimal! | Hourly top sales |
| bottomSale | BigDecimal! | Hourly bottom sales |

## dailyCollectionSnapshot
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | The collection address - The day |
| timestamp | Int | Unix Week (Timestamp / 86400 * 86400) |
| collection | collection! | The collection address |
| dailyVolume | BigDecimal! | The daily volume |
| dailyTransactions | Int | Number of daily transactions |
| dailyAvgSale | BigDecimal! | Average sale amount for the day |
| topSale | BigDecimal! | Daily top sales |
| bottomSale | BigDecimal! | Daily bottom sales |

## weeklyCollectionSnapshot
| Field | Type | Description |
| ----------- | ----------- | ----------- |
| id | ID! | The collection address - The week |
| timestamp | Int | Unix Week (Timestamp / 604800 * 604800) |
| collection | collection! | The collection address |
| weeklyVolume | BigDecimal! | The monthly volume |
| weeklyTransactions | Int | Number of monthly transactions |
| weeklyAvgSale | BigDecimal! | Average sale amount for the week |
| topSale | BigDecimal! | Weekly top sales |
| bottomSale | BigDecimal! | Weekly bottom sales |


