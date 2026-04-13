# Functions

Functions are executable units of codes. A very simplistic function would be something like

```javascript
function meaningOfLife() returns (uint) {
    return 42;
}
```

The above defined function is called `meaningOfLife`, it takes no input parameters and returns a `uint` which is 42. Here, the visibility is set to public by default, but there are other types of visibilities:

- `public`: the function can be accessed by everybody
- `external`: the function can only be accessed from outside, but not be the contract it is defined in
- `internal`: the function can only be accessed by the contract it is defined in and all contracts inheriting from it
- `private`: the function can only be accessed by the contract it is defined in but not from child contracts (default)

Furthermore, we can define the type of a contract:

- `view`: the function will not alter the storage state

```javascript
address addr;
function viewFunction() view returns (uint) {
    return addr.balance;
}
```

- `constant`: obsolete, use `view`
- `pure`: the function will not even access the storage state

```javascript
function pureFunction() pure returns (bool) {
    return true;
}
```

- `payable`: the function allows a contract to receive Ether. This is used on platforms like online stores. The Ether are stored in the contract and there needs to be a special function to withdraw them, otherwise they are lost

```js
contract OnlineStore {
  function buySomething() external payable {
    require(msg.value == 1 ether);
    transferThing(msg.sender);
  }
}
```

In general, a function is defined as

```javascript
function (<parameter types>) {public|external|internal|private} [view|pure|payable] [returns (<return types>)]
```

### Fallback functions

A fallback function is a function without a name. A smart contract can have exactly one fallback function. This function is executed whenever the contract receives Ether. For a function to be able to receive Ether, it has to be marked as `payable`.

```javascript
receive() external payable { }
```

### Function Overloading

You may define several functions in one contract that all have the same name, as long as they differ in the arguments they take. This also holds for inherited functions.

### Modifiers

Function modifiers extend a function by, for instance, checking a precondition. A common use case is to restrict the execution of a function to only the owner of the contract

```javascript
address owner;

modifier onlyOwner(){
    require(msg.sender == owner);
    _;
}

function doSomething() onlyOwner {
    // some logic
}
```

`require` is a built-in function that checks the condition specified next to it. The `_;` is mandatory. It is a placeholder for the function logic the modifier is applied to. The function `doSomething()` is modified by `onlyOwner`, meaning that the contract will first check whether the sender is the owner and if so, the logic of `doSomething()` will be applied. If not, the call is reverted.
