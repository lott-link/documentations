---
description: Random Number Consumer
---

# RNC

### Simple Summary

This is a contract that Consumes Verifiable Randomness using [Chainlink VRF](https://docs.chain.link/docs/chainlink-vrf/) Consumer base.

### Abstract

Smart contracts on EVM chains which Chainlink VRF Consumer base deployed on can use RNC contract to Consume verifiable random numbers. it's just two functions needed: the first one to request to get randomness and pay for it and the other one to receive the randomness and do something with that.&#x20;

RNC will automatically call the second one and fulfill the randomness.

### Motivation

Solidity developers can use the [Chainlink VRF tutorial](https://docs.chain.link/docs/get-a-random-number/) to write a smart contract that consumes randomness. but there are some difficulties: it is not so gas efficient to write a contract along with all RNC functions and variables, especially in the cases that we need just a few randomness calls. the other problem is that we have to use two different currencies for a call. there should be always some LINK token available in the contract that makes us able to request to the consumer base. and in addition to that, we always need some eth or other main currencies for their own EVM chains to pay the gas fee of the transaction.

Lottlink RNC contract is always full of LINK tokens and you can pay only current chains currency to generate a random number and the gas fee.

{% hint style="info" %}
in later updates, the RNC contract will use [uniswap](https://docs.uniswap.org/protocol/guides/swaps) to automatically swap current chains currency to LINK token.
{% endhint %}

### Events

<details>

<summary>Request(bytes32 requestId)</summary>

Emitted when an applicant requests for randomness.

</details>

<details>

<summary>Response(bytes data)</summary>

Emitted when RNC responses to the applicant.

</details>

### Functions

#### external functions

<details>

<summary>applicantFee() public view</summary>

Returns cost of every random number generation which applicant contract should pay.

</details>

<details>

<summary>linkSupply() public view</summary>

Returns LINK supply of the contract

</details>

<details>

<summary>earnedSupply() public view</summary>

Returns ETH supply of the contract

</details>

<details>

<summary>getRandomNumber(bytes4 _callBackSelector) public payable</summary>

Requests for a 30 digits random number and records the applicant's information.

Applicant should provide a `_callBackSelector` to receive the randomness.

Requirements:

* Enough LINK tokens should be available in RNC To generate a random number.
* Enough `msg.value` should be paid by the applicant

Emits a [Request](rnc.md#events) event

</details>

<details>

<summary>withdrawLink(uint256 amount) external</summary>

Withdraw LINK function to avoid locking LINK in the contract.

Requirements:

* only the owner of the contract can call this function.

</details>

<details>

<summary>withdrawEarnedSupply() external</summary>

Withdraw ETH paid by applicants

Requirements:

* only the owner of the contract can call this function.

</details>

#### internal functions

<details>

<summary>linkPrice() internal view</summary>

Returns current price of LINK compared to ETH with 18 decimal places.

earned by an oracle from [chainlink data feeds](https://docs.chain.link/docs/get-the-latest-price/).

</details>

<details>

<summary>fulfillRandomness(bytes32 requestId, uint256 randomness) internal</summary>

Callback function used by VRF Coordinator.

fulfills applicant last info (randomness) and responses to the applicant request.

</details>

<details>

<summary>_response(address contractAddress, bytes4 selector, uint256 randomResult) private</summary>

Response function to the applicable contract.

Requirements:

* call back should be successful.

Emits a [Response](rnc.md#events) event

</details>

{% swagger method="get" path="" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}
