---
title: Functions
weight: 2
date: 2017-01-05
description: 
---

As your smart contracts grow more complex, the need for modularity and reusability becomes paramount. This section introduces you to functions – the cornerstone of modular programming in Solidity. Functions act as reusable blocks of code that encapsulate specific functionalities within your smart contracts.

### Defining Functions
A function definition outlines the blueprint for a specific task within your contract. It consists of several key elements:

* **Visibility Modifier (Optional):** Controls who can call the function (public, private, internal). By default, functions are public and can be called from anywhere.

* **Return Type (Optional):** Specifies the type of data the function will return after execution (e.g., `uint`, `string`, `bool`, or even no return value using `void`).

* **Function Name:** Choose a descriptive name that reflects the function's purpose (following Solidity's [naming conventions](https://docs.soliditylang.org/en/latest/style-guide.html)).

* **Function Parameters (Optional):** A list of parameters enclosed in parenthesis. These act as inputs to the function, allowing you to pass data when calling the function.

* **Function Body:** The code block enclosed in curly braces (`{}`) that defines the actual logic and operations performed by the function.


Here's a basic example of a function definition:

```solidity
function greet(string memory name) public pure returns (string memory) {
  // Function body
  string memory message = "Hello, ";
  message = string(abi.encodePacked(message, name));
  return message;
}
```

**Explanation of the Example**:

* This function is named `greet`.
* It takes one parameter named `name` of type `string memory`.
* The `public` visibility modifier allows anyone to call this function from outside the contract.
* The `pure` modifier indicates the function doesn't modify contract state or perform external calls.
* The return type is `string memory`, signifying it returns a string value.
* The function body concatenates a greeting message with the provided `name` and returns the combined string.


### Function Parameters
Function parameters act as input mechanisms for your functions. You can define parameters within the parenthesis following the function name. Each parameter has a type and a name, similar to variable declarations.

Here's an example of a function with two parameters:

```solidity
function add(uint256 num1, uint256 num2) public pure returns (uint256) {
  // Function body
  uint256 sum = num1 + num2;
  return sum;
}
```

This `add` function takes two `uint256` type parameters (`num1` and `num2`) and returns the sum as a `uint256`.


### Return Values
Return values allow functions to send data back to the caller after execution. You specify the return type within the function definition. If the function doesn't return any data, you can use the void type.

In the previous examples, the `greet` function returns a string value ("Hello, " + name), while the `add` function returns the calculated sum.

**Important Considerations**:

* Not all functions require parameters or return values.
* Parameters are passed by value (a copy) by default in Solidity.


### Calling Functions
Once you've defined functions, you can call them within your code or from other functions to execute their functionalities. To call a function, use its name followed by parentheses, optionally passing in the required arguments (values for the parameters) if applicable.

Here's an example of calling the `greet` function:

```solidity
string memory myGreeting = greet("Bob");
```

This code snippet calls the `greet` function, passing the string "Bob" as the argument for the name parameter. The returned greeting message is then stored in the `myGreeting` variable.


### Practice Makes Perfect!
This section equips you with the fundamentals of defining functions, using parameters, and handling return values. To further enhance your understanding:

* Review the code examples provided throughout this section.
* Experiment with writing your own functions. Try defining functions with different parameters and return types.
* Check online resources and tutorials for further practice on functions in Solidity.

By actively practicing, you'll gain the confidence to leverage functions effectively in building reusable smart contract components.

### Next Steps
The next section covers structures and enums, which offer powerful tools for data organization within your Solidity smart contracts.