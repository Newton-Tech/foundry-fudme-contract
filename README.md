FundMe Contract
The FundMe contract is a sample funding contract implemented using the Foundry smart contract framework. It allows users to fund the contract with Ether based on the ETH/USD price feed and withdraw the funds. The contract is designed to enforce a minimum funding amount in USD.

Prerequisites
Solidity compiler version 0.8.19 or compatible
Chainlink AggregatorV3Interface library
Getting Started
To deploy the FundMe contract, follow these steps:

Deploy the PriceFeed contract that implements the AggregatorV3Interface for obtaining the ETH/USD price feed.

Deploy the FundMe contract, passing the address of the PriceFeed contract as a constructor parameter.

Once the FundMe contract is deployed, you can interact with the contract by funding it with Ether.

Contract Details
State Variables
MINIMUM_USD: The minimum funding amount in USD.

i_owner: The address of the contract owner.

s_funders: An array of addresses of users who have funded the contract.

s_addressToAmountFunded: A mapping that stores the amount funded by each address.

s_priceFeed: An instance of the AggregatorV3Interface contract representing the ETH/USD price feed.

Modifiers
onlyOwner(): A modifier that restricts the execution of a function to the contract owner.
Functions
constructor(address priceFeed): Initializes the FundMe contract with the address of the PriceFeed contract and sets the contract owner as the deployer.

fund(): Allows users to fund the contract with Ether based on the current ETH/USD price feed. Requires the funded amount to meet the minimum USD requirement.

withdraw(): Allows the contract owner to withdraw the funds from the contract. Resets the amount funded by each address and clears the list of funders.

cheaperWithdraw(): An alternative method for the contract owner to withdraw funds in a more cost-efficient way. Works by storing the list of funders in memory and resetting the funded amounts.

getAddressToAmountFunded(address fundingAddress): Retrieves the amount funded by a specific address.

getVersion(): Retrieves the version of the price feed contract.

getFunder(uint256 index): Retrieves the address of a funder at the specified index in the list of funders.

getOwner(): Retrieves the address of the contract owner.

getPriceFeed(): Retrieves the instance of the price feed contract.

License
This contract is licensed under the MIT License. You can find the license text in the LICENSE file.