# Simple UI Example

> **This monorepo:** do the practical in **`03-ui-non-fungible-token/`**. Run `yarn install` there, then follow that folder’s [wiki/README.md](../03-ui-non-fungible-token/wiki/README.md).  
> **Scaffold-ETH 2 hooks:** [docs.scaffoldeth.io — Hooks](https://docs.scaffoldeth.io/hooks/) (replaces older docs links below).  
> Ignore branch `simple-nft-ui-tut` below if you are only using this repository.

---

In this prac we'll add a simple feature to the UI. We'll enable users to approve an NFT for a specific address. The approve function in an ERC-721 smart contract allows the owner of an NFT to grant permission to another address to transfer that NFT on their behalf. This is commonly used in marketplaces, escrow systems, and delegated transfers.

For example, a user owns an NFT and wants to sell it on an NFT marketplace like OpenSea. The marketplace does not own the NFT but needs approval to transfer it when it's sold. The user approves the marketplace contract to handle their NFT.

# Key Points

These are the key points to note for ERC-721 Token Approvals.

1. Per-token approval (approve)

- Grants a single address permission to transfer one specific NFT.
- Overwrites any previous approval for that token.
- Does not allow multiple approvals for the same NFT.

2. Operator approval (setApprovalForAll)

- Grants an address permission to transfer all of the owner's NFTs.
- Used by marketplaces and escrow services.
- Can be revoked anytime.
- It allows multiple operators to have the ability to transfer your tokens.

3. Approvals Can Be Overwritten

- Calling approve(newAddress, tokenId) overwrites any previous approval for that token.
- Only one address can be approved at a time per token.
- If approve(address(0), tokenId) is called, it revokes approval for that token.
- setApprovalForAll(operatorAddress, false) revokes approval for that operator.

4. Approved Addresses Can Transfer NFTs

# Practical

> **Note:** Documentation for Scaffold-ETH hooks can be found [here](https://docs.scaffoldeth.io/hooks/).

## Setup

1. First commit all changes on the current branch you are working on:

```bash
git add -A
git commit -m "tut changes"
```

2. Now use the branch `simple-nft-ui-tut`:

```bash
git fetch upstream simple-nft-ui-tut
git checkout --track origin/simple-nft-ui-tut
```

3. Start your local chain:

```bash
yarn chain
```

4. Let us deploy the SMs (smart contract).

> Note: make sure your local chain is running using: yarn chain

```bash
yarn deploy
```

5. Start your application

```bash
yarn start
```

6. Open your browser and go to localhost:3000

## To Do's

1. Run the tests. They should fail.

```bash
yarn test test/YourCollectible.ts
```

2. We'll fix the `_approve` method.

- `TODO: get the currently approved address for the tokenId`

> Note: We'll need the address to delete the tokenId.

- `TODO: call the _approve logic of the parent ERC721 smart contract`

- `TODO: if the previous approved is the same as the new approved address return`

> Note: if nothing is changing return so that we do not repeat approved tokenIds

- `TODO: add the tokenId to the address's approved array`

> Note: check if the new approval address is not the zero address

- `TODO: delete the previous tokenId from the address's approved array`

3. We'll add a new section to view approved tokens for the connected address.
Navigate to `packages/nextjs/app/myNFTs/_components/MyHoldings.tsx` in visual studio.

- `TODO: create a state variable called myApprovedCollectibles of typle Collectible[]`

- `TODO: create a state variable called approvedCollectiblesLoading of type bool`

- `TODO: create a useEffect Hook to get approved tokens and update the myApprovedCollectibles state variable`

> Note: For approved NFTs the owner is not the current wallet's address. Update the owner of the NFT.

- `TODO: use approvedCollectiblesLoading in the loading element`

- `TODO: write code to show myApprovedCollectibles in the same way that myAllCollectibles are shown`

4. We'll connect to the Sepolia Test network

- `TODO: change chains.hardhat to chains.sepolia in the file packages/nextjs/scaffold.config.ts`

> Note: this config file tells our web application the networks we are connecting to

- `TODO: Install the [metamask](https://chromewebstore.google.com/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn) extension in your browser`

> Note: Keep the wallet seed phrase SAFE. Write them down and store them on the cloud (somewhere safe)

- `TODO: Connect to the Sepolia network and create a new account`

- `TODO: Send ether to your Sepolia account from this [faucet](https://cloud.google.com/application/web3/faucet/ethereum/sepolia)`

> Note: first copy your accounts address on metamask. Put that address in the input for the address on the link above.

5. We'll deploy to the Sepolia Test network

- `TODO: Copy you private key for the account you just created`

- `TODO: Run this in your terminal: yarn account:import`

- `TODO: Enter your private key when requested (keep it simple we're just testing e.g. 123456)`

- `TODO: deploy your smart contract onto the Sepolia network using: yarn deploy --network sepolia`

---

*Source: copied from the FinHubSA ethereum-class-workshop-2025 wiki (Simple UI Example).*
