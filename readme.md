# Programs in PYQs

## **1. Find the second largest element in an array (5m – May 23)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SecondLargest {
    uint[] public numbers;

    function add(uint _num) public {
        numbers.push(_num);
    }

    function getSecondLargest() public view returns (uint) {
        uint largest = 0;
        uint second = 0;

        for (uint i = 0; i < numbers.length; i++) {
            if (numbers[i] > largest) {
                second = largest;
                largest = numbers[i];
            } else if (numbers[i] > second && numbers[i] != largest) {
                second = numbers[i];
            }
        }
        return second;
    }
}
```

* **Key logic:** one loop to track both largest and second largest.
* **Data stored on-chain** using a dynamic array.


## **2. Check if a number is prime (5m – Dec 22)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract PrimeCheck {
    function isPrime(uint num) public pure returns (bool) {
        if (num < 2) return false;
        for (uint i = 2; i * i <= num; i++) {
            if (num % i == 0) {
                return false;
            }
        }
        return true;
    }
}
```

* **Logic:** divides `num` by all integers up to √num.
* **Marked `pure`** since it doesn’t read/write blockchain state.


## **3. Multi-level inheritance (10m – Dec 24, Dec 22)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Base contract
contract A {
    function getA() public pure returns (string memory) {
        return "This is Contract A";
    }
}

// Derived from A
contract B is A {
    function getB() public pure returns (string memory) {
        return "This is Contract B";
    }
}

// Derived from B (and indirectly from A)
contract C is B {
    function getC() public pure returns (string memory) {
        return "This is Contract C";
    }
}
```

* **Multi-level:** C → B → A.
* Functions from A and B are inherited by C automatically.



## **4. Single inheritance (10m – May 23)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Base contract
contract Parent {
    function getParent() public pure returns (string memory) {
        return "This is Parent Contract";
    }
}

// Derived contract using single inheritance
contract Child is Parent {
    function getChild() public pure returns (string memory) {
        return "This is Child Contract";
    }
}
```

* **Single inheritance:** Child inherits only from Parent.
* Functions from Parent are accessible in Child directly.



### Example programs
`Simple Calculator`
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleCalc {
    uint public result;

    function add(uint a, uint b) public returns (uint) {
        result = a + b;
        return result;
    }

    function subtract(uint a, uint b) public returns (uint) {
        result = a - b;
        return result;
    }

    function multiply(uint a, uint b) public returns (uint){
        result = a*b;
        return result;
    }
}
```


### **1. Multiplication and Division**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleMath {
    uint public result;

    function multiply(uint a, uint b) public returns (uint) {
        result = a * b;
        return result;
    }

    function divide(uint a, uint b) public returns (uint) {
        result = a / b; // no check for division by zero
        return result;
    }
}
```


### **2. Square and Cube**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract PowerCalc {
    uint public result;

    function square(uint a) public returns (uint) {
        result = a * a;
        return result;
    }

    function cube(uint a) public returns (uint) {
        result = a * a * a;
        return result;
    }
}
```


### **3. Modulus (Remainder)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ModulusCalc {
    uint public result;

    function mod(uint a, uint b) public returns (uint) {
        result = a % b;
        return result;
    }
}
```


### **4. Increment and Decrement**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Counter {
    uint public count;

    function increment() public returns (uint) {
        count = count + 1;
        return count;
    }

    function decrement() public returns (uint) {
        count = count - 1;
        return count;
    }
}
```


### **5. Store and Retrieve a Number**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StoreNumber {
    uint public number;

    function setNumber(uint _num) public {
        number = _num;
    }

    function getNumber() public view returns (uint) {
        return number;
    }
}
```

### **6. Add Two Numbers (no state variable)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Adder {
    function add(uint a, uint b) public pure returns (uint) {
        return a + b;
    }
}
```


### **7. Multiply Two Numbers (no state variable)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Multiplier {
    function multiply(uint a, uint b) public pure returns (uint) {
        return a * b;
    }
}
```



### **8. Concatenate Strings**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract StringConcat {
    function concat(string memory a, string memory b) public pure returns (string memory) {
        return string(abi.encodePacked(a, b));
    }
}
```



### **9. Get the Sender’s Address**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SenderInfo {
    function getSender() public view returns (address) {
        return msg.sender;
    }
}
```



### **10. Get the Current Block Timestamp**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BlockInfo {
    function getTime() public view returns (uint) {
        return block.timestamp;
    }
}
```


### **11. Store and Get Array Elements**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleArray {
    uint[] public numbers;  // dynamic array

    function addNumber(uint _num) public {
        numbers.push(_num); // add to array
    }

    function getNumber(uint index) public view returns (uint) {
        return numbers[index]; // get by index
    }

    function getLength() public view returns (uint) {
        return numbers.length; // array size
    }
}
```



### **12. Fixed-Size Array Example**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract FixedArray {
    uint[3] public nums = [1, 2, 3];  // fixed-size array

    function setNumber(uint index, uint value) public {
        nums[index] = value;  // update at index
    }

    function getNumber(uint index) public view returns (uint) {
        return nums[index];   // fetch value
    }
}
```



### **13. Sum of All Elements**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ArraySum {
    uint[] public numbers;

    function add(uint _num) public {
        numbers.push(_num);
    }

    function sum() public view returns (uint) {
        uint total = 0;
        for (uint i = 0; i < numbers.length; i++) {
            total += numbers[i];
        }
        return total;
    }
}
```



### **14. Replace an Element**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ReplaceElement {
    uint[] public nums;

    function add(uint _num) public {
        nums.push(_num);
    }

    function replace(uint index, uint newValue) public {
        nums[index] = newValue;
    }
}
```


### **15. Delete an Element (Resets to 0 but keeps length)**

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract DeleteElement {
    uint[] public nums;

    function add(uint _num) public {
        nums.push(_num);
    }

    function remove(uint index) public {
        delete nums[index]; // resets value at index to 0
    }
}
```


