## Solidity Tutorial
Learn Solidity From Examples.

## Table of Contents  
- [Solidity Tutorial](#solidity-tutorial)
- [Table of Contents](#table-of-contents)
- [Online IDE](#online-ide)
- [Basic Structure](#basic-structure)
- [Data Types](#data-types)


## Online IDE
We are going to use [Remix IDE](https://remix.ethereum.org/) to test our examples.

Steps to follow:
1. Create a new file. Say __Example.sol__
   
   ![](image/1.jpeg)
2. Select the latest compiler version and Turn on __Auto compile__
   
   ![](image/2.jpeg)
3. Write the following code to __Example.sol__ and __Deploy__
   
   ![](image/3.jpeg)

[🔝Back to Table of Contents](#table-of-contents)

## Basic Structure
```solidity
// SPDX License Identifier: Every source file should start with a comment indicating its license:
// SPDX-License-Identifier: MIT

// Pragmas: The pragma keyword is used to enable certain compiler features or checks.
pragma solidity ^0.8.17;

// Contracts: Contracts in Solidity are similar to classes in object-oriented languages.
// They contain persistent data in state variables, and functions that can modify these variables.
contract Example {
    // Comments: Single-line comments (//) and multi-line comments (/*...*/) are possible
    // This is a single-line comment.

    /*
    This is a
    multi-line comment.
    */
}

// NatSpec comments: Mainly used for doumentation. 
// They are written with a triple slash (///) or a double asterisk block (/** ... */) and
// they should be used directly above function declarations or statements.

/// @author The Solidity Team
/// @title A simple storage example
contract SimpleStorage {
    uint storedData;

    /// Store `x`.
    /// @param x the new value to store
    /// @dev stores the number in the state variable `storedData`
    function set(uint x) public {
        storedData = x;
    }

    /// Return the stored value.
    /// @dev retrieves the value of the state variable `storedData`
    /// @return the stored value
    function get() public view returns (uint) {
        return storedData;
    }
}
```

[🔝Back to Table of Contents](#table-of-contents)


## Data Types
```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.17;

contract Example {
    /// Fixed size value types


    // Boolean: The possible values are constants true and false
    bool isActive;


    // Integer: Signed and unsigned integers of various sizes
    // int for signed integers
    // uint for unsigned integers
    int temparature;
    uint age;
    // Possible keywords are uint8 to uint256 in steps of 8 and int8 to int256
    // uint is aliase for uint256 and int is aliase for int256
    int8 smallest_int;
    int256 largest_int;
    int also_largedt_int;


    /*  Address: two versions:
        - address: holds 20 byte ethereum address.
                   can't receive ether
        - address payable: same as address with two additional members
                           transfer and send
                           can receive ether                   
    */
    address recipent_address;
    address payable recipent;
    
    
    // Bytes: holds a sequence of bytes from one to up to 32. 
    // Ex: bytes1, bytes2, bytes3, …, bytes32
    // byte is an alias for bytes1.
    bytes1 smallest_byte;
    bytes32 largest_byte;
    // The term bytes represents a dynamic array of bytes. 
    // It’s a shorthand for byte[] .
    bytes array_of_bytes;


    // Enum: Enum is one way to create a user-defined type in Solidity.
    enum Size {
        SMALL,
        MEDIUM,
        LARGE
    }



    /// Variable size reference type


    // String: String literals are written with either double or single-quotes
    // More preferred way is to use byte types instead of String as string 
    // operation requires more gas as compared to byte operation.
    // Solidity provides inbuilt conversion between bytes to string and vice versa
    string name;
    bytes32 another_name;

    
    // Array: Arrays are a group of variables of the same data type, 
    // with each variable having a unique index. 
    // Array size can be fixed or dynamic
    // Fixed-sized array
    uint[10] ten_numbers;
    // Dynamic-size arrays
    uint[] many_numbers;


    // Mapping: similar to a hashtable or dictionary in other programming languages
    mapping(address => uint) balances;


    // Struct: another way to define new types
    struct User {
        uint id;
        string name;
        uint[] connections;
    }
    
}

```