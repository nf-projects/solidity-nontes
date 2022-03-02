# Solidity Programming

# Start of Project

```solidity
pragma solidity >=0.5.0 <0.6.0;
// must contain version

contract HelloWorld {
	// contract 

}
```

# Integers

```solidity
contract Example {
  // This will be stored permanently in the blockchain
  uint myUnsignedInteger = 100;
}
```

- `uint` - only positive numbers
- `int` - positive & negative numbers
- by default `256` size, but can be specific: `uint8`, `uint16`, `uint32`, etc

# Structs

<aside>
💡 Custom data types containing multiple primitive data types

</aside>

```solidity
struct Person {
  uint age;
  string name;
}
```

# Arrays

```solidity
// Array with a fixed length of 2 elements:
uint[2] fixedArray;
// another fixed Array, can contain 5 strings:
string[5] stringArray;
// a dynamic Array - has no fixed size, can keep growing:
uint[] dynamicArray;
```

### Array Push

```solidity
uint[] numbers;
numbers.push(5);
numbers.push(10);
numbers.push(15);
// numbers is now equal to [5, 10, 15]
```

# Public Modifier

- Automatically creates `Getter` method
- Example:

```solidity
// public string array
String[] public people;
```

# Functions

Example:

```solidity
function eatHamburgers(string memory _name, uint _amount) private {

}
```

- Parameters should start with `_`

### Private & Public Functions

- **PRIVATE:** Can only be called within the contract
    - Function name should start with `_` if it’s private
- **PUBLIC:** Can be called externally

### Argument Types:

1. Value (adding `memory` modifier) passes the value
    1. Should be prefixed with `_`
2. Reference (no modifier) passes the reference, and updates the variable if the function updates it

### Function Returns

`function sayHello() public view returns (string memory)`

```solidity
string greeting = "What's up dog";

function sayHello() public returns (string memory) {
  return greeting;
}
```

- View - doesn’t change any values (like example above)
- Pure - return depends on its parameters:

```solidity
function _multiply(uint a, uint b) private pure returns (uint) {
  return a * b;
}
```

# Keccak256, Random Hashes

<aside>
💡 `keccak256` basically returns a 256-bit number based on a “seed”

</aside>

```solidity
//6e91ec6b618bb462a4a6ee5aa2cb0e9cf30f7a052bb467b0ba58b8748c00d2e5
keccak256(abi.encodePacked("aaaab"));
//b1f078126895a1424524de5321b339ab00408010b7cf0e6ed451514981e58aa9
keccak256(abi.encodePacked("aaaac"));
```

# TypeCasting

→ Casting variables similar to Java

```solidity
uint8 a = 5;
uint b = 6;
// throws an error because a * b returns a uint, not uint8:
uint8 c = a * b;
// we have to typecast b as a uint8 to make it work:
uint8 c = a * uint8(b);
```

# Events

→ You can emit events that the frontend will listen to (to notify the frontend of something happening)

```solidity
// declare the event
event IntegersAdded(uint x, uint y, uint result);

function add(uint _x, uint _y) public returns (uint) {
  uint result = _x + _y;
  // fire an event to let the app know the function was called:
  emit IntegersAdded(_x, _y, result);
  return result;
}
```

# Web3.js

<aside>
💡 Web3.js powers the frontend and interacts with Solidity contract in the backend

</aside>

# Addresses

→ The `address` variable type stores an Ethereum wallet adddress

# Mappings

→ Key-value stores with a key and a value, for example:

```solidity
mapping (address => uint) public accountBalance;
```
