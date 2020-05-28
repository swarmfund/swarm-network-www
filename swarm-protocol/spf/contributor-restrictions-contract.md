---
description: '- BETA -'
---

# Contributor Restrictions Contract

* **Smart Contract:** specific to a Swarm Powered Fundraise for a specific SRC20
* **Created:** review the [SPF Deployment Sequence](https://www.swarmnetwork.org/swarm-protocol/spf#deployment-sequence); then referenced in the Swarm Powered Fundraise contract 
* **Purpose:** Manages whitelist and restrictions for each contributor in a Swarm Powered Fundraise
* **Example:**  TBD

## Feature Description

### Read Functions

| Function | Description |
| :--- | :--- |
| `fundraise()` returns `(address)` | Returns the address of the Swarm Powered Fundraise contract that this Contributor Restrictions contract applies to |
| `maxContributors()` returns `(uint256)` | Returns the maximum number of contributors that can participate in a Swarm Powered Fundraise |
| `isAllowed(account)` returns `(bool)` | Checks if an account is on the whitelist of a Swarm Powered Fundraise and the contributor list has not reached the maximum number of contributors |
| `checkRestrictions(address)` returns `(bool)` | Checks if an account is on the whitelist and is not above the maximum number of contributors |

### Write Functions

| Function | Description |
| :--- | :--- |
| `whitelistAccount(address)` | Adds an address to the whitelist of a Swarm Powered Fundraise and accepts any pending contribution |
| `unWhitelistAccount(address)` | Removes an address from the whitelist of a Swarm Powered Fundraise and removes any qualified contributions by the address |
| `bulkWhitelistAccount(address[])` | Whitelists an array of addresses for a Swarm Powered Fundraise |
| `bulkUnWhitelistAccount(address[])` | Removes an array of addresses from the whitelist of a Swarm Powered Fundraise |

