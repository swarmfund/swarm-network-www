# SRC20

## Introduction

[SRC20](https://www.swarm.fund/src20) token framework of the Swarm protocol. It gives token issuers the tools to perform regulatory compliant security token issuances. [This blog post](https://medium.com/swarmfund/smart-contracts-upgrade-bd0da3b736ea) describes the overall goals and benefits.

As the SRC20 is open source, it allows token issuers and service providers alike to freely use this protocol stack and build custom solutions and services on top of it.

## Smart Contract Index

The following four contracts are created in relation to a specific SRC20 token and interact with one another and other global SRC20 smart contracts.

![](../../.gitbook/assets/scr20-overview%20%281%29.png)

### Smart contracts specific to each SRC20

For each new SRC20 token, one of each of these smart contracts is newly created.

| Contract Name | Description | Example |
| :--- | :--- | :--- |
| `Transfer Rules` | Manages whitelists and greylists for holders of a specific SRC20 token. | [Link](https://ropsten.etherscan.io/address/0xad872227FBCEE4271a2F89C4c9B7df0cc86E0e71#code) |
| `Featured` | This contract defines the supported token contract features for a specific SRC20 token \(e.g. account or contract freezing, additional minting or burning tokens\) and allows to check the state of the token contract \(e.g if it is currently paused for transfers\). | [Link](https://ropsten.etherscan.io/address/0x31830850853A9fa8cb7CC7Fbf5bD5f807B8B5B8e#code) |
| `Roles` | This contract defines the owner of the token contract and all assigned roles. Manages the addresses that can perform restricted actions for a specific SRC20 token as defined by the contract owner. SRC20 tokens can have four types of roles: `Owner`, `Authority`, `Manager` and `Delegate`. | [Link](https://ropsten.etherscan.io/address/0x32da71b47888a8c900761dff4fecd37c2e2da654#code) |

### Smart contracts available across all SRC20

Each of the following \(pre-existing\) smart contracts exist across the SRC20 network and each SRC20 token interacts and registers with them.

| Contract Name | Description | Example |
| :--- | :--- | :--- |
| `SRC20 Registry` | Registry of all SRC20 tokens created and 'hodler' of the associated SWM stakes | [Link](https://ropsten.etherscan.io/address/0xf37fdada55b07838cb865d9f2a9d449109eb9521#code) |
| `Asset Registry` | Registry of asset data for all SRC20 tokens \(meta data, esp. NAV\) | [Link](https://ropsten.etherscan.io/address/0x54f9b26edc46bd4beaf70ab2771b7ec178241932#code) |
| `Minter` | Manages the minting of SRC20 and corresponding SWM stakes of additional tokens added to an existing SRC20 | [Link](https://ropsten.etherscan.io/address/0xe0e57388e696c4db04643147070532111b21b8e8#code) |

### Deployment Sequence

As the SRC20 smart contracts need to reference each other, there is a specific deployment order for creating a new SRC20 token.

* **Deploy Smart Contracts**
  * **Step 1:** Deploy a new SRC20 Transfer Rules Smart Contract
  * **Step 2:** Deploy a new SRC20 Featured Smart Contract
  * **Step 3:** Deploy a new SRC20 Roles Smart Contract
* **Create and Register Token:** Sign a transaction to build and deploy your token exactly as per the configured specifications and register with the global SRC20 contracts
  * SRC20 Factory Smart Contract
  * Asset Registry Smart Contract 
  * SRC20 Registry Smart Contract
* **Mint SRC20 Tokens**
  * **Step 4:** Authorize withdrawal of the SWM stake to enable minting of tokens
  * **Step 5:** Mint the tokens by initiating withdrawal of the SWM stake and minting of SRC20 tokens; Deploys a new SRC20 Featured Smart Contract; in the set-up of this deployment the contracts from the previous steps need to be referenced 

**Note:** [Swarm.app](https://swarm.app/) is a dapp, which allows you to easily configure your SRC20 token set-up and in the final step the contracts are deployed accordingly and in the correct sequence

