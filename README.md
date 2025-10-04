<details>
<summary><h2>📑 Table of Contents</h2></summary>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [🤔 What is SuperchainERC20?](#-what-is-superchainerc20)
  - [`IERC7802`](#ierc7802)
- [🚀 Getting Started](#-getting-started)
  - [1. Install prerequisites: `foundry`](#1-install-prerequisites-foundry)
  - [2. Clone and navigate to the repository:](#2-clone-and-navigate-to-the-repository)
  - [3. Install project dependencies using pnpm:](#3-install-project-dependencies-using-pnpm)
  - [4. Initialize .env files:](#4-initialize-env-files)
  - [5. Start the development environment:](#5-start-the-development-environment)
- [📦 Deploying SuperchainERC20s](#-deploying-superchainerc20s)
- [🧪 E2E Tests](#-e2e-tests)
- [🌉 Example: How to bridge a SuperchainERC20 token to another chain](#-example-how-to-bridge-a-superchainerc20-token-to-another-chain)
- [Updating an ERC20 contract to be interoperable](#updating-an-erc20-contract-to-be-interoperable)
- [🤝 Contributing](#-contributing)
- [⚖️ License](#-license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</details>

## ✨ Features

- Deploy interoperable ERC20 tokens across multiple L2 chains
- Cross-chain minting and burning via SuperchainERC20Bridge
- Deterministic deployment with Create2
- Easy local testing with Supersim
- Example scripts for bridging tokens between chains

---

## 🤔 What is SuperchainERC20?

`SuperchainERC20` is an implementation of [ERC-7802](https://ethereum-magicians.org/t/erc-7802-crosschain-token-interface/21508) designed to enable asset interoperability in the Superchain.
`SuperchainERC20` tokens are fungible across the Superchain by giving the `SuperchainERC20Bridge` permission to mint and burn the token during cross-chain transfers. For more information on SuperchainERC20 please visit the [docs](https://docs.optimism.io/stack/interop/superchain-erc20).

**Note**: ERC20 tokens that do not utilize the `SuperchainERC20Bridge` for cross-chain transfers can still achieve fungibility across the Superchain through interop message passing with a custom bridge solution. For these custom tokens, implementing [ERC-7802](https://ethereum-magicians.org/t/erc-7802-crosschain-token-interface/21508) is strongly recommended, as it unifies cross-chain mint and burn interfaces, enabling tokens to benefit from a standardized approach to cross-chain transfers.

### `IERC7802`

To achieve cross-chain functionality, the `SuperchainERC20` standard incorporates the `IERC7802` interface, defining essential functions and events:

- **`crosschainMint`**: Mints tokens on the destination chain as part of a cross-chain transfer.
- **`crosschainBurn`**: Burns tokens on the source chain to facilitate the transfer.
- **Events (`CrosschainMint` and `CrosschainBurn`)**: Emit when tokens are minted or burned, enabling transparent tracking of cross-chain transactions.
