---
title: Mappings
weight: 4
date: 2017-01-05
description: 
---

Solidity offers various mechanisms for data storage within smart contracts. Mappings provide a powerful solution for storing and retrieving data using key-value pairs. This section covers how to leverage mappings for efficient data management in your smart contracts.

### Understanding Mappings
A mapping acts like a giant dictionary or lookup table. It allows you to associate unique keys with their corresponding values. This enables efficient storage and retrieval of data based on specific identifiers.

### Key Points about Mappings
* **Keys**: Keys act as unique identifiers used to access data within the mapping. Keys can be of various data types like integers, strings, or even addresses.
* **Values**: Values represent the actual data you want to store associated with each key. Values can also be of various data types, allowing flexibility in storing different types of information.
* **Dynamic Size**: Unlike fixed-size arrays, mappings can grow dynamically as you add new key-value pairs.

### Defining Mappings
To define a mapping, you use the following syntax:

```solidity
mapping(KeyType => ValueType) MappingName;
```
* **KeyType**: This specifies the data type allowed for keys within the mapping.
* **ValueType**: This defines the data type allowed for values stored in the mapping.
* **MappingName**: Choose a descriptive name for your mapping that reflects its purpose.

Here's an example of defining a mapping named `studentGrades` that stores student IDs (uint) as keys and their corresponding grades (string) as values:

```solidity
mapping(uint => string) studentGrades;
```

### Adding and Retrieving Data
There are two primary ways to interact with mappings:

1. **Adding a Key-Value Pair**:
Use the assignment operator (`=`) along with the key enclosed in square brackets `[]` to assign a value to a specific key within the mapping.

```solidity
studentGrades[123] = "A"; // Add student with ID 123 and assign grade "A"
```

2. **Retrieving a Value**:
Use the key enclosed in square brackets `[]` to access the value associated with that key in the mapping.

```solidity
string grade = studentGrades[123]; // Retrieve the grade for student ID 123
```

**Important Considerations**:
- If you try to retrieve a non-existent key, you'll get the default value for the value type (e.g., 0 for integers, empty string for strings).
- To check if a key exists in the mapping before accessing its value, you can use the exists function provided by Solidity.


### Code Examples
Here's an example that demonstrates using a mapping to store user preferences:

```solidity
mapping(address => bool) public isSubscribed;

function subscribe() public {
  isSubscribed[msg.sender] = true;
}

function unsubscribe() public {
  isSubscribed[msg.sender] = false;
}

// Checking subscription status
if (isSubscribed[msg.sender]) {
  // User is subscribed, send updates
} else {
  // User is not subscribed
}
```

This example uses a mapping `isSubscribed` to track user subscriptions. The `subscribe` and `unsubscribe` functions allow users to manage their subscription status. The code snippet also demonstrates how to check a user's subscription status using the `isSubscribed` mapping.


### Up Next
This section concludes the core fundamentals of Solidity. As you progress in your journey, feel free to proceed the next sections that cover more advanced topics like inheritance, libraries, and advanced contract patterns.