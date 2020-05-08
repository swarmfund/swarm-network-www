# Currency Registry Contract

* **Smart Contract:** specific to a Swarm Powered Fundraise for a specific SRC20
* **Created:**  Step X in the deployment of a Swarm Powered Fundraise and then referenced in the Swarm Powered Fundraise contract
* **Purpose:** Registers all currencies that will be accepted in a specific Swarm Powered Fundraise
* **Example:** TBD

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
      <td style="text-align:left"><code>currenciesList[address]</code> returns <code>(struct)</code>
      </td>
      <td style="text-align:left">An array of CurrencyStats Objects. These objects have the following structure:</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>getAcceptedCurrencies()</code> returns <code>(address[])</code>
      </td>
      <td style="text-align:left">Returns an array of the accepted currencies in a Swarm Powered Fundraise</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>currencyIndex[address]</code> returns <code>(uint256)</code>
      </td>
      <td style="text-align:left">
        <p>A mapping of accepted currency addresses to integers;</p>
        <p>To obtain the index of DAI in the contract use <code>currencyIndex(&quot;0x6B175474E89094C44Da98b954EedeAC495271d0F&quot;)</code>
        </p>
      </td>
    </tr>
  </tbody>
</table> \|

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>currenciesList[address]</code> returns <code>(struct)</code></td>
      <td style="text-align:left">
        <p>An array of CurrencyStats Objects. These objects have the following structure:</p>
        <code>
        <p>struct CurrencyStats {</p>
        <p>address erc20address;</p>
        <p>address exchangeProxy;</p>
        <p>uint256 finalExchangeRate;</p>
        <p>uint256 totalBufferedAmount;</p>
        <p>uint256 totalQualifiedAmount;</p>
        <p>}</p>
        </code>
        <p>To obtain the first object in the array use <code>currencyList[0]</code></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`getAcceptedCurrencies()` returns `(address[])`</td>
      <td style="text-align:left">Returns an array of the accepted currencies in a Swarm Powered Fundraise</td>
    </tr>
    <tr>
      <td style="text-align:left">`currencyIndex[address]` returns `(uint256)`</td>
      <td style="text-align:left">
        <p>A mapping of accepted currency addresses to integers;</p>
        <p>To obtain the index of DAI in the contract use `currencyIndex(&#x201C;0x6B175474E89094C44Da98b954EedeAC495271d0F&#x201D;)`</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`lockedExchangeRate(address)` returns `(uint256)`</td>
      <td style="text-align:left">Returns the value of the locked exchange rate of the currency in the first
        parameter</td>
    </tr>
    <tr>
      <td style="text-align:left">`isAccepted(address)` returns `(bool)`</td>
      <td style="text-align:left">Returns if a specific currency is accepted in a Swarm Powered Fundraise;
        To check if the fundraise accepts DAI use `isAccepted(&#x201C;0x6B175474E89094C44Da98b954EedeAC495271d0F&#x201D;)`</td>
    </tr>
    <tr>
      <td style="text-align:left">`getBaseCurrency()` returns `(address)`</td>
      <td style="text-align:left">Returns the base currency in which a Swarm Powered Fundraise is denominated</td>
    </tr>
    <tr>
      <td style="text-align:left">`toUSD(uint256, address)` returns `(uint256)`</td>
      <td style="text-align:left">Converts the amount given as the first parameter into USD. The second
        parameter is the address of the currency to be converted to USD.</td>
    </tr>
    <tr>
      <td style="text-align:left">`toBCY(uint256, address)` returns `(uint256)`</td>
      <td style="text-align:left">Converts the amount given as the first parameter into the Base Currency.
        The second parameter is the address of the currency to be converted to
        Base Currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`getRate(address, address, uint256, uint256)` returns `(uint256, uint256)`</td>
      <td
      style="text-align:left">
        <p>Returns the exchange rate between the first and the second address. The
          first parameter is the token address of the currency to be exchanged from,
          the second parameter is the address of the currency to be exchanged to,
          the third parameter is the value in Wei to be exchanged and the fourth
          parameter is the decimal places. E.g. to get the rate of 1 ETH in DAI use</p>
        <p>`getRate(&#x201C;0x0000000000000000000000000000000000000000&#x201D;,&#x201D;0x2a1530C4C41db0B0b2bB646CB5Eb1A67b7158667&#x201D;,1000000000000000000,0)`</p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left">`isOwner()` returns `(bool)`</td>
      <td style="text-align:left">Returns true if the calling address is the contract owner</td>
    </tr>
    <tr>
      <td style="text-align:left">`owner()` returns `(address)`</td>
      <td style="text-align:left">Returns the address of the contract owner</td>
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
      <td style="text-align:left">`addCurrency(address, address)` returns `(bool)`</td>
      <td style="text-align:left">Adds a currency to the list of currencies accepted in a Swarm Powered
        Fundraise. The first parameter is the token address and the second parameter
        is the address of the exchange <b>proxy</b> contract</td>
    </tr>
    <tr>
      <td style="text-align:left">`lockExchangeRates()`</td>
      <td style="text-align:left">Locks the exchange rates of currencies accepted in a Swarm Powered Fundraise
        to the Base Currency</td>
    </tr>
    <tr>
      <td style="text-align:left">`setBaseCurrency(address)`</td>
      <td style="text-align:left">Sets a base currency from the list of currencies accepted in a Swarm Powered
        Fundraise; the parameter is the address of the base currency to be set</td>
    </tr>
    <tr>
      <td style="text-align:left">`setUSDERC20(address)` returns `(bool)`</td>
      <td style="text-align:left">
        <p>Sets the currency address that will be used as the default USD dollar
          oracle address for a Swarm Powered Fundraise. Usually set to USDC; e.g.
          to set to USDC use</p>
        <p>`setUSDERC20(&#x201C;0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48&#x201D;)`</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">`renounceOwnership()`</td>
      <td style="text-align:left">Contract owner can renounce ownership of this Currency Registry contract</td>
    </tr>
    <tr>
      <td style="text-align:left">`transferOwnership()`</td>
      <td style="text-align:left">Transfers ownership of this Currency Registry contract to another address</td>
    </tr>
  </tbody>
</table>