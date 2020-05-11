# Transfer Rules Contract

* **Smart Contract:** SRC20 specific
* **Created:** Step 1 in SRC20 deployment \(see [Swarm Tokenization App](https://swarm.app/)\)
* **Purpose:** Manages whitelists and greylists that permits addresses to hold a specific SRC20 token
* **Example:**  [NUVO on Ropsten](https://ropsten.etherscan.io/address/0xad872227FBCEE4271a2F89C4c9B7df0cc86E0e71#code) 

## Feature Description

**Glossary**

| Item | Description |
| :--- | :--- |
| Whitelist | List of addresses able to hold and transfer the specific SRC20 token referring to this `Transfer Rules` contract without requiring approval by the token issuer or an authority |
| Greylist | List of addresses able to hold and transfer SRC20 token referring to this `Transfer Rules` contract only with approval by an Authority, as set within the Rules contract. If a transfer of tokens is attempted where at least one of the addresses is on the greylist, a request for approval is created in the `Transfer Rules` contract of the corresponding SRC20, for the token issuer to approve/reject. |

**Read Functions**

| Function | Description |
| :--- | :--- |
| `_whitelisted()` | Returns if an address is whitelisted |
| `_reqNumber()` | Returns the index of the most recent greylist transfer request |
| `_transferReq()` | Returns the details of a specific greylist transfer request. Returns the from address, to address and the value to be transferred. **Note: To view the details of \_reqNumber “1” use \_transferReq “0” and so on.** |
| `_greyList()` | Returns if an address is greylisted |
| `_src20()` | Displays the address of the corresponding SRC20 token contract \(after it is created\) |
| `owner()` | Displays the address of the contract owner |
| `isGreyListed()` | Returns if an address is greylisted |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `bulkUnGreyListAccount()` | Function to remove multiple addresses from the whitelist. Each account must be separated by a comma \(e.g. \[0x00, 0x00, 0x00\]\). Can only be called by an Authority, as set within the Rules contract |
| `doTransfer()` | Internal function when setting up a transfer. It is executed when transferring SRC20 tokens that checks if the transfer can successfully execute respecting transfer restrictions. If both addresses are on the whitelist, the transfer can go through. If either address is in the greylist, it creates a transfer authorization request. |
| `authorize()` | Internal function callable from another contract to check if a specific  transfer of this SRC20 requires authorization. It returns true if an \`address from\` is either in the whitelist or greylist AND if the \`address to\` is also either in the whitelist or greylist |
| `cancelTransferRequest()` | Cancels a specific transfer request. Can only be called by initiator of transfer request |
| `bulkUnWhitelistAccount()` | Owner can call this function to remove multiple addresses from the whitelist. Each account must be separated by a comma \(e.g. \[0x00, 0x00, 0x00\]\) Can only be called by an Authority, as set within the Rules contract |
| `whitelistAccount()` | Adds a single address to the whitelist. Can only be called by the contract owner. |
| `renounceOwnership()` | Contract owner can renounce ownership of the contract |
| `bulkWhitelistAccount()` | Adds multiple addresses to the whitelist. Each account must be separated by a comma \(e.g. \[0x00, 0x00, 0x00\]\). Can only be called by the contract owner. |
| `unGreyListAccount()` | Removes a single address from the greylist. Can only be called by the contract owner. |
| `transferApproval()` | For token issuer to approve pending transfers. Note, to approve `transferReq` “3” , enter `reqNumber` “2”. |
| `bulkGreyListAccount()` | Adds multiple addresses to the greylist. Each account must be separated by a comma \(e.g.. Ex. \[0x00, 0x00, 0x00\)\]. Can only be called by the contract owner. |
| `GreyListAccount()` | Adds a single address to the greylist. Can only be called by the contract owner. |
| `unWhiteListAccount()` | Removes a single address from the whitelist. Can only be called by the contract owner. |
| `transferOwnership()` | Transfers ownership of this contract to another address. Can only be called by the contract owner. |
| `setSRC()` | Registers this Transfer Rules contract with a specific  SRC20 token contract for which these rules apply. The Transfer Rules contract is deployed in advance of the SRC20 Token contract and therefore requires this reference set once after its creation. Can only be set once and is disabled after the creation of the contract. Calling it subsequently will return an error |

