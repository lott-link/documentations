---
description: Random Number Consumer
---

# RNC

### Summary

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

### functions

<details>

<summary>applicantFee() public view</summary>

Returns cost of every random number generation which applicant contract should pay.

</details>

<details>

<summary>getRandomNumber(bytes4 _callBackSelector) public payable</summary>

Requests for a 30 digits random number and records the applicant's information.

Applicant should provide a `_callBackSelector` to receive the randomness.

Requirements:

* Enough LINK tokens should be available in RNC To generate a random number.
* Enough `msg.value` should be paid by the applicant

Emits a Request event

</details>

{% swagger method="get" path="" baseUrl="" summary="" %}
{% swagger-description %}

{% endswagger-description %}
{% endswagger %}
