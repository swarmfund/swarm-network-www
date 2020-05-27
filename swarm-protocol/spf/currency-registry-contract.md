---
description: '- WORK IN PROGRESS -'
---

# Currency Registry Contract

* **Smart Contract:** specific to a Swarm Powered Fundraise for a specific SRC20
* **Created:**  Step X in the deployment of a Swarm Powered Fundraise and then referenced in the Swarm Powered Fundraise contract
* **Purpose:** Registers all currencies that will be accepted in a specific Swarm Powered Fundraise
* **Example:** TBD

## Feature Description

### Read Functions

| Function | Description |
| :--- | :--- |
| `currenciesList[address]` returns `(struct)` | An array of CurrencyStats Objects. These objects have the following structure: `struct CurrencyStats {address erc20address; address exchangeProxy; uint256 finalExchangeRate; uint256 totalBufferedAmount; uint256 totalQualifiedAmount;}` |
| `getAcceptedCurrencies()` returns `(address[])` | Returns an array of the accepted currencies in a Swarm Powered Fundraise |
| `currencyIndex[address]` returns `(uint256)` | A mapping of accepted currency addresses to integers; To obtain the index of DAI in the contract use `currencyIndex(“0x6B175474E89094C44Da98b954EedeAC495271d0F”)` |
| `lockedExchangeRate(address)` returns `(uint256)` | Returns the value of the locked exchange rate of the currency in the first parameter |
| `isAccepted(address)` returns `(bool)` | Returns if a specific currency is accepted in a Swarm Powered Fundraise; To check if the fundraise accepts DAI use `isAccepted(“0x6B175474E89094C44Da98b954EedeAC495271d0F”)` |
| `getBaseCurrency()` returns `(address)` | Returns the base currency in which a Swarm Powered Fundraise is denominated |
| `toUSD(uint256, address)` returns `(uint256)` | Converts the amount given as the first parameter into USD. The second parameter is the address of the currency to be converted to USD. |
| `toBCY(uint256, address)` returns `(uint256)` | Converts the amount given as the first parameter into the Base Currency. The second parameter is the address of the currency to be converted to Base Currency |
| `getRate(address, address, uint256, uint256)` returns `(uint256, uint256)` | Returns the exchange rate between the first and the second address. The first parameter is the token address of the currency to be exchanged from, the second parameter is the address of the currency to be exchanged to, the third parameter is the value in Wei to be exchanged and the fourth parameter is the decimal places. E.g. to get the rate of 1 ETH in DAI use `getRate(“0x0000000000000000000000000000000000000000”,"0x2a1530C4C41db0B0b2bB646CB5Eb1A67b7158667”,1000000000000000000,0)` |
| `isOwner()` returns `(bool)` | Returns true if the calling address is the contract owner |
| `owner()` returns `(address)` | Returns the address of the contract owner |

### Write Functions

| Function | Description |
| :--- | :--- |
| `addCurrency(address, address)` returns `(bool)` | Adds a currency to the list of currencies accepted in a Swarm Powered Fundraise. The first parameter is the token address and the second parameter is the address of the exchange proxy contract |
| `lockExchangeRates()` | Locks the exchange rates of currencies accepted in a Swarm Powered Fundraise to the Base Currency |
| `setBaseCurrency(address)` | Sets a base currency from the list of currencies accepted in a Swarm Powered Fundraise; the parameter is the address of the base currency to be set |
| `setUSDERC20(address)` returns `(bool)` | Sets the currency address that will be used as the default USD dollar oracle address for a Swarm Powered Fundraise. Usually set to USDC; e.g. to set to USDC use `setUSDERC20(“0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48”)` |
| `renounceOwnership()` | Contract owner can renounce ownership of this Currency Registry contract |
| `transferOwnership()` | Transfers ownership of this Currency Registry contract to another address |

