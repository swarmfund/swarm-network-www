# SRC20 Token Contract

* **Smart Contract:** SRC20 specific
* **Created:** Final Step in SRC20 deployment (see [Swarm Tokenization App](https://swarm.app/))
* **Purpose:** Creates and configures a specific SRC20 token
* **Example:**  [NUVO on Ropsten](https://ropsten.etherscan.io/token/0xAe3CB523328ae4A8E5aFa6E1b856c7F6C67a7d28)  

## Feature Description

**Read Functions**

| Function | Description |
| :--- | :--- |
| `_allowances()` | See Allowances below |
| `name()` | Name of this SRC20 token as set by the issuer |
| `totalSupply()` | Current SRC20 supply (in Wei) |
| `decimals()` | Number of decimal places this SRC20 token is defined to |
| `_maxTotalSupply()` | Maximum supply of this SRC20 tokens that can be minted (in Wei) |
| `_totalSupply()` | Same as totalSupply |
| `_restrictions()` | Address of the Transfer Restriction contract governing transfers for this SRC20 _(not yet implemented; this function is for future reference)_ |
| `_balances()` | Returns the token balance for this SRC20 of a specific address |
| `balanceOf()` | Returns the token balance for this SRC20 of a specific address |
| `_roles()` | Address of the Roles smart contract governing roles for this SRC20 |
| `owner()` | Returns the address of the contract owner |
| `isOwner()` | Returns _true_ if the caller is the current contract owner address of this SRC20 |
| `symbol()` | Ticker code or symbol of this SRC20 token |
| `getTransferNonce()` | Returns the next nonce expected by transfer functions. Nonce is incremented after each successful transfer |
| `_assetRegistry()` | Address of the `AssetRegistry` contract which holds the off-chain properties of all assets tokenized by SRC20 tokens. |
| `_features()` | Address of the TokenFeatures smart contract for this SRC20 token |
| `allowance()` | Returns the number of tokens a spender address has been allowed to spend on behalf of and from the owner address. It means another address (spender) can be allowed to spend SRC20 residing in the function caller's address |
| `_rules()` | Address of the `Transfer Rules` contract for this SRC20 token |
| `getTransferNonce()` | Returns next nonce expected by transfer functions for a certain address |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `transferTokenForced()` | Transfers tokens from one address to another. This call only requires that `_from_ address` has sufficient tokens; other checks are skipped. Only token issuers can call this function and it requires the `ForceTransfer` feature to be enabled |
| `approve()` | Approve the `_spender address_` to spend the specified amount of tokens on behalf of the function caller’s address |
| `bulkTransfer()` | Perform multiple token transfers from the token owner's address. The tokens must already be minted. Can only be executed by a delegate  1. Token issuer must first specify a delegate (owner is not a delegate by default) to use this function  2. Token issuer must call `approve()` function to allow delegate to spend |
| `burnAccount()` | Burns an amount of tokens from a specified address. Tokens are sent to the zero address, Only token issuers can call this function |
| `transferFrom` [from, to, value] | Internal function used by the `Transfer Rules` contract of this SRC20 to check if a transfer requires an authorization |
| `transferToken()` | Transfer token to specified address. Caller needs to provide an authorization signature obtained from MAP API, signed by an authority accepted by the token issuer. _Used by the_ `_transfer_` _function after_ `_transfer validity_` _is acquired_ |
| `increaseAllowance()` | Increase the number of SRC20 tokens, by a _value_, that an already permitted spender address can spend on behalf of the function caller |
| `mint()` | Can only be called by `Minter` Contract and mints additional tokens for this SRC20. Requires a SWM stake to be made simultaneously within `stakeAndMint()` function in the `Minter` contract |
| `updateRestrictionsAndRules()` | Updates the addresses of the Restrictions contract and/or rules `Transfer Rules` contract for this SRC20 token. You can update either one or both, but will be required to enter the one that is not updated alongside the other one. |
| `renounceOwnership()` | Contract owner can renounce ownership of this contract. All functions that can only be called by the owner will subsequently no longer be available |
| `encodedBulkTransfer()` | Only a delegate can call this function. Performs multiple transfers of this SRC20 from the token owner's address. The tokens must already be minted and in the owners address. If this function is called by someone other than the owner (must be a delegate defined in the `Roles` contract of this SRC20, the owner has to call `approve()` first to set up the delegate's allowance. Data needs to be packed correctly before calling this function |
| `burn()` | Can only be called by Owner. Burns an amount of tokens from a specified _address._ _Value_ describes the amount in Wei |
| `decreaseAllowance()` | Reduces by an amount_,_ the number of SRC20 tokens that can be spent by a `_spender address_` from the `caller’s address`. `_Value_` describes the amount in Wei |
| `transfer()` | Transfer of an amount of this SRC20 tokens from the a sender address  to a recipient’s address respecting the `Transfer Rules` contract |
| `transferTokenFrom()` | Transfers an amount of SRC20 token to specified address. Caller needs to provide an authorization signature obtained from MAP API, signed by an authority accepted by the token issuer. _Used by the_ `transfer()` _function when authorization is requested_ |
| `executeTransfer()` | Called by the `Transfer Rules` contract of this SRC20 |
| `transferOwnership()` | Transfers ownership of this contract to another address. Can only be called by the contract owner. |

**Events**

| Event | Description |
| :--- | :--- |
| `OwnershipTransferred()` | Event created by contract when initial ownership is created or  when the ownership is transferred |
| `ManagementTransferred()` | Event created by contract when initial ownership is created or  when the ownership is transferred |
| `RestrictionsAndRulesUpdated()` | Event created by contract when the restrictions and rules contracts is updated |
| `Transfer()` | Event created by contract when a transfer occurs for this SRC20 respecting the `Transfer Rules` (white/greylists) |
| `Approval()` | Event created by contract when when a spender has received approval to spend on behalf of another holder of SRC20 tokens |