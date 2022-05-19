---
sidebar_position: 1
---

# The ERC721 Marketplace Subgraph

This Subgraph acts as a market aggregator for 3 marketplaces (all sale events from [OpenSea](https://opensea.io/), [LooksRare](https://looksrare.org/), and [X2Y2](https://x2y2.io/)) and indexes all ERC721 NFT transfer activity.

This guide explains the ERC721 Marketplace Subgraph and how to interact with it.

### Resources
- [Subgraph Explorer](https://thegraph.com/explorer) - sandbox for querying data and endpoints for developers.

- [ERC721 Marketplace Subgraph](https://github.com/Data-Nexus/721-Marketplace) - source code for deployed Subgraph.

### Contracts
#### OpenSea v1
0x7be8076f4ea4a4ad08075c2508e481d6c946d12b (start block: 5774644)

#### Opensea V2
0x7f268357a8c2552623316e2562d90e642bb538e5 (start block: 14120913)

#### LooksRare
0x59728544B08AB483533076417FbBB2fD0B17CE3a (start block: 13885625)

#### X2Y2
0x74312363e45dcaba76c59ec49a7aa8a65a67eed3 (start block: 14139150)

### Usage
You can utilize this Subgraph to get any sales realted info happened on OpenSea, LooksRare, and X2Y2. You can also query any info regarding any ERC721 NFT collection. All of which will be explained in details in the next section.

### Making Queries
To learn more about querying a subgraph refer to [The Graph's documentation](https://thegraph.com/docs/en/about/introduction/).