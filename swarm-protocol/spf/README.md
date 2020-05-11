# SwarmPoweredFundraise

## Introduction

The SwarmPoweredFundraise \(SFP\) is a significant addition to the open Swarm protocol and provides powerful tools to perform regulatory compliant fundraises for security tokens.

The requirement is that the token for which the fundraise occurs is operated on the [SRC20](https://www.swarm.fund/src20) standard. An SFP is like a module that can be used for each distinct fundraise for an SRC20 token.

Like SRC20, the SFP stack is open source, so the Swarm network welcomes token issuers and service providers freely use, extend and customize.

## Smart Contract Index

The following four contracts are created in relation to a specific SRC20 token and interact with one another and other global SRC20 smart contracts.

![](../../.gitbook/assets/spf-overview%20%281%29.png)

### Smart contracts specific to each SwarmPoweredFundraise

For each new SRC20 token, one of each of these smart contracts is newly created.

| Contract Name | Description | Example |
| :--- | :--- | :--- |
| Currency Registry | Registers all currencies that will be accepted in a specific Swarm Powered Fundraise | TBD |
| Affiliate Manager | Registers affiliates and their commissions for a SwarmPoweredFundraise | TBD |
| Swarm Powered Fundraise | Operates the actual SwarmPoweredFundraise; finalizes via stakeToMint | TBD |
| Contributor Restrictions | Manages whitelist and restrictions for each contributor in a Swarm Powered Fundraise | TBD |

### Smart contracts available across all SwarmPoweredFundraises

Each of the following \(pre-existing\) smart contracts exist across the SRC20 network and each SRC20 token interacts and registers with them.

| Contract Name | Description | Example |
| :--- | :--- | :--- |
| Uniswap Proxy | Proxy Contract that makes ongoing calls to the different Uniswap exchanges to obtain the prices of accepted currencies used in Swarm Powered Fundraises | TBD |
| Issuer Stake Offer Pool \(ISOP\) | Allows SWM token holders to offer their tokens OTC for issuance stake; NOT YET FORMALLY RELEASED AND FUNCTIONAL | TBD |

### Deployment Sequence

TBD

