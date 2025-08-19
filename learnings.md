# Starting with Solidity

### What is Solidity
A programming language that creates smart contracts and instructs them how to behave

### Compilation
Solidity is compiled in binary and it runs on EVM (Ethereum Virtual Machine)

## Syntax

### Pragma version
`pragma` specifies the compiler version of Solidity.



```solidity
// SPDX-License-Identifier: MIT
// compiler version must be greater than or equal to 0.8.26 and less than 0.9.0

pragma solidity ^0.8.26;
```

but in exam , write the following :
```sol
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.2 <0.9.0;
```

### Writing a contract

- Whenever you want to write something in solidity , you should write it with the keyword `contract`
- For example
```sol
contract HelloWorld {
    string public greet = "Hello World!";
}
```

### Primitive Data types

`uint`
- `uint` stands for unsigned integer, meaning non negative integers
- it has different sizes available
```sol
uint8   ranges from 0 to 2 ** 8 - 1
uint16  ranges from 0 to 2 ** 16 - 1
.....................................
uint256 ranges from 0 to 2 ** 256 - 1
```
- `uint` is just an alias for `uint256`.
- Example 
```sol
uint8 public u8 = 1;
uint256 public u256 = 456;
uint256 public u = 123; // uint is an alias for uint256

```