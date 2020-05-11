# Asset Registry Contract

* **Smart Contract:** globally across all SRC20
* **Created:** pre-exists / created only once
* **Purpose:** Registry of asset data for all SRC20 tokens (meta data, esp. NAV)
* **Example:**  [On Ropsten](https://ropsten.etherscan.io/address/0x54f9b26edc46bd4beaf70ab2771b7ec178241932#code)  

## Feature Description

**Glossary**

| Item | Description |
| :--- | :--- |
| KYA (Know Your Asset) | The intent of KYA is to create cryptographically-proven single-source-of-truth for metadata of a specific SRC20 and the asset it represents; token issuers can add and update dozens of parameters and attributes of their project, store them on a URL or IPFS file; this allows investors to have unfettered access to a full history of data change over the life-cycle of the token |
| NAV (NetAssetValue) | NAV describes the value of the asset which is tokenized by a specific SRC20; it’s a common value in capital markets to describe the value of an asset and is based on underlying reports and assessments about the asset; as NAV represents the value of assets on the Swarm network it is used as the key value to determine the required SWM staking amounts for each SRC20 token |

**Read Functions**

| Function | Description |
| :--- | :--- |
| `getNetAssetValueUSD()` | Returns the registered NAV for a specific SRC20 |
| `_src20Factory()` returns `(address)` | (...) |
| `owner()` returns `(address)` | Returns the address of the contract owner |
| `isOwner()` returns `(bool)` | Returns _true_ if the caller is the contract owner |
| `assetList()` returns `kyaHash(bytes32), kyaUrl(string), netAssetValueUSD(uint256)` | Returns all KYA data (NAV, KYA hash, KYA URL) registered in this contract for a specific SRC20 |
| `getKYA()` returns `(bytes32), (string)` | Returns the KYA data (KYA hash, KYA URL) registered in this contract for a specific SRC20 |

**Write Functions**

| Function | Description |
| :--- | :--- |
| `addAsset()` | Creates a new record for of KYA data (NAV, KYA hash, KYA URL) for a specific SRC20 in this contract |
| `renounceOwnership()` | Contract owner can renounce ownership of the contract |
| `updateNetAssetValueUSD()` | Updates the NAV value for a specific SRC20 |
| `TransferOwnership()` returns `newOwner(address)` | Transfers ownership of this contract to another address |
| `udateKYA()` | Updates the KYA data (KYA hash, KYA URL) registered in this contract for a specific SRC20 |