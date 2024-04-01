# Deploying the NTD Contracts

## Prerequisites
Node.js and npm installed

Hardhat environment set up

Deployment account with ETH

## Steps
Clone the repository and install dependencies

git clone [repo](https://github.com/neuraltensordynamics/ntd-smart-contracts, "NTD Contracts")
cd ntd-smart-contracts

npm install



## Set environment variables
Copy .env.example to .env and fill in the values:

ETHERSCAN_API_KEY=

INFURA_API_KEY=

SEPOLIA_PRIVATE_KEY=



## Compile the contracts
npx hardhat compile



## Deploy the contracts
Run npx hardhat run --network sepolia migrations/deploy.js

This will deploy the NtdTAO contract.

Initialize the NtdTAO contract

Call the initialize function on the deployed NtdTAO contract, passing in:

owner - The address that will have admin permissions
supply - The total staking token supply to mint, specified in wei
For example:

`await staking.initialize(ownerAddress, 100000000)`



## Additional setup

After initializing, call the following functions to finish setting up:

- setWtao - Pass in the wTAO token address
- grantRole(MANAGE_STAKING_CONFIG_ROLE, ownerAddress) - Grant admin role
- setMaxDepositPerRequest
- setNativeTokenReceiver
- setProtocolVault
- setMinStackingAmount
- setMaxStackingAmount
- setUpperExchangeRate
- setLowerExchangeRate
- setExchangeRate


## Verify on Etherscan
Run npx hardhat verify --network sepolia <contractAddress> to verify the source code.

The deployment is now complete!