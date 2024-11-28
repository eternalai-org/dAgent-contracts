# Dagent Contracts

Welcome to the Dagent Contracts repository. This project houses the smart contracts for the Dagent platform, a decentralized AI network.

## Table of Contents

- [Dagent Contracts](#dagent-contracts)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Contracts Overview](#contracts-overview)
  - [Prerequisites](#prerequisites)
  - [Setup](#setup)
    - [1. Clone the Repository](#1-clone-the-repository)
    - [2. Configure Environment Variables](#2-configure-environment-variables)
    - [3. Install Dependencies](#3-install-dependencies)
    - [4. Compilation](#4-compilation)
    - [5. Deployment](#5-deployment)
      - [Deploy to a Specific Network](#deploy-to-a-specific-network)
      - [Example: Deploy to Arbitrum Mainnet](#example-deploy-to-arbitrum-mainnet)

## Overview

The Dagent platform utilizes decentralized smart contracts to establish a scalable and robust AI network on the blockchain. This repository contains all necessary smart contracts for deploying and interacting with the Dagent platform.

## Contracts Overview

- **SystemPromptManager**: Manages agents as ERC721 NFTs. Each agent has a system prompt and a mission, used to clarify context before forwarding user chat prompts to the HybridModel.
- **ModelCollection**: The collection of AI models. 
- **HybridModel**: Represents the AI model, receiving requests from SystemPromptManager or EOAs and forwarding them to the WorkerHub.
- **WorkerHub**: Processes chat prompts (inference) via the AI network maintained by Workers.
- **StakingHub**: Handles staking operations, requiring Workers to stake tokens before joining the AI network and servicing requests.

## Prerequisites

- Node.js and npm installed
- Hardhat installed (globally or via npx)
- Infura API Key for Arbitrum Mainnet
- Necessary private keys for deployment

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/eternalai-org/dagent-contracts.git
cd dagent-contracts
```

### 2. Configure Environment Variables
Copy the example environment file and fill in the required variables:

```bash
cp .env.example .env
```

Update the .env file with your details:

- ARBITRUM_MAINNET_INFURA_API_KEY: Your Infura API key

- ARBITRUM_MAINNET_PRIVATE_KEY: Private key of the deployer

- ARBITRUM_MAINNET_PRIVATE_KEY_WORKER_1: Private key of worker 1

- ARBITRUM_MAINNET_PRIVATE_KEY_WORKER_2: Private key of worker 2

- ARBITRUM_MAINNET_PRIVATE_KEY_WORKER_3: Private key of worker 3

- ARBITRUM_MAINNET_L2_OWNER_ADDRESS: Owner address of the L2 chain who will receive rewards for each inference

Note: Workers are entities responsible for maintaining the AI consensus.

### 3. Install Dependencies
```bash
npm install
```

### 4. Compilation
Compile the smart contracts using Hardhat:

```bash
npx hardhat compile
```

### 5. Deployment
#### Deploy to a Specific Network
Replace <YOUR_NETWORK> with the target network (e.g., arbitrum_mainnet):
```bash
npx hardhat run scripts/autoDeploy.ts --network <YOUR_NETWORK>
```
#### Example: Deploy to Arbitrum Mainnet

```bash
npx hardhat run scripts/autoDeploy.ts --network arbitrum_mainnet
```