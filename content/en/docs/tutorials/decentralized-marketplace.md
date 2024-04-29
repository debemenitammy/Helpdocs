---
title: Building a Decentralized Marketplace with Solidity
weight: 2
date: 2017-01-05
description: 
---

In this tutorial, we'll guide you through building a simple marketplace on the blockchain using Solidity. Here, users can list items for sale and purchase them directly from each other, eliminating the need for a central authority.

By the end of this tutorial, you'll be able to:

* Develop a smart contract that facilitates peer-to-peer item listing, purchasing, and ownership transfer.
* Understand the core functionalities of a decentralized marketplace, including product management, payments (simulated here), and secure transactions.
* Deploy your marketplace contract to a test network and interact with it to experience decentralized trading.


### Prerequisites
Before you begin, ensure you have the following:

* A code editor like [Visual Studio Code](https://code.visualstudio.com/) or [Remix IDE](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.25+commit.b61c2a91.js).
* A local blockchain environment set up using tools like [Ganache](https://archive.trufflesuite.com/ganache/) or [Truffle](https://archive.trufflesuite.com/).
* Basic understanding of Solidity syntax and data types (refer to the "Solidity Fundamentals" section if needed).
* [MetaMask wallet](https://metamask.io/) or a similar tool to interact with your deployed contract.


### Step-by-Step Guide: Building Your Marketplace

1. **Setting Up the Project**:

* Open your code editor and create a new directory for this project (e.g., `decentralized-marketplace`).
* Initialize a new Solidity project within this directory using the tool of your choice (e.g., `truffle init`).

2. **Creating the Marketplace Contract**:

* Inside your project directory, create a new file named `Marketplace.sol`.
* Paste the following code snippet into the `Marketplace.sol` file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Marketplace {
  // Structure to store product information
  struct Product {
    uint256 id;
    string name;
    uint256 price;
    address payable owner;
    bool purchased;
  }

  // Mapping to store products by their unique identifier
  mapping(uint256 => Product) public products;

  // Current product ID (auto-increments for each new product)
  uint256 public nextProductId = 1;

  // Function to add a new product to the marketplace
  function addProduct(string memory _name, uint256 _price) public {
    products[nextProductId] = Product(nextProductId, _name, _price, msg.sender, false);
    nextProductId++;
  }

  // Function to purchase a product (simulates payment)
  function purchaseProduct(uint256 _productId) public payable {
    Product memory product = products[_productId];
    require(product.purchased == false, "Product is already purchased");
    require(msg.value >= product.price, "Insufficient funds sent");

    // Simulate payment by transferring funds to the seller (for educational purposes)
    product.owner.transfer(msg.value);
    products[_productId].purchased = true;
  }

  // Function to get all available products
  function getProducts() public view returns (Product[] memory) {
    Product[] memory availableProducts = new Product[](nextProductId - 1);
    uint256 index = 0;
    for (uint256 i = 1; i < nextProductId; i++) {
      if (!products[i].purchased) {
        availableProducts[index] = products[i];
        index++;
      }
    }
    return availableProducts;
  }
}
```

**Explanation of the Code**:

* This code defines a smart contract named `Marketplace`.
* The `Product` struct stores information about each item listed on the marketplace.
* A mapping (`products`) keeps track of products using their unique ID as the key.
* The `nextProductId` variable keeps track of the next available ID for new products.
* The `addProduct` function allows sellers to list items with a name and price.
* The `purchaseProduct` function simulates a purchase by checking product availability, verifying sufficient funds, and transferring simulated funds to the seller. (In a real-world scenario, this would likely involve integrating with an oracle or token system).
* The `getProducts` function retrieves a list of all available (unpurchased) products currently on the marketplace.

3. **Compiling and Deploying the Contract**:

Follow the same steps as in the previous tutorial to compile and deploy the `Marketplace.sol` contract to your local blockchain network.


4. **Interacting with Your Marketplace**:
Open your MetaMask wallet and connect it to the network where you deployed the marketplace contract. Here, we'll simulate the experience of both sellers listing items and buyers purchasing them.

**Seller Actions**:

1. **Interact with Contract**: In MetaMask, navigate to the "Interact with Contract" functionality. Paste the deployed contract address for your marketplace and look for the `addProduct` function.
2. **Listing an Item**: Provide a name for your product (e.g., "Digital Artwork") and set a price using some whole number (e.g., 10) to simulate the value. This value won't represent real currency but demonstrates the concept.
3. **Confirm Transaction**: MetaMask will prompt you to confirm the transaction, including gas fees. Once confirmed, the transaction will be submitted to the network, and your item will be listed on the marketplace.


**Buyer Actions**:

1. **Interact with Contract (View)**: Similar to the seller, use the "Interact with Contract" function in MetaMask. This time, look for the `getProducts` function (it should be set to "view" as it doesn't modify contract state).
2. **Viewing Available Products**: Calling the `getProducts` function will retrieve a list of currently available products (those not marked as purchased). You should see your seller's listed item with its details.
3. **Purchasing an Item**: Find the ID of the product you want to buy (it should be displayed in the list of available products). Look for the `purchaseProduct` function and enter the product ID in the designated field.
4. **Simulating Payment and Confirming Transaction**: Since this is a simulated marketplace, you won't be sending real currency. However, MetaMask will still prompt you to confirm a transaction with gas fees. Confirming the transaction will initiate the purchase process.

**Monitoring Your Marketplace**:

* Refresh the `getProducts` function after each transaction (adding a product or making a purchase). The product list should update accordingly.
* You can switch between your seller and buyer MetaMask accounts to test both sides of the marketplace functionality.


**Important Note**:

Remember, this is a simplified example for educational purposes. Real-world marketplaces would likely involve integrating with oracle networks for real-time price feeds and tokenized payment systems for secure transactions.

Congratulations! You've successfully interacted with your deployed decentralized marketplace smart contract. This exercise demonstrates the core functionalities of peer-to-peer trading on a blockchain platform.

### Key Takeaways
In this tutorial, you learned how to:

* Build a basic decentralized marketplace contract using Solidity.
* Simulate product listing and purchasing functionalities.
* Understand the potential of blockchain technology for creating trustless and transparent marketplaces.