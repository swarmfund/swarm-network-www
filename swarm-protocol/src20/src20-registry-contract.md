# SRC20 Registry Contract

* **Smart Contract:** globally across all SRC20
* **Created:** pre-exists / created only once
* **Purpose:** Registry of all SRC20 tokens created and the associated SWM stakes
* **Example:**  [On Ropsten](https://ropsten.etherscan.io/address/0xf37fdada55b07838cb865d9f2a9d449109eb9521#code)  

## Feature Description

**Glossary**

| Item | Description |
| :--- | :--- |
| (SWM) Stake | On Swarm token issuers are required to stake an amount of SWM token to trigger the minting and distribution of SRC20 tokens; the required stake amounts follow a [staking rate card](https://docs.swarm.fund/SWM_Issuance_Staking_Rate_Card.png) which has been adopted as a network policy by the Swarm Network |

**Read Functions**

| Function | Description |
| :--- | :--- |
| `swmNeeded()` returns `(uint256)` | Returns the SWM stake amount needed to mint an additional amount of specific SRC20 tokens; this function translates the Net Asset Value into USD denominated staking amounts based on the network policy and then uses the referenced SWMPriceOracle to translate them into SWM values based on current prices |
| `contains()` returns `(bool)` | Returns _true_ when a SRC20 token address is successfully registered with this `SRC20 Registry` contract |
| `getStake()` returns `(uint256)` | Returns the amount of SWM staked for a specific SRC20 |
| `owner()` returns `(address)` | Returns the address of the contract owner |
| `isOwner()` returns `(bool)` | Returns _true_ if the caller is the contract owner |
| `calcTokens()` | External function allowing users to check the corresponding amount of SRC20 tokens that can be minted for a SWM stake value; responds in SRC20 in Wei (e.g. 1 = 1 additional SRC20); This differs from the `calcStake()` function in the `Minter` contract which is for staking/minting a brand new token. This function instead is for calculating the additional incremental stake on an existing SRC20 token |
| `getMinter()` returns `(address)` | Returns address of the `Minter` contract for a specific SRC20 |
| `getTokenOwner()` returns `(address)` | Returns the address of the owner (and staker) of a specific SRC20 |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `remove()` returns `(bool)` | Removes specific SRC20 from the `SRC20 Registry`; can only be executed by the contract owner; returns _true_ on success |
| `addFactory()` returns `(bool)` | Adds new factory to the `SRC20 Registry` contract address that can register a specific SRC20 token; returns _true_ on success |
| `removeMinter()` returns `(bool)` | This proxy function removes a contract from the list of authorized minters; use the address of the `Minter` contract to remove; returns _true_ on success |
| `removeFactory()` returns `(bool)` | This proxy function removes a `SRC20Factory` contract that can register a specific SRC20 token; use the address of the `SRC20Factory`contract to remove; returns _true_ on success  |
| `renounceManagement()` returns `(bool)` | Allows the manager to renounce management for a specific SRC20 token address; returns _true_ on success |
| `getSrc20toSwmRatio()` returns `Amount()` | External function for calculating how much SWM tokens are needed to be staked in order to get 1 SRC20 token |
| `increaseSupply()`returns `(bool)` | This function the token issuer can call in order to increase his SRC20 supply and stake his tokens; enter parameters with  `src20` (address of src20 token contract), `swmAccount` (address from which stake tokens are going to be deducted), and `srcValue` (Value of desired SRC20 token supply increase in unit256/Wei); returns _true_ on success |
| `renounceOwnership()` | Contract owner can renounce ownership of the contract |
| `transferManagement()`returns `(bool)` | Allows the manager to transfer management for a specific SRC20 token address to a new address; returns _true_ on success |
| `addMinter()` | This proxy function adds a contract to the list of authorized minters |
| `mintSupply()` returns `(bool)` | Mints additional supply of a specific SRC20 token based on SWM token stake; can be used for initial supply and subsequent minting of new SRC20 tokens; When used, Manager will update SWM/SRC20 values in this call and use it for token owner's `increaseSupply()` / `decreaseSupply()` calls, minting/burning SRC20 based on current SWM/SRC20 ratio. Only owner (Swarm network controlled address) of this contract can invoke this method; returns _true_ on success |
| `put()` | Adds a SRC20 token to the `SRC20 Registry`; only factories can add; returns _true_ on success |
| `decreaseSupply()` returns `(bool)` | This function the token issuer can call in order to decrease his SRC20 supply and receive his SWM stake; enter parameters with `src20` (Address of src20 token contract), `swmAccount` (address to which SWM stake tokens will be returned), and `srcValue` (Value of desired SRC20 token supply decrease in unit256/Wei); returns _true_ on success |
| `transferOwnership()` | Transfers ownership of this contract to another address. Can only be called by the contract owner |