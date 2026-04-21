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

- [ ] **TODO:** Install [MetaMask](https://chromewebstore.google.com/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn) 
       _Security:_ Store seed phrases **offline** in a safe place; never commit them or share them.

<img width="2646" height="1546" alt="image" src="https://github.com/user-attachments/assets/548f1cb4-fb31-46c7-94ba-5829fbe3ad26" />


- [ ]  After installation, click on the metamask extension
- [ ]  Click on the burger menu icon on the top right and select 'Networks'
- [ ]  If there is a Sepolia account click on it
- [ ]  If there is no Sepolia, click 'Add network' at the bottom of the pop-up
- [ ]  Fill in the details of Sepolia like below

<div style="flex-direction: row;">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/215df1a7-fd82-48ed-911f-51de52601e4e" />
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/3e39c3a4-c2ad-45ad-8423-8094296575b1" />
</div>

- [ ]  To import an account, click on the top left where it says 'Imported Account 5'
- [ ]  Then click on 'Add Wallet' and then 'Import an Account'
- [ ]  Get you private key from the [blockchain concepts](https://blockchain-basics.vercel.app/blockchain-concepts/public-key-cryptography/key-generation.html) tutorial and paste it in the private key input.

<div style="flex-direction: row;">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/d4722ac9-5dbf-4674-928f-6264986de616" />
<img width="500" alt="image" src="https://github.com/user-attachments/assets/0dda265b-643a-4b3e-a6c0-2b120a51234a" />
</div>

- [ ] To get you account address, go to the accounts page
- [ ] Click on the vertical ellipsis of the account you want then click on addresses
- [ ] **TODO:** Fund the account with Sepolia ETH (e.g. [Sepolia PoW Faucet](https://sepolia-faucet.pk910.de/) or another trusted faucet).  
       _Note:_ Copy your account address from the wallet and paste it into the faucet.

<div style="flex-direction: row;">
<img width="500"  alt="image" src="https://github.com/user-attachments/assets/d4722ac9-5dbf-4674-928f-6264986de616" />
<img width="500" alt="image" src="https://github.com/user-attachments/assets/bc51f0b0-ac5d-46d2-83c8-81f8f8767e7f" />
</div>

### 2. Deploy to Sepolia

- [ ] **TODO:** Export or copy the **private key** for the funded test account (testnet only; never reuse mainnet keys).

- [ ] **TODO:** Run `yarn account:import` from `03-ui-non-fungible-token` and paste the key when prompted (follow any local password / keystore prompts your script uses).

- [ ] **TODO:** Deploy to Sepolia, for example:

  ```bash
  yarn deploy --network sepolia
  ```

  Ensure `hardhat.config.ts` defines `sepolia` and that you have a valid RPC URL in environment variables as required by this repo.
  A valid RPC URL can be found [here](https://chainlist.org/chain/11155111). At the date of writing `https://1rpc.io/sepolia` was a valide RPC URL.

---

## Reference

- Upstream wiki: [Simple UI Example](https://github.com/FinHubSA/ethereum-class-workshop-2025/wiki/Simple-UI-Example)
- Lesson guide: [README.md](./README.md)
