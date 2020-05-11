# Swarm Powered Fundraise Contract

* **Smart Contract:** specific to a Swarm Powered Fundraise for a specific SRC20
* **Created:**  Step X \(final step\) in the deployment of a Swarm Powered Fundraise; this contract references all other previously deployed contracts related to this fundraise 
* **Purpose:** Operates the actual SwarmPoweredFundraise; finalizes via stakeToMint
* **Example:**  TBD

## Feature Description

### Read Functions

| Function | Description |
| :--- | :--- |
| `label()` returns `(string)` | The label of the current fundraise |
| `startDate()` returns `(uint256)` | Start date of the fundraise in UNIX time |
| `endDate()` returns `(uint256)` | End date of the fundraise in UNIX time |
| `minAmountBCY()` returns `(uint256)` | Minimum amount accepted as contribution in base currency |
| `maxAmountBCY()` returns `(uint256)` | Maximum amount accepted as contribution in base currency |
| `expirationTime()` returns `(uint256)` | Time required for the issuer to stake and mint security tokens after the fundraise has been successfully completed. If the expiration time is reached, all contributors are able to get a refund |
| `src20()` returns `(address)` | The SRC20 token that is being offered as a security |
| `minter()` returns `(address)` | The contract that is responsible for minting the security tokens after the stake has been made |
| `affiliateManager()` returns `(address)` | The contract address of the Affiliate Manager contract which is responsible for managing affiliate addresses, links and commissions |
| `contributorRestrictions()` returns `(address)` | The contract address of the Contributor Restrictions contract which is responsible for handling contributor restrictions |
| `currencyRegistry()` returns `(address)` | The contract address of the Currency Registry which is responsible for managing accepted currencies in the fundraise |
| `offchainContributionsAllowed()` returns `(bool)` | Returns true if off-chain contributions are allowed. If off chain contributions are allowed the token manager can manually input contributions into the contract |
| `softCapBCY()` returns `(uint256)` | The soft cap amount in base currency |
| `hardCapBCY()` returns `(uint256)` | The hard cap amount in base currency |
| `SRC20tokenPriceBCY()` returns `(uint256)` | The price of each SRC20 token being sold in base currency. If this is set to 0 the value will be calculated based off of tokens to mint |
| `SRC20tokensToMint()` returns `(uint256)` | The amount of SRC20 tokens that are for sale and will be minted. It will be 0 if the fundraising is based off of a token price |
| `fundraiseAmountBCY()` returns `(uint256)` | The amount raised in base currency |
| `numberOfContributors()` returns `(uint256)` | The total number of unique addresses that have contributed to the fundraise |
| `totalIssuerWithdrawalsBCY()` returns `(uint256)` | The total amount the issuer can withdraw in base currency |
| `issuerWallet()` returns `(address)` | Returns the address of the wallet which will receive the raised funds |
| `isFinished()` returns `(bool)` | Returns true if the fundraising has been cancelled or successfully finished&lt; |
| `setupCompleted()` returns `(bool)` | Returns true if the fundraising set up is complete |
| `contributionsLocked()` returns `(bool)` | Returns true if contributions are locked. This means contributors are not able to obtain a refund |
| `contributionsList[address]` returns `(array)` | Each contributor address holds an array of a Contribution structure like this `struct Contribution {address currency;uint256 amount;uint256 sequence;ContributionStatus status;}` |
| `bufferedContributions[address][address]` returns `(uint256)` | These are contributions that have yet to be counted as valid; the first parameter is the contributor and the second is the currency address in this format `bufferedContributions[contributor_address][currency_address]= amount contributed` |
| `bufferedSums[address]` returns `(uint256)` | Total sum of pending contributions per currency address |
| `qualifiedContributions[address][address]` returns `(uint256)` | These are contributions that have been qualified and count in the fundraise. The first parameter is the contributor and the second is the currency address |
| `qualifiedSums[address]` returns `(uint256)` | Total sum of qualified contributions per currency address |
| `historicalBalance[address]` returns `(array)` | An array of Balance structures per currency address. `struct Balance {uint256 sequence;uint256 balance;}` |

### Write Functions

| Function | Description |
| :--- | :--- |
| `setupContract(uint256, uint256, address, address, bool)` | This function finishes setting up the contract once it has been deployed. The parameters are the following: 1/ Minimum contribution amount accepted in base currency; 2/ Maximum contribution amount accepted in base currency; 3/ Affiliate Manager contract address; 4/ Contributor Restrictions contract address; 5/ A boolean that sets if the contributions are locked |
| `cancelFundraise() returns (bool)` | It cancels the fundraise; this function can only be called by the contract owner \(token issuer\) |
| `getContributionsBCY(address, bool)` returns `(uint256)` | Returns the contributor’s sum of contributions in base currency; the contributor’s address is the first parameter and the second parameter is a boolean for qualified contributions \(_true_\) or pending contributions \(_false_\) |
| `addOffchainContribution(address, address, uint256)` returns `(bool)` | If off-chain contributions are allowed the token issuer can add contributions manually so the contract can later mint and distribute tokens for manual contributions; this feature requires trust on the part of the token issuer |
| `contribute(address, uint256, string)` returns `(bool)` | Allow contributions of ERC20 tokens that are registered in the `Currency Registry` contract. The first parameter is the address of the ERC20, the second is the amount in Wei and the third is the affiliate link if there is one; e.g. to contribute 100 DAI with affiliate link name affiliate use `contribute("0x6b175474e89094c44da98b954eedeac495271d0f",100000000000000000000,"affiliate")` |
| `getRefund()` returns `(bool)` | Allow a user to get ERC20 and ETH refunds if the fundraise has passed expiration time or has been cancelled |
| `acceptContributor(address)` returns `(bool)` | Function that can only be called by the Contributor Restriction smart contract after a user has been whitelisted by the issuer |
| `removeContributor(address)` returns `(bool)` | Function that can only be called by the Contributor Restriction smart contract after a user's address has been unwhitelisted by the token issuer |
| `stakeAndMint(address, uint256)` returns `(bool)` | Allow token issuer to stake SWM tokens in order to mint SRC20 tokens. The token issuer can either use `ISOP` or stake directly if they have the required SWM. The `stakeAndMint()` function will also conclude the fundraise by internally calling the function `finishFundraise()`. When `stakeAndMint()` finalizes the fundraise, that the people whitelisted for a fundraise are automatically added to the SRC20 Transfer Rules via `bulkWhitelistAccount()`. Otherwise `stakeAndMint()` could run into problems because the holders are not able to hold the newly minted SRC20 tokens |
| `claimTokens()` returns `(uint256)` | Allow contributors to claim their portion of SRC20 tokens after the fundraising is successfully over |

