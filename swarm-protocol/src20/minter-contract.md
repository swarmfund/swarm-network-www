# Minter Contract

* **Smart Contract:** globally across all SRC20
* **Created:** pre-exists / created once
* **Purpose:** Manages the minting of SRC20 and corresponding SWM stakes of additional  tokens added to an existing SRC20 
* **Example:**  [On Ropsten](https://ropsten.etherscan.io/address/0xe0e57388e696c4db04643147070532111b21b8e8#code)  

## Feature Description

**Read Functions**

| Function | Description |
| :--- | :--- |
| `calcStake` | src20\(address\), netAssetValueUSD\(uint256\)   Returns the SWM stake amount needed to mint an additional amount of specific SRC20 tokens; this function translates the Net Asset Value into USD denominated staking amounts based on the network policy and then uses the referenced SWMPriceOracle to translate them into SWM values based on current prices |
| `_SWMPriceOracle` returns `(address)` | Displays the address for the price oracle contract used to determine the SWM price |
| `_registry` returns `\(address)` | Displays the SRC20 registry contract used in this contract |
| `_asset` returns `\(address)` | ??? |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `stakeAndMint` | src20\(address\), numSRC20Tokens\(uint256\) |

