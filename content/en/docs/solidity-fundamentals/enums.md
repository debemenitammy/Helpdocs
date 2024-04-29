---
title: Structures and Enums
weight: 3
date: 2017-01-05
description: 
---

As your Solidity projects grow in complexity, managing and manipulating data efficiently becomes crucial. This section introduces you to two powerful tools for data organization: structures and enums.


### Structures
A structure (struct) allows you to group related variables of different data types under a single name. This creates a user-defined data type that simplifies data handling and promotes code readability.


### Defining Structures
To define a structure, you use the `struct` keyword followed by a name and curly braces (`{}`) enclosing the member variables. These member variables act like regular variables within the structure, each with its own data type and name.

Here's an example of a structure named `Person`:

```solidity
struct Person {
  uint age;
  string name;
  bool isActive;
}
```

This `Person` structure has three member variables:

* `age`: Stores the person's age as an integer (`uint`).
* `name`: Holds the person's name as a string (`string`).
* `isActive`: Represents the person's active status as a boolean (`bool`).


### Declaring and Using Structures
Once defined, you can declare variables of the structure type. These variables act like containers that can hold specific data related to a person.

Here's an example of declaring and using a Person structure variable:

```solidity
Person alice; // Declares a variable 'alice' of type 'Person'

alice.age = 30;
alice.name = "Alice Smith";
alice.isActive = true;

// Accessing member variables using dot notation
uint aliceAge = alice.age;
```

By using structures, you can group related data into a single unit, making your code more organized and easier to understand.


### Enums
An enumeration (enum) allows you to create a user-defined data type that restricts a variable to a specific set of predefined values. This enhances code readability and reduces errors by ensuring variables can only hold the defined options.


### Defining Enums
To define an enum, you use the `enum` keyword followed by a name and curly braces (`{}`) enclosing the list of possible values (separated by commas).

Here's an example of an `enum` named `Status` with three possible values:

```solidity
enum Status { Pending, Approved, Rejected }
```

This `Status` enum defines three options: `Pending`, `Approved`, and `Rejected`.


### Declaring and Using Enums
Once defined, you can declare variables of the enum type. These variables can only hold one of the predefined values from the enum.

Here's an example of declaring and using a `Status` enum variable:

```solidity
Status applicationStatus = Status.Pending;

// Changing the value
applicationStatus = Status.Approved;

// Using enums in conditional statements
if (applicationStatus == Status.Approved) {
  // Grant access
}
```

By using enums, you can define clear and limited options for your variables, improving code clarity and preventing invalid data assignments.

### Code Examples
Here's an example that combines structures and enums to manage a user's profile data:

```solidity
struct User {
  uint id;
  string name;
  Status status; // Using the 'Status' enum
}

enum Status { Active, Inactive }

User john;
john.id = 1;
john.name = "John Doe";
john.status = Status.Active;

// Accessing and modifying data
if (john.status == Status.Active) {
  // User is active, allow interaction
} else {
  // User is inactive, restrict access
}
```

This example demonstrates how structures and enums can be used together to organize and manage user data effectively within a smart contract.


### Next Steps
The next section covers mappings, a fundamental concept for storing key-value data pairs within your Solidity smart contracts.
