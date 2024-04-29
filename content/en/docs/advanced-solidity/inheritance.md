---
title: Inheritance
weight: 1
date: 2017-01-05
description: 
---

As your smart contract projects become more complex, the need for code reusability and modularity becomes paramount. Inheritance in Solidity provides a powerful mechanism to achieve these goals. Inheritance allows you to create new contracts (subclasses) that inherit functionalities and properties from existing contracts (base classes).


### Benefits of Inheritance
* **Code Reusability**: By inheriting from a base class, you can reuse existing code, reducing development time and redundancy.
* **Maintainability**: Modifications made to the base class are automatically reflected in inheriting contracts, improving code maintainability.
* **Hierarchical Relationships**: Inheritance allows you to model real-world hierarchical relationships between contracts. For example, a `SavingsAccount` contract could inherit from a generic `Account` contract.


### Understanding Inheritance Concepts
* **Base Class (Parent Class)**: The contract that provides the functionalities and properties to be inherited.
* **Sub Class (Child Class)**: The contract that inherits from the base class. It can access and potentially override inherited functionalities.
* **Inheritance Relationship**: The connection between the subclass and its base class, indicating which functionalities and properties are inherited.
* **"is" Keyword**: Used in the subclass definition to specify the base class it inherits from.


### Creating an Inheritance Hierarchy
Here's an example demonstrating a simple inheritance hierarchy:

**Base Contract (Vehicle.sol)**:

```solidity
contract Vehicle {
  string public model;
  uint public year;

  function setDetails(string memory _model, uint _year) public {
    model = _model;
    year = _year;
  }

  function getYear() public view returns (uint) {
    return year;
  }
}
```

This `Vehicle` base class defines properties (`model` and `year`) and functions (`setDetails` and `getYear`) related to a generic vehicle.


**Sub Class (Car.sol)**:
```solidity
contract Car is Vehicle { // Inherits from 'Vehicle' base class
  uint public mileage;

  function setMileage(uint _mileage) public {
    mileage = _mileage;
  }
}
```
This `Car` subclass inherits from the `Vehicle` base class using the `is` keyword. It adds a new property (`mileage`) specific to cars and defines a new function (`setMileage`). The `Car` contract can also access and utilize the inherited properties and functions from the `Vehicle` base class.


### Visibility Specifiers and Inheritance
Solidity inheritance interacts with visibility modifiers (public, private, internal) defined in the base class:

* **Public members**: Inherited by the subclass and accessible from anywhere.
* **Private members**: Not inherited by the subclass and only accessible within the base class.
* **Internal members**: Inherited by the subclass but only accessible within the same contract or inheriting contracts from the same source unit.


### Overriding Functions
Subclasses can override inherited functions by providing their own implementations. This allows you to specialize the behavior of a function for the specific context of the subclass.

Here's an example of overriding the `getYear` function in the `Car` subclass:

```solidity
contract Car is Vehicle {
  // ... other code

  function getYear() public view override returns (uint) {
    // Custom logic for retrieving car's year (e.g., considering model year)
    return year + 2; // Example modification
  }
}
```

The `Car` subclass overrides the `getYear` function, potentially adding specific logic related to car models or calculations.


### Understanding Inheritance Limitations
* **Multiple Inheritance**: Not directly supported in Solidity. You can achieve similar functionality using interfaces (covered in a later section).
* **Diamond Problem**: Can occur with complex inheritance structures. Careful planning is required to avoid conflicts.


### When to Use Inheritance
Inheritance is a powerful tool, but it's not always the best solution. Consider inheritance when:

* You have a base class with common functionalities that can be reused by multiple contracts.
* You want to model hierarchical relationships between contracts.
* Code maintainability and reusability are crucial for your project.


### Looking Ahead
The next section contains code examples explaining interfaces, another fundamental concept for promoting code reusability and defining function specifications in Solidity.