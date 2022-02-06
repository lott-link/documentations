# Power NFT

### Simple Summary

It is an NFTcontract that rewards its token owners every round of time by random.

### Abstract

The following NFT contract is an ERC721 standardized smart contract that can live on Ethereum and all other EVM smart chains which Chain link VRF supports.

Power NFT uses Openzeppelin ERC721 implementation as the NFT side and Chainlink VRF as a provably fair and verifiable source to select the winner.

Like other NFTs, Power NFT represents ownership over digital or physical assets. Every power NFT holds a URI that can identify an image, a video, or other files.

Everyone can buy a token using the `buyToken(uri, referral, dappId)` payable function. The contract deposits the paid value in a uint variable as `tokenValue`.

Random number consumer determines next round 'power' and current round's winner token. Selected token charges by withdrawable balance as token value multiplied by the 'power.'.

The owner of the selected token can call the `burnAndWithdraw()` function and withdraw its balance. But the token burns then.

Power NFT uses a peer-to-peer advertisement system. And every person should introduce a referral and dapp which caused they buy a token. Then the contract deposits dapp and referral commission in LottLink Id card. (so they have to own an Id Card)

### Motivation

Power NFT has a living contract and is such an interactive NFT which means it is not just a file or asset. In addition to ERC721 attributes, every NFT has a value and a withdrawable balance that makes it not a simple NFT being.

It is a public contract. Artists can convert their arts to an NFT without deploying an exclusive contract and transfer or sell it directly or in marketplaces.

There is no exclusive dapp. Dapp developers can design their own dapp, use Power NFT, sell NFTs and receive a commission.

In addition to developers, ordinary people can also earn `commission` as `referral`

A decentralized DAO will govern the contract in the final version on the mainnet.

### Functions

