# Scaffold-ETH

[Scaffold-Eth](https://scaffoldeth.io/) is a comprehensive development toolkit designed for building decentralized applications (dApps) on the Ethereum blockchain. It simplifies the developer’s workflow by streamlining both the backend and frontend processes. On the backend, ScaffoldEth makes it easier to create, deploy, and manage smart contracts, while on the frontend, it allows developers to efficiently build user interfaces that seamlessly interact with those smart contracts. The toolkit’s integrated features help reduce complexity, enabling rapid dApp development with minimal friction.

It offers several key features:

1. Contract Hot Reload: Automatically updates the frontend to reflect changes in your smart contract as you edit it.

2. Custom Hooks: A set of custom React hooks built around Wagmi, streamlining interactions with smart contracts. With TypeScript autocompletion, developers get helpful suggestions and error-checking during development, improving code reliability.

3. Web3 Components: A library of reusable, common Web3 components, allowing you to quickly build and integrate essential blockchain features into your frontend, accelerating the development process.

4. Burner Wallet & Local Faucet: Easily test your dApp with an in-browser burner wallet and a local faucet for sending small amounts of Ether.

5. Integration with Wallet Providers: Connect your application to different wallet providers, allowing interaction with the Ethereum network for real-world functionality.

Here are the main components of a development stack for building dApps with ScaffoldEth:

1. [Hardhat](https://hardhat.org/docs) or [Foundry](https://book.getfoundry.sh/): Developers can choose between these two tools for local network simulation, deploying smart contracts, and running tests.

2. [Wagmi](https://wagmi.sh/react/getting-started): Provides essential React hooks, making it easier to interact with the Ethereum network from a frontend.

3. [Viem](https://viem.sh/docs/getting-started.html): A low-level library offering Ethereum primitives, serving as an alternative to ethers.js or web3.js for interacting with Ethereum smart contracts.

4. [Next.js](https://nextjs.org/docs): A popular React framework that simplifies frontend development and offers useful pre-made hooks to build the UI.

5. [RainbowKit](https://www.rainbowkit.com/docs/introduction): Adds wallet connection functionality, allowing users to connect various Ethereum wallets to interact with the dApp.

6. [DaisyUI](https://daisyui.com/docs/install/): A UI component library based on [Tailwind CSS](https://tailwindui.com/components), providing a wide range of pre-built, customizable UI components for rapid frontend design.

This setup provides developers with all the necessary tools to efficiently build, test, and deploy Ethereum-based decentralized applications.

**This course** uses **Scaffold-ETH 2** ([docs](https://docs.scaffoldeth.io), [website](https://scaffoldeth.io)) inside each lesson folder.
