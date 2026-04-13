# Setup

> **Monorepo (this repository, 2026)**  
> Clone this workshop repository. Each lesson is a separate app under **`01-basic-concepts/`**, **`02-non-fungible-tokens/`**, or **`03-ui-non-fungible-token/`**.  
> For each lesson: `cd` into that folder, run `yarn install`, then in separate terminals run `yarn chain`, `yarn deploy`, and `yarn start`.  
> Open [http://localhost:3000](http://localhost:3000).  
> The steps below describe the **original single-repo** FinHub workflow; use them for context, but prefer the lesson folders here.

---

## Local Environment Set Up

Let’s start by cloning this repository

1. Navigate to a directory/folder of your choice using `cd example/directory` and run the following git command in your terminal:

```bash
git clone https://github.com/FinHubSA/EthereumClassWorkshop-2025.git
```

> You’ll find two main packages in the packages directory:
>
> - **hardhat:** This package contains the Hardhat framework, which is used for compiling, testing, and deploying smart contracts.
> - **nextjs:** This package holds the code for the frontend application built with Next.js. It includes everything related to the user interface that interacts with your deployed smart contracts.

- These packages help separate the backend (smart contracts) and frontend (UI), streamlining the development process.

2. Navigate into the `EthereumClassWorkshop-2025` then run the command `yarn install` to install the nodejs libraries

```bash
cd EthereumClassWorkshop-2025
yarn install
```

3. Open your VSCode and click on `file` then `open folder`. Find the folder you cloned your project into, click on it and then click `open` on the popup window.

4. Open a terminal on you VSCode. Let’s start by running a local blockchain in a terminal with `yarn chain`.

```bash
yarn chain
```

5. Open a second terminal and run the command `yarn deploy`, which will compile and deploy the YourContract.sol smart contract, located in the `packages/hardhat/contracts` folder, in the local blockchain.

```bash
yarn deploy
```

6. In a third terminal, run `yarn start` to launch the frontend of your application.

```bash
yarn start
```

7. Open your browser and enter the url `http://localhost:3000`

This is the home page of Scaffold-ETH that we find at localhost:3000:

### Burner Wallet

Scaffold-ETH includes a burner wallet, which is a temporary wallet created directly in the browser. It provides a simple way to quickly interact with and test your contracts on a local blockchain environment without needing to set up a persistent wallet or manually manage private keys.

### Local Faucet

Our burner wallet starts with a balance of 0 ETH, but Scaffold-ETH has a built-in faucet feature that allows you to easily add ETH to your burner wallet.

### Debug page

In the top left corner of the interface, you can navigate to the ‘Debug Contracts’ page, which allows you to interact with and test your deployed smart contract:

This page reports the variables and the functions defined in YourContract:

For example we can test the setGreeting function to set a new value for greeting:

In this case we have used the function setGreeting to update the value of the variable greeting from “Building Unstoppable Apps!!!” to “Hello World”.

### Block Explorer

Scaffold-ETH also includes a block explorer, which you can access via the button in the bottom left corner of the page:

In this page we can check the transactions that we have executed with our wallet.
