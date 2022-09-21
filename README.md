## Solidity Tutorial
Learn Solidity From Examples.

## Table of Contents  
- [Solidity Tutorial](#solidity-tutorial)
- [Table of Contents](#table-of-contents)
- [Online IDE](#online-ide)
- [Basic Structure](#basic-structure)
- [Data Types](#data-types)
- [Operators](#operators)
- [Vaiable Types](#vaiable-types)
- [Statement](#statement)
- [Function](#function)


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
contract BasicStructure {
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

contract DataTypes {
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

[🔝Back to Table of Contents](#table-of-contents)


## Operators
List of operators with order of precedence

| Precedence           | Description                                                       | Operator                                 |
| -------------------- | ----------------------------------------------------------------- | ---------------------------------------- |
| _1_                  | Postfix increment and decrement                                   | `++`, `--`                               |
| _1_ | New expression       | `new <typename>`                                                  |
| _1_ | Array subscripting   | `<array>[<index>]`                                                |
| _1_ | Member access        | `<object>.<member>`                                               |
| _1_ | Function-like call   | `<func>(<args...>)`                                               |
| _1_ | Parentheses          | `(<statement>)`                                                   |
| _2_                  | Prefix increment and decrement                                    | `++`, `--`                               |
| _2_ | Unary minus          | `-`                                                               |
| _2_ | Unary operations     | `delete`                                                          |
| _2_ | Logical NOT          | `!`                                                               |
| _2_ | Bitwise NOT          | `~`                                                               |
| _3_                  | Exponentiation                                                    | `**`                                     |
| _4_                  | Multiplication, division and modulo                               | `*`, `/`, `%`                            |
| _5_                  | Addition and subtraction                                          | `+`, `-`                                 |
| _6_                  | Bitwise shift operators                                           | `<<`, `>>`                               |
| _7_                  | Bitwise AND                                                       | `&`                                      |
| _8_                  | Bitwise XOR                                                       | `^`                                      |
| _9_                  | Bitwise OR                                                        | `\|`                                      |
| _10_                 | Inequality operators                                              | `<`, `>`, `<=`, `>=`                     |
| _11_                 | Equality operators                                                | `==`, `!=`                               |
| _12_                 | Logical AND                                                       | `&&`                                     |
| _13_                 | Logical OR                                                        | `\|\|`                                     |
| _14_                 | Ternary operator                                                  | `<conditional> ? <if-true> : <if-false>` |
| _14_ | Assignment operators | `=`,`\|=`, `^=`, `&=`, `<<=`, `>>=`, `+=`, `-=`, `*=`, `/=`, `%=` |
| _15_                 | Comma operator                                                    | `,`                                      |


[🔝Back to Table of Contents](#table-of-contents)


## Vaiable Types
```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.17;

contract VariableTypes {
    // State variable: values are permanently stored in a contract storage.
    uint state_variable;
    /* State variable visibility
    - private: only available inside the contract that defines it (default)
    - internal: only available inside the contract that defines it AND 
                any contracts that inherit it
    - public: available to any contract or third party that wants to call it
    */
    uint private default_private_variable;
    uint internal internal_variable;
    uint public public_variable;

    function getSummation() public pure returns(uint) {
        // Local variable: values are available only within a function where it is defined
        uint local_variable1 = 2;
        uint local_variable2 = 3;
        return local_variable1 + local_variable2;
    }
    
    function getSender() public view returns(address) {
        // Global Variables − Special variables exists in the global namespace used to 
        // get information about the blockchain
        // Application Binary Interface operations. Ex:
        abi;
        // Block information. Ex:
        block.number;
        // Message information. Ex:
        msg.data;
        // Transaction information. Ex:
        tx.gasprice;
        // Different fuinctions. Ex:
        // assert, require, keccak256, sha256
        return msg.sender;
    }
}
```


[🔝Back to Table of Contents](#table-of-contents)


## Statement
```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.17;

contract Statement {
    uint time = 5;
    string greeting;

    function conditionalStatement() public {
        // if, else if, else is just like other programming languages
        if (time < 10) {
            greeting = "Good morning";
        } else if (time < 20) {
            greeting = "Good day";
        } else {
            greeting = "Good evening";
        }

        // Ternary operator
        greeting = time < 15 ? "Day" : "Night";

    }

    function loop() public {
        // for loop is same as other programming languages
        for (uint i = 1; i < 10; i++) {
            greeting = "";
        }

        // while loop is also same as other programming languages
        while (time <= 10) {
            time++;
        }

        // loops also supports break and continue
        while(true) {
            time++;

            if (time == 0) {
                continue;
            }

            if (time == 25) {
                break;
            }
        }
    }

}
```


[🔝Back to Table of Contents](#table-of-contents)


## Function
```solidity
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.17;

contract Functions {
    /*
    function myFunction(type var1, type var2) <visibility-specifier> <modifier> returns (bool) {
        return true;
    }

    Funtion can receive arguments but it's not required.
    Data type of arguments should be specified.

    Function Visibility Specifiers defines who has access to the functions in your contract.
    A function’s visibility can be set to
    Private: only available inside the contract that defines it.
    Internal: only available inside the contract that defines it AND 
              any contracts that inherit it
    External: only be called by external contacts.
              Not visible inside the contract that defines it.
    Public: available to any contract or third party that wants to call it.

    Modifiers dictate a Solidity functions behavior
    view: functions are read only functions and do not MODIFY the state variables
    pure: more restrictive then view functions and do not READ or MODIFY state variables
    payable: functions provide a mechanism to receive funds in your contract
    If not specified that means function can access and modify state variables

    Function can return value but it's not required.
    Data type of the return value should be specified.
    */

    uint amount;

    // Writes a state variable, publicly available function
    function setStaticAmount() public {
        amount = 10;
    }

    // Writes a state variable from an argument
    function setAmount(uint _amount) public {
        amount = _amount;
    }

    // Reads a state variable
    function getAmount() public view returns(uint) {
        return amount;
    }

    // Never accessed a state variable
    function getStaticValue() public pure returns(uint) {
        uint local_variable = 10;
        return local_variable;
    }

    function getSummation(uint a, uint b) public pure returns(uint) {
        return a + b;
    }

    // Only this contact can access it
    function getMultiplication(uint a, uint b) private pure returns(uint) {
        return a * b;
    }

    // Inherited contracts also have access to this funtion 
    function getSubtraction(uint a, uint b) internal pure returns(uint) {
        return a - b;
    }

    // Only external contracts have access to it 
    function getExponent(uint a, uint b) external pure returns(uint) {
        return a ** b;
    }

    
    // payable is added to this function so another contract can call it and
    // send ether to this contract
    function payMeMoney() public payable {
        amount += msg.value;
    }
}
```

[🔝Back to Table of Contents](#table-of-contents)

