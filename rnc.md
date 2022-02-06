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

Solidity developers can use the [Chainlink VRF tutorial](https://docs.chain.link/docs/get-a-random-number/) to write a smart contract that consumes randomness. but there are some difficulties: it is not so gas efficient to write a contract along with all RNC functions and variables
