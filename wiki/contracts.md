# Contracts

A contract is what in other programming languages would be considered a class. They contain state variables that are altered by functions.

```javascript
pragma solidity ^0.5.0;         // defines the compiler version

contract ExampleCoin {
    // State variables hold information
    // accessible to the contract
    address public minter;
    mapping (address => uint) public balances;

    // Events allow clients to react to specific
    // contract changes you declare
    event Sent(address from, address to, uint amount);

    // Constructor code is only run when the contract
    // is created
    constructor() public {
        minter = msg.sender;
    }

    // Sends an amount of newly created coins to an address
    // Can only be called by the contract creator
    function mint(address receiver, uint amount) public {
        require(msg.sender == minter, "Function can only be called by minter.");
        require(amount < 1e60, "Amount is too high.");
        balances[receiver] += amount;
    }

    // Sends an amount of existing coins
    // from any caller to an address
    function send(address receiver, uint amount) public {
        require(amount <= balances[msg.sender], "Insufficient balance.");
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```

Source: adapted from [Solidity documentation](https://solidity.readthedocs.io/en/v0.5.11/introduction-to-smart-contracts.html)

The line `address public minter` declares a state variable `minter` of type address that is publicly accessible. The keyword `public` automatically generates a getter-function that allows you to access the current value of the state variable. This function can either be called internally or via transactions from other contracts or users. By default, state variables are private, meaning that without the `public` keyword, other contracts have no possibility to access the variable.

The deployed contract will have its own contract address (different from the deployer’s address) on the blockchain. This address is accessible in a smart contract using the keyword `this`, e.g. `address myAddress = address(this);` stores the public address of the deployed contract under the variable `myAddress`.

The next line, `mapping (address => uint) public balances`, also creates a public state variable, `balances`, that allows addresses to be mapped to unsigned integers. Since the variable is public, there is no need to define a getter-function but it is defined automatically. The following snippet shows this function. `balances` returns a particular `uint` corresponding to an input `address _account`.

```javascript
function balances(address _account) returns (uint) {
    return balances[_account];
}
```

Getter functions have external visibility. If a concept is accessed internally (i.e. without `this.`), it is evaluated as a state variable. If it is accessed externally (i.e. with `this.`), it is evaluated as a function.

```javascript
contract C {
    uint public data;
    function x() {
        data = 3; // internal access
        uint val = this.data(); // external access
    }
}
```

The line `event Sent(address from, address to, uint amount)` declares the event `Sent`, which is executed in the last line of the function `send`. User interfaces are able to listen to events being fired on the blockchain without much cost. As soon as it is fired, the listener will also receive the arguments `from`, `to` and `amount`, which makes it easy to track transactions. Events allow light clients to track and react to transactions efficiently.

When a contract is created, the `constructor` function is executed only once and never again. While deploying the contract, the constructor is invoked and is used to initialize the state variables. It permanently stores the address of the person creating the contract. The information is retrieved from the global variable `msg`, that contains some properties which allow access to the blockchain. `msg.sender` always stores the address of the user or contract executing the current (external) function call.

The two functions `mint` and `send` are accessible only to users because they are external. `mint`, however, can only be successfully executed by the creator of the contract because it checks if the message sender is the minter (note that is functionality could have also been implemented as a modifier). If another user calls this function, it will return without executing the mining. The `mint` function controls the supply of the currency by issuing new coins to the creator of the contract.

On the other hand, `send` can be used by anyone who already has some of these coins to send coins to somebody else. Note that if you use this contract to send coins to an address, you will not see these coins when you look at that address on an Ethereum blockchain explorer because the balance is only stored in the data storage of that particular coin contract. By the use of events, however, it is relatively easy to create your own “blockchain explorer” that tracks transactions and balances of your new coin.

## Inheritance

A contract can inherit code from one or multiple contracts. The inheritance system is very similar to the one of Python.

```js
pragma solidity ^0.5.0;

contract Owned {

    address owner;

    constructor () {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner);
        _;
    }
}

contract ExampleCoin is Owned{

    mapping (address => uint) public balances;

    event Sent(address from, address to, uint amount);

    function mint(address receiver, uint amount) external onlyOwner {
        require(amount < 1e60, "Amount is too high.");
        balances[receiver] += amount;
    }

    function send(address receiver, uint amount) public {
        require(amount <= balances[msg.sender], "Insufficient balance.");
        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount);
    }
}
```

The superior contract is Owned, that sets the state variable `owner` on construction. It also defines a modifier `onlyOwner`.

The contract `ExampleCoin` inherits from `Owned`. Therefore, it has access to the state variable `owner` and the modifier `onlyOwner`.
