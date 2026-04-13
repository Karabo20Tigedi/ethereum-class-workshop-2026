# Simple NFT Example

> **This monorepo:** do the practical in **`02-non-fungible-tokens/`**. Run `yarn install` there, then follow that folder’s [wiki/README.md](../02-non-fungible-tokens/wiki/README.md).  
> Tests: `yarn workspace @se-2/hardhat test test/YourCollectible.ts` or `cd packages/hardhat && yarn test test/YourCollectible.ts`.  
> Ignore branch `simple-nft-tut` below if you are only using this repository.

---

In this prac we'll go through the basic concepts of the ERC-721 standard. We'll use the ERC-721 smart contract implementation by the OpenZeppelin library.

# Simple NFT

The smart contract we are testing, YourCollectible.sol is a simple smart contract that implements the [ERC-721](https://github.com/ethereum/ercs/blob/master/ERCS/erc-721.md) standard by extending the ERC721 abstract smart contract by OpenZeppelin. It also extends the ERC721Enumerable and ERC721URIStorage.

The enumeration extension is OPTIONAL for ERC-721 smart contracts. This allows your contract to publish its full list of NFTs and make them discoverable. If implemented, a program can find the total supply and get all the NFTs using a for loop. For each user, it's also possible to iterate the tokens they owner using tokenOfOwnerByIndex function which gives the `index`th nft owned by the address passed to the function.

The metadata/storage extension is OPTIONAL for ERC-721 smart contracts. This allows your smart contract to be interrogated for its name and for details about the assets which your NFTs represent. OpenSea the market place for NFTs says:

> Providing asset metadata allows applications like OpenSea to pull in rich data for digital assets and easily display them in-app. Digital assets on a given smart contract are typically represented solely by a unique identifier (e.g., the tokenId in ERC721), so metadata allows these assets to have additional properties, such as a name, description, and image.

The tokenURI function in your ERC721 or the uri function in your ERC1155 contract should return an HTTP or IPFS URL. When queried, this URL should return a JSON blob of data with the metadata for your token [Source: OpenSea](https://docs.opensea.io/docs/metadata-standards).

## Practical

Use the branch `simple-nft-tut`:

```bash
git fetch upstream simple-nft-tut
git checkout --track origin/simple-nft-tut
```

1. Run the tests. They should fail.

```bash
yarn test test/YourCollectible.ts
```

2. We'll fix `mintItem` method. The functionality is tested in the Mocha test suite called `Mint Token`.

- `TODO: use _mint to create/mint an NFT`

> Note: The _mint function is from the ERC721 OpenZeppelin class

- `TODO: use _setTokenURI to set the metadata source for the NFT`

- `TODO: increament the tokenIdCounter`

3. Run the tests. The test case `Should not allow minting to contract address without implementing IERC721Receiver` will fail.

```bash
yarn test test/YourCollectible.ts
```

- The test fails because we used _mint instead of _safeMint. Safe Mint is used to check whether the account receiving the NFT can handle ERC721 tokens by calling onERC721Received. If it doesn't there is a risk that the NFT will be forever locked in the SM with no way of getting it out.

- `TODO: use _safeMint to create/mint an NFT`

- Deploy and run the tests again

```bash
yarn deploy
yarn test test/YourCollectible.ts
```

4. We'll write a test for the transfering of NFT's functionality. This is in the test case called 'Should allow transfer from non-owner user1 after approving them'.

- `TODO: write a test to check that user 1 cannot transfer the token they created for user 2`

> Note: The NFT with Id tokenId_0 currently belongs to user 2
> hint: connect to the SM using user1 and try transferring the NFT from user 2 to user 3.

- `TODO: call yourCollectible SM and have user 2 to approve/authorize user 1 to transfer the token on their behalf`

> Note: Approve gives permission to `to` to transfer `tokenId` token to another account. The approval is cleared when the token is transferred. Only a single account can be approved at a time, so approving the zero address clears previous approvals.

- `TODO: call yourCollectibe and have user 1 transfer tokenId_0 to user 3`

- `TODO: write a test to check that the owner of the token is currently user 3`

- `TODO: write a test to check that user 2 has no token that they own`

---

*Source: copied from the FinHubSA ethereum-class-workshop-2025 wiki (Simple NFT Example).*
