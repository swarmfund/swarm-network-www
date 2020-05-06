# Test



### 

### SRC20 Smart Contract Index

#### Smart contracts created per each new security token \(one per SRC20 token\)

|  |
| :--- |




#### Smart contracts created per each new security token \(one per SRC20 token\)

| SC Name | Description | Example |
| :--- | :--- | :--- |
| Transfer Rules | Manages whitelists and greylists for holders of a specific SRC20 token. | [Link](https://ropsten.etherscan.io/address/0xad872227FBCEE4271a2F89C4c9B7df0cc86E0e71#code) |
| Token Features | Managing additional token contract features for a specific SRC20 token, and for checking the state of the token contract \(e.g whether it is currently paused for transfers\). | [Link](https://ropsten.etherscan.io/address/0x31830850853A9fa8cb7CC7Fbf5bD5f807B8B5B8e#code) |
| Roles | Manages the addresses that can perform restricted actions for a specific SRC20 token as defined by the contract owner. SRC20 tokens can have four types of roles: Owner, Authority, Manager and Delegate. | [Link](https://ropsten.etherscan.io/address/0x32da71b47888a8c900761dff4fecd37c2e2da654#code) |

### Smart Contract Feature Description - Specific Contracts

The following four contracts relate to and are referenced from a unique SRC20 security token.

### **SRC20 Token - Smart Contract**

| Created | Final Step in SWARM Tokenization App |
| :--- | :--- |
| Purpose | Creates and configures a specific SRC20 Security Token |
| Example | [NUVO on Ropsten](https://ropsten.etherscan.io/token/0xAe3CB523328ae4A8E5aFa6E1b856c7F6C67a7d28) |

#### Read Functions
| Name | Description
| :--- | :--- |
| \_allowances | See Allowances below |
| name | Name of this SRC20 token as set by the issuer |
| totalSupply | Current SRC20 supply \(in Wei\) |
| decimals | Number of decimal places this SRC20 token is defined to |
| \_maxTotalSupply | Maximum supply of this SRC20 tokens that can be minted \(in Wei\) |
| \_totalSupply | Same as totalSupply |
| \_restrictions | Address of the Transfer Restriction contract governing transfers for this SRC20 \(not yet implemented\) |
| \_balances | Returns the token balance for this SRC20 of a specific address |
| balanceOf | Returns the token balance for this SRC20 of a specific address |
| \_roles | Address of the Roles smart contract governing roles for this SRC20 |
| owner | Address of the owner of this SRC20 token contract |
| isOwner | Returns _true_ if the caller is the current contract owner address of this SRC20 |
| symbol | Ticker code or symbol of this SRC20 token |
| getTransferNonce | Returns the next nonce expected by transfer functions. Nonce is incremented after each successful transfer |
| \_assetRegistry | Address of the AssetRegistry contract which holds the off-chain properties of all assets tokenized by SRC20 tokens. |
| \_features | Address of the TokenFeatures smart contract for this SRC20 token |
| allowance | Returns the number of tokens a spender address has been allowed to spend on behalf of and from the owner address. |
| \_rules | Address of the TokenRules smart contract for this SRC20 token |
| getTransferNonce | Returns next nonce expected by transfer functions for a certain address |

#### Write Functions
| Name | Description
| :--- | :--- |
| transferTokenForced | **Only token issuers can call this function.** Transfers tokens from one address to another. This call only requires that _from_ address has sufficient tokens; other checks are skipped. \ \* Requires 'ForceTransfer' feature enabled |
| approve | Approve the _spender address_ to spend the specified amount of tokens on behalf of the function caller’s address |
| bulkTransfer | Perform multiple token transfers from the token owner's address. The tokens must already be minted. Can only be executed by a delegate \ 1. Token issuer must first specify a delegate \(owner is not a delegate by default\) to use this function \ 2. Token issuer must call approve\(\) function to allow delegate to spend |
| burnAccount | **Only token issuers can call this function.** Burns an amount of tokens from a specified address. Tokens are sent to the zero address |
| transferFrom \[from, to, value\] | Internal function used by the Transfer Rules contract of this SRC20 to check if a transfer requires an authorization |
| transferToken | Transfer token to specified address. Caller needs to provide an authorization signature obtained from MAP API, signed by an authority accepted by the token issuer. _Used by the transfer function after transfer validity is acquired_ |
| increaseAllowance | Increase the number of SRC20 tokens, by a _value_, that an already permitted spender address can spend on behalf of the function caller |
| mint | Can only be called by Mint Contract and mints additional tokens for this SRC20. Requires a SWM stake to be made simultaneously within StakeandMint\(\) function in the Mint contract |
| updateRestrictionsAndRules | Updates the addresses of the Restrictions and/or rules \(TransferRules\) contract applied to this SRC20 token. You can update either one or both. |
| renounceOwnership | Contract owner can renounce ownership of this SRC20 contract. All functions that can only be called by the owner will subsequently no longer be available |
| encodedBulkTransfer | Only a delegate can call this function. Performs multiple transfers of this SRC20 from the token owner's address. The tokens must already be minted and in the owners address. If this function is called by someone other than the owner \(must be a delegate defined in the Roles contract of this SRC20\), the owner has to call approve\(\) first to set up the delegate's allowance. Data needs to be packed correctly before calling this function |
| burn | Can only be called by Owner. Burns an amount of tokens from a specified _address._ _Value_ describes the amount in Wei |
| decreaseAllowance | Reduces by an amount_,_ the number of SRC20 tokens that can be spent by a _spender address_ from the caller’s address. _Value_ describes the amount in Wei |
| transfer | Transfer call executed by TransferRules contract of this SRC20 after a restricted transfer is authorized. SRC20 tokens are transferred from the token contract to the recipient’s address |
| transferTokenFrom | Transfers an amount of SRC20 token to specified address. Caller needs to provide an authorization signature obtained from MAP API, signed by an authority accepted by the token issuer. _Used by the transfer function when authorization is requested_ |
| executeTransfer | Called by the TransferRules contract of this SRC20 |
| transferOwnership | Transfers ownership of this SRC20 contract to another address |
| OwnershipTransferred | Internal function called by contract to set initial ownership and when ownership is transferred |
| ManagementTransferred | Called by contract to set initial manager and when manager address is transferred |
| RestrictionsAndRulesUpdated | Internal function to update the restrictions and rules contracts. |
| Transfer | Main transfer call |
| Approval | Internal function used by the contract to check if spender has approval to spend on behalf of the contract owner |

