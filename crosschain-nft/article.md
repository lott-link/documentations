# Article

### **Cross Chain NFT Introduction**

Cross Chain NFT (Non-Fungible Token) is a unique non-interchangeable unit of data stored on such blockchain, power by smart contracts. Smart contract developers can use CrossChain NFT to communicate with other EVM compatible chain to transfer their own NFT form current blockchain to another one. They can transfer NFTs on some smart chains that rely on ERC721 like:

* Ethereum
* Polygon
* Binance Smart&#x20;

Cross Chain NFT on EVM compatible chain like: Ethereum, Binance Smart or Polygon enables smart contracts to approve an NFT on a blockchain and request to transfer NFT to another one. A Cross Chain NFT is the interoperability between two relatively independent blockchains. In other words, it allows blockchains to speak to one another because they’re built in a standardized way. Cross Chain NFT implementation is mainly represented by NFT swap and NFT transfer. With Cross Chains NFT, the limitations of a single chain NFT can be avoided.

### **Cross Chain NFT Contract**

CrossChainNFT contract Lock the \`tokenId\` from \`from\` in this contract, \`targetChainId\` and transfer to \`to\`. If \`to\` on \`targetChainId\` does not exist, token would be transferred back to \`from\` address. If \`to\` refers to a smart contract, it must implementation IERC721Receiver ‘onERC721Received’, which is called upon a safe transfer.

### **How dose Cross Chain NFT work?**

* **Token’s owner request a cross chain transfer**     &#x20;

By “requestTransferCrossChain” function you can request for a cross chain transfer on EVM compatible chain. CrossChainNFT will transfer your NFT from your address to its address and hold it. It hosts an off-chain order book. Using relayer, users can find, create, fill or cancel NFTs. Relayer helps you to mint a wrapped token corresponding to your NFT on EVM compatible chain and transfer it cryptographically to the address you requested. A relayer can talk to other relayers and create a pool of orders to increase liquidity.

* **Regards this contract, the token will be locked**

By implementation of Cross Chain NFT and send a request on another EVM compatible chain based on contract ‘tokenId’ from ‘from’ will be locked and ‘targetChainId’ will transfer to ‘to’. if \`to\` on \`targetChainId\` does not exist, token would be transfered back to \`from\` address. If \`to\` refers to a smart contract, it must imp\`{IERC721Receiver-onERC721Received}, which is called upon a safe transfer. If the caller is not \`from\`, it must have been allowed to move this token by either ‘approve’ or ‘setApprovalForAll’.

* **Mint a wToken by an event**

Relayers use ‘RelayerCallSafeMintWrappedToken’ event to mint a wToken on the \`targetChainId\` to get back the wToken on current chain. Then, relayer uses ‘RelayerCallRedeem’ event to redeem the collateral token on the other chainId.

Owener of NFT has an exclusive account with a basic access control. By default, the owner of account will be the one that deploy the contract. ‘transferOwnership’ function can change the next owner account.

Regads, ‘MintRedeemInterface’ when an NFT locks in a contract on a chain; its corresponding wToken will be minted in the other chain and when the wToken burns in a chain; the real NFT will be redeemed in its own chain.interface. ‘redeem’ function redeem the \`tokenId\` of \`contAddr\` and transfer it to \`to\`. ‘safeMintWrappedToken’ function SafeMint a wToken and transfer it to \`to\` and wToken holds the the data of real token.

\-      **wToken mint by relayer in another chain**

By WrapERC-721 contract that is a multi-chain contract, when an NFT locks in a contract on a chain; its corresponding wToken will be minted in the other chain. When the wToken burns in a chain; the real NFT will be redeemed in its own chain. ‘setImplementation’ function Set a new implementationAddr to do cross chain transactions. Owner of the token should approve the contract to lock the ‘tokenId’ of ‘contAddr’. only implementationAddr can call ‘redeem’ function to redeem the \`tokenId\` of \`contAddr\` and transfer it to \`to\`. ‘implementationAddr’ can call ‘SafeMint’ function to mint a ‘wToken’ and transfer it to \`to\`. ‘wToken’ holds the real token data. ‘burnWrappedToken’ function burn the ‘wTokenId’ that caller should be owner or approved by the owner. very ‘wToken’ is representing a real NFT which holds its data in this contract. when a ‘wToken’ mints, its data sets and when a ‘wToken’ burns its data will be burned too. ‘tokenURI’ function returns the URI of real NFTs representing.

\-      **Back NFT to the real chain**

‘CrossChainImplementation’ contract Emitted a request to relayer to mint a wToken owned by \`to\` on \`targetChainId\`. Then redeem the locked token and transfer it to \`to\` by emitting another request to relayer.

‘CrossChainImplementationInterface’ is an interface that contains two functions:  ‘requestTransferCrossChain’ and ‘requestReleaseLockedToken’ function signatures without the function definition implementation.

\-      **Storage wToken Data in contract**

In ‘WrapERC721DataStorage’ contract every wToken is representing a real NFT which holds its data in this contract. When a wToken mints, its data sets and when a wToken burns its data will be burned too.

**Cross Chain NFT Implementation**

\-      **Mint and Redeem a wToken**

Relayers use ‘RelayerCallSafeMintWrappedToken’ event to mint a wToken on the \`targetChainId\`. Relayer uses ‘RelayerCallRedeem’ event to redeem the locked token and transfer it to \`to\` by emitting a request.

\-      **Mint and Redeem Payment**

In payment contract, ‘mintFee’ function returns the fee needed to mint a token on the \`targetChainId\`. ‘redeemFee’ function returns the fee needed to redeem a token on the \`targetChainId\`. In both function \`targetChainId\` should be supported by this contract.

‘payMintFee’ function transfer most of value to the relayer to mint a wToken on other chain and the rest to the dapp as bonus.

‘payRedeemFee’ function Transfer most of value to the relayer to redeem a token on other chain and the rest to the dapp as bonus.

Both ‘payMintFee’ and ‘payRedeemFee’ function value should be more than minimum value needed to redeem a token.
