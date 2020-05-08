# SRC20 Registry Contract

* **Smart Contract:** globally across all SRC20
* **Created:** pre-exists / created only once
* **Purpose:** Registry of all SRC20 tokens created and the associated SWM stakes
* **Example:**  [On Ropsten](https://ropsten.etherscan.io/address/0xf37fdada55b07838cb865d9f2a9d449109eb9521#code)  

## Feature Description

**Glossary**

| Item | Description |
| :--- | :--- |
| (SWM\) Stake | On Swarm token issuers are required to stake an amount of SWM token to trigger the minting and distribution of SRC20 tokens; the required stake amounts follow a [staking rate card](https://docs.swarm.fund/SWM_Issuance_Staking_Rate_Card.png) which has been adopted as a network policy by the Swarm Network |

**Read Functions**

| Function | Description |
| :--- | :--- |
| `swmNeeded` returns `(uint256)` | Returns the SWM stake amount needed to mint an additional amount of specific SRC20 tokens; this function translates the Net Asset Value into USD denominated staking amounts based on the network policy and then uses the referenced SWMPriceOracle to translate them into SWM values based on current prices |
| `contains` returns `(bool)` | Returns _true_ when a SRC20 token address is successfully registered with this SRC20 Registry Contract |
| `getStake` returns `(uint256)` | Returns the amount of SWM staked for a specific SRC20 |
| `owner` returns `(address)` | Returns the address of the contract owner |
| `isOwner` returns `(bool)` | Returns _true_ if the caller is the contract owner |
| `calcTokens` | src20 (address\), swmValue (uint256\) returns uint256 |
| `getMinter` returns `(address)` | returns address |
| `getTokenOwner` returns `(address)` | Returns the address of the owner (and staker\) of a specific SRC20 |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `remove` returns `(address)` | token (address\) |
| `addFactory` returns `account(address)` | account (address\) |
| `removeMinter` returns `minter(address)` | minter (address\) |
| `removeFactory` returns `account(address)` | account (address\) |
| `renounceManagement` returns `src20(address)` | src20 (address\) |
| `getSrc20toSwmRatio` returns `src20(address)` | src20 (address\) |
| `increaseSupply` | src20 (address\), swmAccount(address\), srcValue(unit256\) |
| `renounceOwnership()` | Contract owner can renounce ownership of the contract |
| `transferManagement()` | src20 (address\), newManager(address\) |
| `addMinter()` | minter (address\) |
| `mintSupply` | src20 (address\), swmAccount(address\), swmValue(unit256\), srcValue(unit256\) |
| `put` | token (address\), roles (address\), tokenOwner (address\), minter (address\) |
| `decreaseSupply` | src20 (address\), swmAccount(address\), srcValue(unit256\) |
| `transferOwnership` | Transfers ownership of this contract to another address. Can only be called by the contract owner. |

