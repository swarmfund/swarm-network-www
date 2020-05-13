# SRC20Factory Contract

* **Smart Contract:** globally across all SRC20
* **Created:** pre-exists / created once
* **Purpose:** Manages the minting of SRC20 and corresponding SWM stakes of additional  tokens added to an existing SRC20 
* **Example:**  [On Ropsten](https://ropsten.etherscan.io/address/0xe0e57388e696c4db04643147070532111b21b8e8#code)  

## Feature Description

**Read Functions**

| Function | Description |
| :--- | :--- |
| none |  |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `create()` | Creates new SRC20 contract using all the named parameters. Expects token properties and desired capabilities of the token. Only SRC20Factory owner can call this function. Emits SRC20Created event with address of new token. |
