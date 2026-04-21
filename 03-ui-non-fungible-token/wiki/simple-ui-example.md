# Simple UI Example — key points & TODOs

This page adapts the [Simple UI Example](https://github.com/FinHubSA/ethereum-class-workshop-2025/wiki/Simple-UI-Example) wiki for this monorepo. Work under `03-ui-non-fungible-token/`.

**Scaffold-ETH hooks:** [docs.scaffoldeth.io — Hooks](https://docs.scaffoldeth.io/hooks/).

## What this lesson adds

You build practical knowledge of deploying the NFT app to Sepolia and interacting with it through the UI using a connected wallet.

---

## Practical — checklist

### 1. Point the app at Sepolia (testnet)

- [ ] **TODO:** In `packages/nextjs/scaffold.config.ts`, switch from **`chains.hardhat`** to **`chains.sepolia`** (or the equivalent target network your template exports).  
       _Note:_ This file defines which networks the frontend targets by default.

- [ ] **TODO:** Install [MetaMask](https://chromewebstore.google.com/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn) (or another compatible wallet).  
       _Security:_ Store seed phrases **offline** in a safe place; never commit them or share them.

- [ ] **TODO:** In MetaMask, connect to **Sepolia** and create or select an account.

- [ ] **TODO:** Fund the account with Sepolia ETH (e.g. [Google Cloud Sepolia faucet](https://cloud.google.com/application/web3/faucet/ethereum/sepolia) or another trusted faucet).  
       _Note:_ Copy your account address from the wallet and paste it into the faucet.

### 2. Deploy to Sepolia

- [ ] **TODO:** Export or copy the **private key** for the funded test account (testnet only; never reuse mainnet keys).

- [ ] **TODO:** Run `yarn account:import` from `03-ui-non-fungible-token` and paste the key when prompted (follow any local password / keystore prompts your script uses).

- [ ] **TODO:** Deploy to Sepolia, for example:

  ```bash
  yarn deploy --network sepolia
  ```

  Ensure `hardhat.config.ts` defines `sepolia` and that you have a valid RPC URL / API key in environment variables as required by this repo.

---

## Reference

- Upstream wiki: [Simple UI Example](https://github.com/FinHubSA/ethereum-class-workshop-2025/wiki/Simple-UI-Example)
- Lesson guide: [README.md](./README.md)
