# Simple Staking Example

> **This monorepo:** do the practical in **`01-basic-concepts/`**. Run `yarn install` there, then follow that folder’s [wiki/README.md](../01-basic-concepts/wiki/README.md).  
> Use `yarn workspace @se-2/hardhat test test/StakingContract.ts` or `cd packages/hardhat && yarn test test/StakingContract.ts`.  
> Ignore branch `basic-concepts-tut` below if you are only using this repository.

---

In this prac we'll go through the basic concepts of smart contract development using Solidity. Let's start by doing some admin on our git repository.

# Git Environment Set Up

1. Navigate to the directory that you cloned the EthereumClassWorkshop repository into using `cd example/directory/EthereumClassWorkshop-2025` and run the following git command in your terminal to check the remote git repositories your local one is linked to:

```bash
git remote -v
```

2. The command will show that the origin points to the FinHub's github repository. We do not want you to change the FinHub's github repository. We would like to change the origin to point to your own github repository. Firstly let us create your own repository on Github. In your browser go to [github.com](https://github.com/) and:

- Create an account or login
- After logging in, click on `new` to add a new repository
- Fill in the 'Repository Name' e.g. EthereumClassWorkshop-2025
- Leave everything as default and click on 'Create Repository'

- Copy the link to your repository

- In your terminal, run the command below to add a link to a remote repository from your local repository. Replace with the link you copied above:

```bash
git remote set-url origin <copied-url>
```

- Run the command again. This time it should show the `origin` url's for fetch and push.

```bash
git remote -v
```

- The origin tag now points to your own Github repository.

3. We also want to be able to fetch from the repository that in owned by FinHubSA. To do this, in your browser go the [FinHubSA EthereumClassWorkshop-2025](https://github.com/FinHubSA/EthereumClassWorkshop-2025) repository.

- Copy the HTTPS link
- In your terminal, run the command below to add a link to the new remote repository from your local repository. Replace with the link you copied above:

```bash
git remote add upstream <copied-url>
git remote -v
```

- Note: There are now 2 remote repositories linked to your local repository

4. Now fetch the branch called `basic-concepts-tut` from the upstream repository and create a new local branch using the remote branch you fetched:

```bash
git fetch upstream basic-concepts-tut
git checkout -b basic-concepts-tut upstream/basic-concepts-tut
```

5. Run `yarn install` to make sure all dependencies are installed

```bash
yarn install
```

We'll use test driven development (TDD) to learn about the basics of smart contract development. Test Driven Development (TDD) is a software development practice where developers write automated tests before writing the actual code that needs to be tested. Developers create unit test cases before developing the actual code. It is an iterative approach combining Programming, Unit Test Creation, and Refactoring.

# Test Driven Development

Scaffold-Eth uses the Chai library for tests. Chai is a library of assertions, which allow you to test specific features of your code, within the Mocha test suites framework. Tests are common in software engineering because they help to document the core functionality of the code and make sure that new features do not introduce breaking changes.

## Mocha

Mocha and Chai are two JavaScript frameworks commonly used together for unit testing. Mocha is a testing framework that provides functions that are executed according in a specific order, and that logs their results to the terminal window.

When you read tests written in Mocha, you’ll see regular use of the keywords `describe` and `it`. These keywords, provided by Mocha, provide structure to the tests by batching them into test suites and test cases.

A test suite is a collection of tests all relating to a single functionality or behavior. A test case or a unit test is a single description about the desired behavior of the code that either passes or fails. Test suites are batched underneath the `describe` keyword, and test cases are batched under the `it` keyword.

## Chai

The base component of test cases are assertions. Assertions are tied to particular values (whereas test cases are descriptions of behavior) and they will fail if the expected value does not match the actual value.

Every assertion in a test case must be met in order for the test case to pass.

Chai is an assertion library that is often used alongside Mocha. It provides functions and methods that help you compare the output of a certain test with its expected value. Chai provides clean syntax that almost reads like English!

Example of a Chai assertion: `expect(exampleArray).to.have.lengthOf(3)`;

This code will check whether that the variable exampleArray has a length of three or not.

# Simple Staking Contract

The smart contract we are testing, StakingContract.sol is a simple smart contract that allows users add eth into a staking pool. Whatever they contribute is recorded in the SM and they are able to withdraw it at any time they want. A user is only able to join once. They cannot join again until they withdraw their staking portion. The test file can be found at packages/hardhat/test/StakingContract.ts.

## Practical

Use the branch `basic-concepts-tut`:

```bash
git fetch upstream basic-concepts-tut
git switch basic-concepts-tut
```

1. Run the tests. They should fail.

```bash
yarn test test/StakingContract.ts
```

2. We'll fix `addUser` method. The functionality is tested in the Mocha test case called `Add users`.

- `TODO: make sure the function can receive ether`

> hint: Only functions with `payable` in their signature can receive ether.

- `TODO: use require to check if the user sent ether in the calling transaction`

> hint: The msg.value global variable has the transaction value in wei

- `TODO: use require to check if user already exists or not`

> hint: Use the exists field in the User struct

- `TODO: use require to check if user length is less than MAX_PEOPLE`

> hint: Use solidity's string.concat and OpenZeppelin's Strings.toString method for the requirement error message

> Question: Why do we put the require methods at the top of the method?

- `TODO: create the user object in memory`

> hint: Use the User struct to check the fields to put

- `TODO: store the user in the users key value mapping and the userAddresses array`

- `TODO: emit the UserAdded log`

3. We'll fix `withdraw` method. The functionality is tested in the Mocha test case called `Withdrawals`

- `TODO: get the amount to be withdrawn`

> Note: How can we save gas when accessing the User fields?

- `TODO: use require to check if the user has any money to withdraw`

- `TODO: use the call function on an address object to send Ether to the user`

> Note: The call method transfers ether directly to an EOA. To a smart contract, it calls its fallback() or receive() method. This method should have the payable keyword in their function signature to be able to get ether from a call command.

- `TODO: use require to check if the transfer was successful`

4. We'll fix `_delete` method. The functionality is tested in the Mocha test case called `Withdrawals`

- `TODO: get the user object into memory`

- `TODO: delete the user from the users mapping`

- `TODO: delete the user from users and from the userAddresses array`

> hint: get the address on the last position of the userAddresses array and get the last user using the obtained address.

> hint: put the last address into the position of the address being deleted. after that edit the user's index to be in the deleted user position.

- `TODO: use pop() to remove the last element of the userAddresses array`

5. We'll check how a re-entry attack occurs. A re-entrancy attack is a common smart contract vulnerability in Ethereum where an external contract repeatedly calls back into the vulnerable contract before the first execution is completed. This allows an attacker to drain funds from the contract before its state is updated.

- `TODO: remove the lock modifier on the withdraw method`

- `TODO: in the receive method of AttackerContract.sol, put a method that will be recursively called to withdraw money`

> hint: When we withdraw the targeted/victiom contract should have enough ether for the attacker to withdraw otherwise it throws an error

- `TODO: uncomment the test called 'Should allow a re-entry attack' and comment the one called 'Should not allow a re-entry attack'`

- `TODO: run the tests. They should all pass`

---

*Source: copied from the FinHubSA ethereum-class-workshop-2025 wiki (Simple Staking Example).*
