---
description: '- BETA -'
---

# Uniswap Proxy Contract

* **Smart Contract:** globally across all Swarm Powered Fundraises
* **Created:** pre-exists / created only once  and then referenced in each Swarm Powered Fundraise contract
* **Purpose:** Proxy Contract that makes ongoing calls to the different Uniswap exchanges to obtain the prices of accepted currencies used in Swarm Powered Fundraises
* **Example:** TBD

## Feature Description

### Read Functions

| Function | Description |
| :--- | :--- |
| `getRate(address, address, uint256, uint256)` returns `(uint256, uint256)` | Returns the exchange rate between first and second address. The first parameter is the token address of the currency to be exchanged from, the second parameter is the address of the currency to be exchanged to, the third parameter is the value in Wei to be exchanged and the fourth parameter is the decimal places; e.g. to get the rate of 1 ETH in DAI `getRate(“0x0000000000000000000000000000000000000000”,”0x2a1530C4C41db0B0b2bB646CB5Eb1A67b7158667”,1000000000000000000,0)` |
| `isOwner()` returns `(bool)` | Returns true if the caller is the current contract owner address of this contract |
| `owner()` returns `(address)` | Returns the address of the owner of this contract |

### Write Functions

| Function | Description |
| :--- | :--- |
| `addOrUpdateExchange(address, address)` | Adds an exchange pair between two currencies to the proxy. The first parameter is the token address and the second parameter is the Uniswap exchange address; e.g. to set up DAI stable coin the following should be called `addOrUpdateExchange("0x6B175474E89094C44Da98b954EedeAC495271d0F&#x201D;,&#x201D;0x6B175474E89094C44Da98b954EedeAC495271d0F")` |
| `renounceOwnership()` | Contract owner can renounce ownership of this contract. |
| `transferOwnership()` | An owner can transfer their role to a new address or to a multisig wallet |

