# Commission Contract

### Simple Summary

Pays shares the Commission between dapps, referrals, and the DAO.

### Abstract

this upgradeable contract determines how to share and deposit commissions. commissions come from the [Power NFT](./) contract to this contract and the Commission contract divides the commission into 3 parts: referral percent, dapp percent, and the rest for the DAO percent. each part separately will be deposited to their own [Id Cards](../id-card/) accounts.
