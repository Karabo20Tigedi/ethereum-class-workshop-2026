# Basic Concepts

Solidity is a programming language that looks similar to JavaScript and is used to write smart contracts on Ethereum. Solidity code needs to be compiled in bytecode in order to be understood by the Ethereum Virtual Machine (EVM). The language is strongly typed with the possibility to define custom data structures. A great way to learn solidity is by following these tutorials at [solidity by example](https://solidity-by-example.org/)

### File Ending

Files that contain solidity code need to end in ".sol".

### Pragma

Every solidity file starts with a line like

```javascript
pragma solidity ^0.5.0;
```

This statement is meant for the compiler. This pragma ensures that the source code is only meant for compiler versions that are not older than 0.5.0 and not newer than 0.6.0. This ensures that the contract always compiles the way we intended it because compilers within this range are backward compatible.

### Imports

You may import other ".sol" files from the same directory by calling

```javascript
import "./MyContract.sol";
```

or

```javascript
import "./MyContract.sol" as SomeContract;
```

### Comments

Single-line comments (//) and multi-line comments (/\*...\*/) are possible.

```javascript
// This is a single-line comment.

/*
This is a
multi-line comment.
*/
```

### Global variables

The global namespace holds some special variables and functions, that provide you with general information. These are the following ([Source](https://solidity.readthedocs.io/en/latest/units-and-global-variables.html)):

- `block.blockhash(uint blockNumber) returns (bytes32)`: hash of the given block - only works for 256 most recent, excluding current, blocks - deprecated in version 0.4.22 and replaced by blockhash(uint blockNumber).
- `block.coinbase (address)`: current block miner’s address
- `block.difficulty (uint)`: current block difficulty
- `block.gaslimit (uint)`: current block gaslimit
- `block.number (uint)`: current block number
- `block.timestamp (uint)`: current block timestamp as seconds since unix epoch
- `gasleft() returns (uint256)`: remaining gas
- `msg.data (bytes)`: complete calldata
- `msg.gas (uint)`: remaining gas - deprecated in version 0.4.21 and to be replaced by gasleft()
- `msg.sender (address)`: sender of the message (current call)
- `msg.sig (bytes4)`: first four bytes of the calldata (i.e. function identifier)
- `msg.value (uint)`: number of wei sent with the message
- `now (uint)`: current block timestamp (alias for block.timestamp)
- `tx.gasprice (uint)`: gas price of the transaction
- `tx.origin (address)`: sender of the transaction (full call chain)

### Gas

Every transaction, i.e. every execution of Solidity code on the EVM, costs gas. The concept ensures that code does not run forever and clogs up the system. It also incentivizes developers to program efficiently because user's won't use contract functionality that is too expensive.

Gas is linked to "real money" in form of Ether by the gas price. Each gas that is burned during a transaction therefore costs one unit of whatever you specified as your gas price. Therefore, be careful when setting it. If it is too high, it will cost you a fortune. If it is too low, it may take forever for your transaction to be mined. You can find an overview of the current gas prices on the Ethereum main chain [here](https://ethgasstation.info/).
