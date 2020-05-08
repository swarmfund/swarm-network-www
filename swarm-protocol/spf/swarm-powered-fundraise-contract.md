# Swarm Powered Fundraise Contract

* **Smart Contract:** specific to a Swarm Powered Fundraise for a specific SRC20
* **Created:**  Step X \(final step\) in the deployment of a Swarm Powered Fundraise; this contract references all other previously deployed contracts related to this fundraise 
* **Purpose:** Operates the actual SwarmPoweredFundraise; finalizes via stakeToMint
* **Example:**  TBD

## Feature Description

### Read Functions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">`label()` returns `(string)`</td>
      <td style="text-align:left">The label of the current fundraise</td>
    </tr>
    <tr>
      <td style="text-align:left">`startDate()` returns `(uint256)`</td>
      <td style="text-align:left">Start date of the fundraise in <a href="https://www.unixtimestamp.com/index.php">UNIX time</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`endDate()` returns `(uint256)`</td>
      <td style="text-align:left">End date of the fundraise in <a href="https://www.unixtimestamp.com/index.php">UNIX time</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`minAmountBCY()` returns `(uint256)`</td>
      <td style="text-align:left">Minimum amount accepted as contribution in base currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`maxAmountBCY()` returns `(uint256)`</td>
      <td style="text-align:left">Maximum amount accepted as contribution in base currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`expirationTime()` returns `(uint256)`</td>
      <td style="text-align:left">Time required for the issuer to stake and mint security tokens after the
        fundraise has been successfully completed. If the expiration time is reached,
        all contributors are able to get a refund</td>
    </tr>
    <tr>
      <td style="text-align:left">`src20()` returns `(address)`</td>
      <td style="text-align:left">The SRC20 token that is being offered as a security</td>
    </tr>
    <tr>
      <td style="text-align:left">`minter()` returns `(address)`</td>
      <td style="text-align:left">The contract that is responsible for minting the security tokens after
        the stake has been made</td>
    </tr>
    <tr>
      <td style="text-align:left">`affiliateManager()` returns `(address)`</td>
      <td style="text-align:left">The contract address of the Affiliate Manager contract which is responsible
        for managing affiliate addresses, links and commissions</td>
    </tr>
    <tr>
      <td style="text-align:left">`contributorRestrictions()` returns `(address)`</td>
      <td style="text-align:left">The contract address of the Contributor Restrictions contract which is
        responsible for handling contributor restrictions</td>
    </tr>
    <tr>
      <td style="text-align:left">`currencyRegistry()` returns `(address)`</td>
      <td style="text-align:left">The contract address of the Currency Registry which is responsible for
        managing accepted currencies in the fundraise</td>
    </tr>
    <tr>
      <td style="text-align:left">`offchainContributionsAllowed()` returns `(bool)`</td>
      <td style="text-align:left">Returns true if off-chain contributions are allowed. If off chain contributions
        are allowed the token manager can manually input contributions into the
        contract</td>
    </tr>
    <tr>
      <td style="text-align:left">`softCapBCY()` returns `(uint256)`</td>
      <td style="text-align:left">The soft cap amount in base currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`hardCapBCY()` returns `(uint256)`</td>
      <td style="text-align:left">The hard cap amount in base currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`SRC20tokenPriceBCY()` returns `(uint256)`</td>
      <td style="text-align:left">The price of each SRC20 token being sold in base currency. If this is
        set to 0 the value will be calculated based off of tokens to mint</td>
    </tr>
    <tr>
      <td style="text-align:left">`SRC20tokensToMint()` returns `(uint256)`</td>
      <td style="text-align:left">The amount of SRC20 tokens that are for sale and will be minted. It will
        be 0 if the fundraising is based off of a token price</td>
    </tr>
    <tr>
      <td style="text-align:left">`fundraiseAmountBCY()` returns `(uint256)`</td>
      <td style="text-align:left">The amount raised in base currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`numberOfContributors()` returns `(uint256)`</td>
      <td style="text-align:left">The total number of unique addresses that have contributed to the fundraise</td>
    </tr>
    <tr>
      <td style="text-align:left">`totalIssuerWithdrawalsBCY()` returns `(uint256)`</td>
      <td style="text-align:left">The total amount the issuer can withdraw in base currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`issuerWallet()` returns `(address)`</td>
      <td style="text-align:left">Returns the address of the wallet which will receive the raised funds</td>
    </tr>
    <tr>
      <td style="text-align:left">`isFinished()` returns `(bool)`</td>
      <td style="text-align:left">Returns true if the fundraising has been cancelled or successfully finished</td>
    </tr>
    <tr>
      <td style="text-align:left">`setupCompleted()` returns `(bool)`</td>
      <td style="text-align:left">Returns true if the fundraising set up is complete</td>
    </tr>
    <tr>
      <td style="text-align:left">`contributionsLocked()` returns `(bool)`</td>
      <td style="text-align:left">Returns true if contributions are locked. This means contributors are
        not able to obtain a refund</td>
    </tr>
    <tr>
      <td style="text-align:left">`contributionsList[address]` returns `(array)`</td>
      <td style="text-align:left">
        <p>Each contributor address holds an array of a Contribution structure like
          this</p>
        <p>```struct Contribution {</p>
        <p>address currency;</p>
        <p>uint256 amount;</p>
        <p>uint256 sequence;</p>
        <p>ContributionStatus status;</p>
        <p>}```</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`bufferedContributions[address][address]` returns `(uint256)`</td>
      <td
      style="text-align:left">These are contributions that have yet to be counted as valid; the first
        parameter is the contributor and the second is the currency address in
        this format `bufferedContributions[contributor_address][currency_address]
        = amount contributed`</td>
    </tr>
    <tr>
      <td style="text-align:left">`bufferedSums[address]` returns `(uint256)`</td>
      <td style="text-align:left">Total sum of pending contributions per currency address</td>
    </tr>
    <tr>
      <td style="text-align:left">`qualifiedContributions[address][address]` returns `(uint256)`</td>
      <td
      style="text-align:left">These are contributions that have been qualified and count in the fundraise.
        The first parameter is the contributor and the second is the currency address</td>
    </tr>
    <tr>
      <td style="text-align:left">`qualifiedSums[address]` returns `(uint256)`</td>
      <td style="text-align:left">Total sum of qualified contributions per currency address</td>
    </tr>
    <tr>
      <td style="text-align:left">`historicalBalance[address]` returns `(array)`</td>
      <td style="text-align:left">
        <p>An array of Balance structures per currency address.</p>
        <p>```struct Balance {</p>
        <p>uint256 sequence;</p>
        <p>uint256 balance;</p>
        <p>}```</p>
      </td>
    </tr>
  </tbody>
</table>\#\#\#\# Write Functions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">`setupContract(uint256, uint256, address, address, bool)`</td>
      <td style="text-align:left">
        <p>This function finishes setting up the contract once it has been deployed.
          The parameters are the following:</p>
        <p>1- Minimum contribution amount accepted in base currency</p>
        <p>2- Maximum contribution amount accepted in base currency</p>
        <p>3 - Affiliate Manager contract address</p>
        <p>4 - Contributor Restrictions contract address</p>
        <p>5 - A boolean that sets if the contributions are locked</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`cancelFundraise() returns (bool)`</td>
      <td style="text-align:left">It cancels the fundraise; this function can only be called by the contract
        owner (token issuer)</td>
    </tr>
    <tr>
      <td style="text-align:left">`getContributionsBCY(address, bool)` returns `(uint256)`</td>
      <td style="text-align:left">Returns the contributor&#x2019;s sum of contributions in base currency;
        the contributor&#x2019;s address is the first parameter and the second
        parameter is a boolean for qualified contributions (<em>true</em>) or pending
        contributions (<em>false</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left">`addOffchainContribution(address, address, uint256)` returns `(bool)`</td>
      <td
      style="text-align:left">If off-chain contributions are allowed the token issuer can add contributions
        manually so the contract can later mint and distribute tokens for manual
        contributions; this feature requires trust on the part of the token issuer</td>
    </tr>
    <tr>
      <td style="text-align:left">`contribute(address, uint256, string)` returns `(bool)`</td>
      <td style="text-align:left">
        <p>Allow contributions of ERC20 tokens that are registered in the `Currency
          Registry` contract. The first parameter is the address of the ERC20, the
          second is the amount in Wei and the third is the affiliate link if there
          is one; e.g. to contribute 100 DAI with affiliate link name affiliate use</p>
        <p>`contribute(&#x201C;0x6b175474e89094c44da98b954eedeac495271d0f&#x201D;,100000000000000000000,&#x201D;affiliate&#x201D;)`</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`getRefund()` returns `(bool)`</td>
      <td style="text-align:left">Allow a user to get ERC20 and ETH refunds if the fundraise has passed
        expiration time or has been cancelled</td>
    </tr>
    <tr>
      <td style="text-align:left">`acceptContributor(address)` returns `(bool)`</td>
      <td style="text-align:left">Function that can only be called by the Contributor Restriction smart
        contract after a user has been whitelisted by the issuer</td>
    </tr>
    <tr>
      <td style="text-align:left">`removeContributor(address)` returns `(bool)`</td>
      <td style="text-align:left">Function that can only be called by the Contributor Restriction smart
        contract after a user&#x2019;s address has been unwhitelisted by the token
        issuer</td>
    </tr>
    <tr>
      <td style="text-align:left">`stakeAndMint(address, uint256)` returns `(bool)`</td>
      <td style="text-align:left">
        <p>Allow token issuer to stake SWM tokens in order to mint SRC20 tokens.
          The token issuer can either use ISOP or stake directly if they have the
          required SWM.</p>
        <p>The stakeAndMint function will also conclude the fundraise by internally
          calling the function finishFundraise().</p>
        <p>When stakeAndMint() finalizes the fundraise, that the people whitelisted
          for a fundraise are automatically added to the SRC20 Transfer Rules via
          bulkWhitelistAccount(). Otherwise stakeAndMint() could run into problems
          because the holders are not able to hold the newly minted SRC20 tokens.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`claimTokens()` returns `(uint256)`</td>
      <td style="text-align:left">Allow contributors to claim their portion of SRC20 tokens after the fundraising
        is successfully over</td>
    </tr>
  </tbody>
</table>