---
description: '- WORK IN PROGRESS -'
---

# SwarmPoweredFundraise

![](../../.gitbook/assets/fundraising-hero.png)

## Introduction

The SwarmPoweredFundraise \(SPF\) is a significant addition to the open Swarm protocol and provides powerful tools to perform regulatory compliant fundraises for security tokens.

The requirement is that the token for which the fundraise occurs is operated on the [SRC20](https://www.swarm.fund/src20) standard. An SFP is like a module that can be used for each distinct fundraise for an SRC20 token.

Like SRC20, the SPF stack is open source, so the Swarm network welcomes token issuers and service providers freely use, extend and customize.

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

1. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/factories/SRC20Registry.sol
   It needs SWM token address during deployment
2. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/factories/SRC20Factory.sol
   It needs SRC20Registry deployment address during deployment; after 'SRC20Factory' is deployed, go to deployed SRC20Registry contract and add this 'SRC20Factory' deployment address in 'addFactory()' function
3. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/token/AssetRegistry.sol
   It needs 'SRC20Factory' deployment address during deployment
4. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/factories/SWMPriceOracle.sol
   It needs SWM price in the form of two variables like numerator and denominator
5. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/factories/GetRateMinter.sol
   It needs three parameters, one is 'SRC20Registry' address, second is 'AssetRegistry' address and third is 'SWMPriceOracle' address. After 'GetRateMinter' is deployed, goto deployed 'SRC20Registry' contract and add this 'GetRateMinter' address in 'addMinter()' function
6. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/rules/TransferRules.sol
   It needs owner address, most of the time it will be issuer wallet address
7. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/roles/SRC20Roles.sol
   It needs the following parameters: 1/ 'owner address', 2/ 'SRC20Registry address' and 3/ 'TransferRules address'
8. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/token/features/Featured.sol
   It requires the following parameters: 1/ vowner address' and 2/ any number greater than 0 to enable features
9. Goto 'SRC20Factory' deployed contract, generate new SRC20 token using 'create()' function
10. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/fundraising/UniswapProxy.sol
11. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/fundraising/CurrencyRegistry.sol
   Register whatever currencies you want to accept for this fundraise using 'addCurrency()' function; most of the time it will be ZERO address for ETH, DAI address, USDC address and WBTC address. Register your base currency you want to use for this fundraise using 'setBaseCurrency()' function.
12. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/fundraising/SwarmPoweredFundraise.sol
   This requires several parameters: like 'label', 'SRC20 address', 'CurrencyRegistry address', 'startDate', 'endDate', 'softcap' and 'hardcap'
13. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/fundraising/AffiliateManager.sol
14. Deploy https://github.com/swarmfund/swarm-compliant-contract/blob/master/contracts/fundraising/ContributorRestrictions.sol
   It requires the following parameters: 1/ 'SwarmPoweredFundraise address' and 2/ 'number of contributors' want to allow for this fundraise
15. Goto 'SwarmPoweredFundraise' deployed contract and complete the remaining setup using 'setupContract()' function.'setupContract' requires many parameters like 'SRC20 token price', 'minimum amount of contribution', 'maximum amount of contribution', 'AffiliateManager address', 'ContributorRestrictions address', 'GetRateMinter address' and 'lock' or 'unlock' contributions
16. Goto 'SRC20' deployed contract and set 'SwarmPoweredFundraise' address using 'setFundRaiseAddr()' function
17. Goto 'ContributorRestrictions' deployed contract and whitelist all your contributors using 'whitelistAccount()' function. After this contributors can contribute to fundraise.
18. Once fundraise is completed, issuer can call 'stakeAndMint'. This function will do the following in one process: 1/ staking his equivalent SWM tokens, 2/ minting SRC20 tokens and 3/ withdrawing total contributor funds to contract owner 
