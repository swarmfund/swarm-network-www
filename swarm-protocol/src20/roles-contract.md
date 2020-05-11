# Roles Contract

* **Smart Contract:** SRC20 specific
* **Created:** Step 3 in SRC20 deployment \(see [Swarm Tokenization App](https://swarm.app/)\)
* **Purpose:** Manages the addresses that can perform restricted actions for an SRC20 as defined by the contract owner. SRC20 tokens can have four types of roles: Owner, Authority, Manager and Delegate
* **Example:**  [NUVO on Ropsten](https://ropsten.etherscan.io/address/0x32da71b47888a8c900761dff4fecd37c2e2da654#code)  

## Feature Description

**Glossary**

| Item | Description |
| :--- | :--- |


| Owner | Owner is the owner of the \`Roles\` smart contract |
| :--- | :--- |


| Delegate | Address responsible for updating the KYA document, Net Asset Value, transfer restrictions and rules and perform bulk transfers that bypass whitelist and greylist. |
| :--- | :--- |


| Authority | Address authorized to maintain the white and greylists \(add/remove\) for a specific SRC20 token, as well as authorize transfers subject to a greylist |
| :--- | :--- |


| Manager | There is one manager, which is a smart contract responsible for minting or burning tokens. It is initially set to be the SRC20 Registry contract where you can increase or decrease the supply.  |
| :--- | :--- |


| Function | Description |
| :--- | :--- |
| `isDelegate` | Returns _true_/_false_ whether an address is a Delegate for this token contract |
| `isAuthority` | Returns _true_/_false_ whether an address is an Authority for this token contract |
| `manager` | Returns the address of the Manager contract. This is normally the address of the `SRC20Registry` contract, where staking and minting is executed |
| `owner` | Returns the address of the contract owner |
| `isOwner` | Returns _true_ if the caller is the current owner |
| `isManager` | Returns _true_ if the caller is the current Manager |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `renounceManagement` | Relinquish the ability to manage this contract. _**Attention:**_ _**If a manager renounces management there is no possible way to mint or burn SRC20 tokens anymore**_ |
| `addAuthority` | Add an address that is able to authorize direct SRC20 token transfers, onchain or offchain. Can only be called by the owner. |
| `removeDelegate` | Remove an address from being able to perform delegate functions. Can only be called by the owner. |
| `renounceOwnership` | Can only be called by the owner and it sets the owner address to `0x0` |
| `removeAuthority` | Removes an address from being able to authorize direct SRC20 token transfers, onchain or offchain. Can only be called by the owner. |
| `transferManagement` | A manager can transfer their role to a new address. |
| `addDelegate` | Add an address that is able to perform delegate only functions. Can only be called by the owner. |
| `transferOwnership` | An owner can transfer their role to a new address or to a multisig wallet or to a multisig wallet. |

