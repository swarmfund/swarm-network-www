# Roles Contract

* **Smart Contract:** SRC20 specific
* **Created:** Step 3 in SRC20 deployment \(see [Swarm Tokenization App](https://swarm.app/)\)
* **Purpose:** Manages the addresses that can perform restricted actions for an SRC20 as defined by the contract owner. SRC20 tokens can have four types of roles: Owner, Authority, Manager and Delegate
* **Example:**  [NUVO on Ropsten](https://ropsten.etherscan.io/address/0x32da71b47888a8c900761dff4fecd37c2e2da654#code)  

### Feature Description

**Glossary**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Item</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Owner</td>
      <td style="text-align:left">Owner is the owner of the `Roles` smart contract</td>
    </tr>
    <tr>
      <td style="text-align:left">Delegate</td>
      <td style="text-align:left">Address responsible for updating the KYA document, Net Asset Value, transfer
        restrictions and rules and perform bulk transfers that bypass whitelist
        and greylist.</td>
    </tr>
    <tr>
      <td style="text-align:left">Authority</td>
      <td style="text-align:left">Is able to authorize SRC20 token direct transfers (MAP) onchain or offchain.</td>
    </tr>
    <tr>
      <td style="text-align:left">Manager</td>
      <td style="text-align:left">
        <p>The manager is responsible for minting or burning tokens. \ \ There can
          be only one Manager per SRC20 token.</p>
        <p>Managers can perform the following action:</p>
        <ul>
          <li>`<em><b>Renounce Management</b></em>` - If a manager renounces management
            there is no possible way to mint or burn SRC20 tokens anymore.</li>
          <li>
            <p>`<em><b>Transfer Management</b></em>` - A manager can transfer their role
              to a new address or to a multisig wallet.</p>
            <p>Managers are proxy accounts for the owner of the token. \ \ Only the `<b>Owner</b>`
              of the Roles contract can call the decrease or increase function from the
              `<b>Manager Account</b>`</p>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>**Read Functions**

| Function | Description |
| :--- | :--- |
| \`isDelegate\` | Returns _true_/_false_ whether an address is a Delegate for this token contract |
| \`isAuthority\` | Returns _true_/_fals_e whether an address is an Authority for this token contract |
| \`manager\` | Returns the address of the Manager contract. This is normally the address of the \`SRC20Registry\` contract, where staking and minting is executed |
| \`owner\` | Returns the address of the contract owner |
| \`isOwner\` | Returns _true_ if the caller is the current owner |
| \`isManager\` | Returns _true_ if the caller is the current Manager |

**Write Functions**

| Function | Description |
| :--- | :--- |
| \`renounceManagement\` | Relinquish the ability to manage this contract. _**Attention:**_ _**If a manager renounces management there is no possible way to mint or burn SRC20 tokens anymore**_ |
| \`addAuthority\` | Add an address that is able to authorize direct SRC20 token transfers, onchain or offchain. Can only be called by the owner. |
| \`removeDelegate\` | Remove an address from being able to perform delegate functions. Can only be called by the owner. |
| \`renounceOwnership\` | Can only be called by the owner and it sets the owner address to \`0x0\` |
| \`removeAuthority\` | Removes an address from being able to authorize direct SRC20 token transfers, onchain or offchain. Can only be called by the owner. |
| \`transferManagement\` | A manager can transfer their role to a new address. |
| \`addDelegate\` | Add an address that is able to perform delegate only functions. Can only be called by the owner. |
| \`transferOwnership\` | An owner can transfer their role to a new address or to a multisig wallet or to a multisig wallet. |

