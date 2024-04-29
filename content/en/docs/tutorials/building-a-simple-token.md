---
title: Building a Simple Token on Solidity
weight: 1
date: 2017-01-05
description: 
---

In this tutorial, we'll guide you through building a simple token using Solidity, the programming language for creating smart contracts on the blockchain.

By the end of this tutorial, you'll be able to:

* Deploy a basic token contract to a test network.
* Understand the core functionalities of a token, including supply, transfer, and balance tracking.
* Interact with your deployed token contract to mint new tokens and transfer them between accounts.


### Prerequisites
Before you begin, ensure you have the following:

* A code editor like [Visual Studio Code](https://code.visualstudio.com/) or [Remix IDE](https://remix.ethereum.org/#lang=en&optimize=false&runs=200&evmVersion=null&version=soljson-v0.8.25+commit.b61c2a91.js).
* A local blockchain environment set up using tools like [Ganache](https://archive.trufflesuite.com/ganache/) or [Truffle](https://archive.trufflesuite.com/).
* Basic understanding of Solidity syntax and data types (refer to the "Solidity Fundamentals" section if needed).
* [MetaMask wallet](https://metamask.io/) or a similar tool to interact with your deployed contract.


### Step-by-Step Guide: Building Your Token

1. **Setting Up the Project**:

* Open your code editor and create a new directory for this project (e.g., `simple-token`).
* Initialize a new Solidity project within this directory using the tool of your choice (e.g., `truffle init`).

2. **Creating the Token Contract**:

* Inside your project directory, create a new file named `SimpleToken.sol`.
* Paste the following code snippet into the `SimpleToken.sol` file:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleToken {
  // Total supply of tokens
  uint256 public totalSupply;

  // Mapping to store token balances for each address
  mapping(address => uint256) public balances;

  // Constructor to initialize the total token supply
  constructor(uint256 initialSupply) {
    totalSupply = initialSupply;
    balances[msg.sender] = totalSupply; // Allocate initial supply to the deployer
  }

  // Function to transfer tokens from one address to another
  function transfer(address recipient, uint256 amount) public {
    require(balances[msg.sender] >= amount, "Insufficient balance");
    balances[msg.sender] -= amount;
    balances[recipient] += amount;
  }

  // Function to get the token balance of an address
  function balanceOf(address owner) public view returns (uint256) {
    return balances[owner];
  }
}
```

Explanation of the Code:

* This code defines a smart contract named `SimpleToken`.
* The `totalSupply` variable stores the total number of tokens in existence.
* The `balances` mapping keeps track of the token balance for each address.
* The constructor takes an initial supply value as input and allocates it to the deployer's address.
* The `transfer` function allows users to send tokens to other addresses, performing balance checks before the transfer.
* The `balanceOf` function retrieves the token balance of a specified address.


3. **Compiling the Contract**:

Use your chosen tool (e.g., Truffle) to compile the `SimpleToken.sol` contract. This generates bytecode, which is machine code for the Ethereum Virtual Machine (EVM).

4. **Deploying the Contract**:

* Connect your MetaMask wallet to your local blockchain network.
* Use your development environment (e.g., Truffle) to deploy the `SimpleToken` contract to the network.
* Take note of the contract address generated during deployment. You'll need it to interact with the contract later.

5. **Interacting with Your Token**:

* Open your MetaMask wallet and switch to the network where you deployed the contract.
* Use the "Interact with Contract" functionality in MetaMask. Paste the deployed contract address and look for the `transfer` and `balanceOf` functions.


### Try it Out

* Use the `balanceOf` function to check the initial token balance in your MetaMask wallet (should be the initial supply you deployed with).
* Specify a recipient address and a desired transfer amount, then use the `transfer` function to send some tokens to another address.
* Switch to the recipient's address in MetaMask and use the `balanceOf` function again to confirm the transferred tokens are reflected in their balance.


Congratulations! You've successfully built and deployed your first token on a blockchain network. This is a fundamental building block for many DeFi applications.


### Key Takeaways

In this tutorial, you learned how to:

* Create a basic token contract using Solidity.
* Understand the core functionalities of a token, including:
    * Total Supply: Setting a maximum number of tokens that can ever exist.
    * Transferring Tokens: Enabling users to send tokens between addresses.
    * Balance Tracking: Maintaining a record of how many tokens each address holds.
* Deploy a smart contract to a local blockchain network.
* Interact with your deployed contract using a wallet like MetaMask.