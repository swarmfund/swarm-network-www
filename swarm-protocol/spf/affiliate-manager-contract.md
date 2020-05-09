# Affiliate Manager Contract

* **Smart Contract:** specific to a Swarm Powered Fundraise for a specific SRC20
* **Created:**  Step X in the deployment of a Swarm Powered Fundraise and then referenced in the Swarm Powered Fundraise contract
* **Purpose:** Registers all currencies that will be accepted in a specific Swarm Powered Fundraise
* **Example:**  TBD

## Feature Description

### Read Functions

| Function | Description |
| :--- | :--- |
| `affiliateLinks(address)` returns `(string)` | Returns the affiliate link of an affiliate address |
| `affiliates(address)` returns `(struct)` | Returns the Affiliate object from the affiliate address: `struct Affiliate {string affiliateLink;string affiliateLink;uint256 percentage;}` |
| `getAffiliate(string)` returns `(address, uint256)` | Returns the address and percentage amount of an affiliate. It takes the affiliate link as a parameter |
| `isOwner()` returns `(bool)` | Returns true if the calling address is the contract owner |
| `owner()` returns `(address)` | Returns the address of the owner of the contract |

### Write Functions

| Function | Description |
| :--- | :--- |
| `removeAffiliate(address)` returns `(bool)` | Removes an affiliate from the list of affiliates accepted in a Swarm Powered Fundraise; the parameter is the address of the affiliate wallet |
| `setupAffiliate(address, string, uint256)` returns `(bool)` | Setup a new affiliate; the first parameter is the address of the affiliate’s wallet, the second is the affiliate link and the third is the participation percentage amount that determines participation of the affiliate whenever a contribution references the affiliate link |
| `renounceOwnership()` | Contract owner can renounce ownership of the contract |
| `transferOwnership()` | Transfers ownership of this Affiliate Manager contract to a new contract owner |

