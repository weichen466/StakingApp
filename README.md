# Decentralized Staking App

A decentralized staking application, allowing users to stake ETH with a 72-hour deadline and 1 ETH threshold mechanism.

## Overview

This project implements a staking mechanism where:

- Users can stake ETH into the contract
- There's a 72-hour deadline from contract deployment
- If 1 ETH threshold is reached before deadline, funds are sent to an external contract
- If threshold is not met, users can withdraw their stakes after the deadline

## Tech Stack

- **Smart Contracts**: Solidity 0.8.20 with Hardhat
- **Frontend**: Next.js with TypeScript
- **Web3 Integration**: wagmi, viem
- **Styling**: Tailwind CSS
- **Package Manager**: Yarn (v3.2.3)

## Project Structure

```
packages/
├── hardhat/          # Smart contracts and deployment
│   ├── contracts/    # Solidity contracts
│   ├── deploy/       # Deployment scripts
│   ├── test/         # Contract tests
│   └── scripts/      # Utility scripts
└── nextjs/           # Frontend application
    ├── app/          # Next.js app directory
    ├── components/   # React components
    ├── hooks/        # Custom hooks
    └── utils/        # Utility functions
```

## Smart Contracts

### Staker.sol

Main staking contract with features:

- **Stake**: Users can stake ETH (minimum any amount)
- **Execute**: Anyone can execute after deadline to either complete or enable withdrawals
- **Withdraw**: Users can withdraw if threshold wasn't met
- **Time Left**: View function to check remaining time

**Key Parameters:**

- Threshold: 1 ETH
- Deadline: 72 hours from deployment

### ExampleExternalContract.sol

Simple contract that receives funds when staking threshold is met.

## Getting Started

### Prerequisites

- Node.js >=20.18.3
- Yarn package manager

### Installation

1. Clone the repository

```bash
git clone <repository-url>
cd challenge-decentralized-staking
```

2. Install dependencies

```bash
yarn install
```

3. Start the local blockchain

```bash
yarn chain
```

4. Deploy contracts (in new terminal)

```bash
yarn deploy
```

5. Start the frontend

```bash
yarn start
```

## Available Scripts

### Main Commands

- `yarn start` - Start the frontend development server
- `yarn chain` - Start local Hardhat blockchain
- `yarn deploy` - Deploy contracts to local network
- `yarn test` - Run contract tests

### Development Commands

- `yarn compile` - Compile smart contracts
- `yarn format` - Format code (both frontend and contracts)
- `yarn lint` - Run linting
- `yarn verify` - Verify contracts on block explorer

### Account Management

- `yarn account` - List account information
- `yarn account:generate` - Generate new account
- `yarn account:import` - Import existing account
- `yarn account:reveal-pk` - Reveal private key

## Usage

1. **Connect Wallet**: Connect your MetaMask or other Web3 wallet
2. **Stake ETH**: Enter amount and click stake button
3. **Monitor Progress**: Watch the staking progress and time remaining
4. **Execute**: Anyone can execute the contract after deadline
5. **Withdraw**: If threshold not met, withdraw your stake

## Testing

Run the test suite:

```bash
yarn test
```

Tests cover:

- Staking functionality
- Withdrawal mechanisms
- Threshold validation
- Time-based execution

## Deployment

### Local Deployment

```bash
yarn chain  # Terminal 1
yarn deploy # Terminal 2
```

### Testnet Deployment

1. Set up environment variables in `packages/hardhat/.env`
2. Configure network in `hardhat.config.ts`
3. Deploy with: `yarn hardhat:deploy --network sepolia`

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Learn More

- [Hardhat Documentation](https://hardhat.org/docs)
- [Next.js Documentation](https://nextjs.org/docs)
- [Ethereum Development Guide](https://ethereum.org/en/developers/)
