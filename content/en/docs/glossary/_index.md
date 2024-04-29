---
title: Glossary
weight: 7
date: 2017-01-05
description: 
---

## Key Solidity Terms

This section provides a comprehensive glossary of essential Solidity terms, serving as a quick reference guide for your blockchain development journey.

### Address

* **Definition:** A 20-byte identifier representing an account on the blockchain. It's used to send and receive transactions, store data, and deploy smart contracts.
* **Example:** `0x1234567890AbCdEf1234567890AbCdEf12345678`

### Block

* **Definition:** A unit of data storage on a blockchain. It stores a collection of transactions and other information, linked together in a chronological chain.
* **Example:** Each new block on the Ethereum blockchain contains a list of transactions, information about the miner who validated the block, and a reference to the previous block.

### Contract

* **Definition:** In Solidity, a contract is a piece of code deployed on the blockchain that defines rules and conditions for interactions. It can store data, execute functions, and manage transactions autonomously.
* **Example:** A smart contract can be used to create a decentralized marketplace where users can buy and sell items securely without relying on a central authority.

### Function

* **Definition:** A reusable block of code within a Solidity contract that performs a specific task. Functions can receive input data (arguments), process it, and potentially return output data.
* **Example:** A `transfer` function in a token contract might be used to send tokens from one account to another.

### Gas

* **Definition:** A unit of measurement on the Ethereum blockchain that represents the computational effort required to execute a transaction or smart contract. Users need to pay gas fees to incentivize miners to process their transactions.
* **Example:** The complexity of a Solidity function can affect the amount of gas it consumes. Simple functions generally cost less gas than complex functions with many operations.

### Mapping

* **Definition:** A key-value data structure in Solidity that allows you to associate a value with a unique key. It's a powerful way to store and retrieve data efficiently.
* **Example:** A mapping can be used to store user balances in a token contract, where the user's address is the key and their token balance is the value.

### Modifier

* **Definition:** A special keyword in Solidity used to alter the behavior of a function before or after its execution. Modifiers can be used for access control, checking conditions, and performing additional tasks around a function's core logic.
* **Example:** A `onlyOwner` modifier can be used to restrict a function to be called only by the contract's owner.

### Solidity

* **Definition:** A high-level, object-oriented programming language specifically designed for writing smart contracts on the Ethereum Virtual Machine (EVM). It allows developers to create secure and transparent applications that run on the blockchain.

### State Variable

* **Definition:** A variable declared within a Solidity contract that stores data persistently on the blockchain. The value of a state variable is accessible throughout the contract's lifetime and can be modified by its functions.
* **Example:** A state variable can be used to store the total supply of tokens in a token contract.

### Transaction

* **Definition:** A message sent from one account on the blockchain to another. It can include data, ether (cryptocurrency), or both. Transactions require gas fees to be processed by miners.
* **Example:** A transaction might be used to transfer funds between two Ethereum accounts, or to interact with a smart contract on the blockchain.

### Type

* **Definition:** In Solidity, a type specifies the kind of data a variable can hold. It ensures type safety, preventing errors caused by using incompatible data types.
* **Example:** Solidity supports various basic data types like integers, strings, and booleans, as well as more complex user-defined types.

These are some of the terms you might find in this documentation. By actively using this resource and exploring the detailed definitions, you'll gain a deeper understanding of Solidity's core concepts and become more comfortable developing your own dApps.