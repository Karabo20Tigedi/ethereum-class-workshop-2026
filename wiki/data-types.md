# Data Types

## Value Types

The following data types are called value types because they are copied when used in functions.

- `bool`: boolean can only have two possible values, `true` and `false`

```javascript
bool b = true;
```

- `uint`/`int`: unsigned and signed integers. Unsigned integers can only be positive, including the zero, wheras signed integers can also be negative. The default size in 256 bits, but they can range from 8 to 256 bits in steps of 8. To indicate another size, define them as `uint64` or `int64`, respectively.

```javascript
uint  u =  1;
int64 i = -3;
```

- `fixed` / `ufixed`: Signed and unsigned fixed point number of various sizes. They are defined as `fixedMxN` and `ufixedMxN` where M is the number of bits before the dot and N is the number of decimal points. `M` lies between 8 and 256 bits and must be divisible by 8. `N` must be between 0 and 80, inclusive. **Note:** Fixed point numbers are not fully supported by Solidity yet. They can be declared, but cannot be assigned to or from.

```javascript
ufixed8x2 f = 3.14;
```

- `address`: holds an Ethereum address, which is 42 characters long and 20 bytes large. The type `address` has the following members:

  - `address.balance` returns the balance of the given address
  - `address.transfer(amount)` transfers x Ether from the current account to the address specified
  - `address.call("function", "parameter")` calls a contract function with the given parameter. Has access to contract's functions, storage, balance, ...
  - `address.delegatecall("function", "parameter")` is similar to above but only uses other contracts functions. Allows user to use library code stored in other contract

```javascript
address a = 0x281055afc982d96fab65b3a49cac8b878184cb16;
```

- `bytesN`: fixed-size byte array where N can be between 1 and 32. It has one member, `length`.

```javascript
bytes32(0x01020304);
// 0x0000000000000000000000000000000000000000000000000000000001020304
bytes32("01020304");
// 0x3031303230333034000000000000000000000000000000000000000000000000
```

- `enum`: one way to define a user-specific data structure. They are explicitly convertible to and from all integer types. They are often useful for making code more readable and maintainable, because one can use descriptive names without the performance penalty of string comparisons.

```javascript
enum moveChoice { moveLeft, moveRight, moveStraight, stayStill };
```

- `function`: see [Functions](functions.md)

## Reference Types

### Arrays

Arrays can have a fixed or dynamic size and can hold any type of data type (including other arrays).

```javascript
// an array of booleans of length 10
bool[3] b = [true, true, false];
// an array of addresses of dynamic length
address[] a;
// an array of 5 dynamic arrays of uints (illustrative)
uint[][5] m;
```

Special arrays:

- `bytes`: is similar to `byte[]`, but it is more efficient
- `string`: holds strings, which are marked by single or double quotes. For now, it does not allow for length or index access

```javascript
string h = 'Hello World'
string y = "you are cool"
```

Members:

- length: holds an array's number of elements. Using `someArray.length = 10`, dynamic arrays can be resized in memory.
- push: is used to append elemnts to a dynamic storage array. The return value of that function is the new length.

```javascript
uint8[] u = [1, 2, 3];
u.push(4);
// u = [1, 2, 3, 4]
```

### Structs

Structs are the second type of user-specific data types. In contrast to enums, they are data structures that hold zero or more pieces of data of variable type and size. Struct types can be used inside mappings and arrays and they can itself contain mappings and arrays, but not other structs.

```javascript
struct Student {
    address addr;
    string name;
    uint age;
}
Student julia = Student(0x281055afc982d96fab65b3a49cac8b878184cb16, 'Julia', 25);
```

### Data location

Every complex type, i.e. arrays and structs, has an additional annotation, the "data location", about whether it is stored in memory or in storage.

- `memory`: function parameters
- `storage`: state variables

## Mappings

Mappings can be understood as hash tables, mapping a key to any kind of value. The key is not actually stored but only its `keccak256` hash. The value can be any type, including dynamic arrays, structs, mappings, and even contracts. Because of this flexibility, a mapping does not have a `length` member.

```javascript
mapping (address => uint) balances;
balances[msg.sender] = 20;
```
