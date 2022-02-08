# Commission Contract

### Simple Summary

Pays shares the Commission between dapps, referrals, and the DAO.

### Abstract

this upgradeable contract determines how to share and deposit commissions. commissions come from the [Power NFT](./) contract to this contract and the Commission contract divides the commission into 3 parts: referral percent, dapp percent, and the rest for the DAO percent. each part separately will be deposited to their own [Id Cards](../id-card/) accounts.

### Functions

<details>

<summary><code>dappPercent() public view</code></summary>

Returns dapp commission percent

</details>

<details>

<summary><code>referralPercent() public view</code></summary>

Returns referral commission percent

</details>

<details>

<summary><code>setPercent(uint256 _dappPercent, uint256 _referralPercent) public</code></summary>

Set the referral percent and the dapp percent in one call

Requirements:

* `_dappPercent` and `_referralPercent` must be lesser than 100 in total.
* only the owner of the contract can call this function.

</details>

<details>

<summary><code>payCommission(string memory referral, uint256 dappId) public payable</code></summary>

Deposit commissions to the referral, dapp, and the DAO.

Dapp commission and referral will be deducted from the total commission and the rest is the DAO commission.

commissions will be deposited separately to referral, dapp and, the DAO ID Cards.

Requirements:

* `referral` username and `dappId` must exist.

</details>
