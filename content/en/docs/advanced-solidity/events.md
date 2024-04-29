---
title: Events
weight: 2
date: 2017-01-05
description: 
---

Solidity smart contracts operate on the blockchain, but often interact with external applications or user interfaces. Events provide a crucial communication mechanism that allows your smart contracts to notify these external entities about specific occurrences within the contract.


### Understanding Events
Events act as a notification system within your smart contract. You can define events to emit specific data whenever certain actions or conditions are met. External applications that monitor your contract for these events (often referred to as event listeners) can then receive and react to the emitted data.

This two-way communication between smart contracts and external applications fosters greater transparency and enables applications to respond to changes within the contract, creating a more dynamic and interactive user experience.


### Defining Events
Creating an event involves defining its details within your Solidity code. To define an event, you use the `event` keyword followed by a name and parentheses containing a comma-separated list of parameters (similar to function parameters). Each parameter has a data type specifying the type of data that will be emitted with the event.

Here's an example of defining an event named `Transfer` that emits data whenever a token transfer occurs:

```solidity
event Transfer(address indexed from, address indexed to, uint256 value);
```

**Explanation**:

* This `Transfer` event takes three parameters:
  * `from`: Address of the sender (indexed for efficient searching).
  * `to`: Address of the receiver (indexed for efficient searching).
  * `value`: Amount of tokens transferred.
* The `indexed` keyword applied to `from` and `to` allows external applications to efficiently filter events based on specific addresses.


### Emitting Events
Once you've defined an event, you can emit it within your code using the emit keyword followed by the event name and parentheses containing the actual data values to be emitted (corresponding to the defined parameters).

Here's an example of emitting the `Transfer` event within a token transfer function:

```solidity
function transfer(address recipient, uint256 amount) public returns (bool) {
  // Transfer logic (e.g., deducting balance from sender, adding to receiver)
  emit Transfer(msg.sender, recipient, amount);
  return true;
}
```

In this example, whenever the `transfer` function successfully transfers tokens, it emits the `Transfer` event with the sender's address, recipient's address, and the transferred amount.


### External Applications
External applications can utilize tools and libraries specific to the blockchain platform (e.g., web3.js for Ethereum) to listen for events emitted by your smart contract. When an event is emitted, these applications receive the data and can perform actions based on the information received.

For example, a user interface might update a user's token balance upon receiving a `Transfer` event, reflecting the latest transaction in the application.


### Benefits of Using Events
* **Enhanced Transparency**: Events provide a way for external applications to stay informed about happenings within your smart contract.
* **Improved User Experience**: External applications can react to events and update user interfaces in real-time, creating a more dynamic user experience.
* **Decoupled Logic**: Events allow for decoupling your smart contract logic from the specific actions of external applications.

### Next Steps
The next section will go into advanced topics like inheritance and libraries, which can help you write more modular and reusable Solidity code.