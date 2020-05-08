# Token Features Contract

* **Smart Contract:** SRC20 specific
* **Created:** Step 2 in SRC20 deployment \(see [Swarm Tokenization App](https://swarm.app/)\)
* **Purpose:** Manages additional token contract features for a specific SCR20 token contract, and checks the state of the SRC20 token contract \(e.g. whether it is currently paused for transfers\)
* **Example:**  [NUVO on Ropsten](https://ropsten.etherscan.io/address/0x31830850853A9fa8cb7CC7Fbf5bD5f807B8B5B8e#code) 

## Feature Description

**Read Functions**

| Function | Description |
| :--- | :--- |
| `isTokenPaused` | Displays _true_/_false_ based on whether the SRC20 token contract is paused |
| `pausable` | Displays the index of this feature, for checking if enabled. Index = 2 |
| `paused` | Displays _true_/_false_ based on whether the SRC20 token contract is paused |
| `isEnabled` | Returns _true_/_false_ based on whether a specific SRC20 token feature is enabled. Requires the user to enter the index of the feature. |
| `accountBurning` | Displays the index of this feature, for checking if enabled. Index = 4 |
| `accountFreezing` | Displays the index of this feature, for checking if enabled. Index = 8 |
| `_enabledFeatures` | Internal function |
| `owner` | Returns the address of the contract owner |
| `isOwner` | Returns _true_ if the caller is the contract owner |
| `forceTransfer` | Displays the index of this feature, for checking if enabled. Index = 1 |
| `checkTransfer` | Call to check if a transfer of SRC20 tokens between two addresses will pass under any restrictions set by this Features contract. Transfer rules need to be checked separately in the Transfer Rules contract of this SRC20 |
| `isAccountFrozen` | Returns _true_/_false_ whether a specified account holding these SRC20 tokens is frozen, meaning it is disabled from being able to make transfers of any of this SRC20 token |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `pauseToken` | Pauses the SRC20 token. No transfers of any kind can take place while being paused. Can only be called by the contract owner if Pausable functionality is enabled |
| `renounceOwnership` | Leaves this Token Features contract without an owner. Can only be called by the contract owner. Subsequently, it will no longer be possible to call functions with `onlyOwner` modifiers, thereby removing any functionality that is only available to the contract owner. |
| `unfreezeAccount` | Unfreezes a specific address, enabling it to initiate transfers. Can only be called by the contract owner if `AccountFreezing` functionality is enabled. |
| `unPauseToken` | Reverses the pausing of a token and transfers for this SRC20 token will resume being possible. Can only be called by the contract owner if Pausable functionality is enabled. |
| `freezeAccount` | Freezes a specific address, disabling it from being able to initiate transfers of this SRC20 token. Can only be called by the contract owner if `AccountFreezing` functionality is enabled. |
| `transferOwnership` | Transfers ownership of this `Token Features` contract to a new contract owner. Can only be called by the contract owner. |

