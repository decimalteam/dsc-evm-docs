---
sidebar_position: 4
#position in left-hand side corner
---

# Blockchain testing project

## Using this Project

Clone repository from ``https://bitbucket.org/decimalteam/dsc-evm-tests/src/master/``

## Installing Node.js

### Linux

#### Ubuntu

Copy and paste these commands in a terminal:

```
sudo apt update
sudo apt install curl git
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt install nodejs
```

### MacOS

Make sure you have `git` installed. Otherwise, follow [these instructions](https://www.atlassian.com/git/tutorials/install-git).

There are multiple ways of installing Node.js on MacOS. We will be using [Node Version Manager (nvm)](http://github.com/creationix/nvm).

Copy and paste these commands in a terminal:

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.35.2/install.sh | bash
nvm install 12
nvm use 12
nvm alias default 12
npm install npm --global # Upgrade npm to the latest version
```

### Windows

Installing Node.js on Windows requires a few manual steps. We'll install git, Node.js 12.x and npm.

Download and run these:
1. [Git's installer for Windows](https://git-scm.com/download/win)
2. `node-v12.XX.XX-x64.msi` from [here](https://nodejs.org/dist/latest-v12.x)


## Upgrading your Node.js installation

If your version of Node.js is older than `12.0` follow the instructions below to upgrade.

### Linux

#### Ubuntu

1. Run `sudo apt remove nodejs` in a terminal to remove Node.js.
2. Find the version of Node.js that you want to install [here](https://github.com/nodesource/distributions#debinstall) and follow the instructions.
3. Run `sudo apt update && sudo apt install nodejs` in a terminal to install Node.js again.

### MacOS

You can change your Node.js version using [nvm](http://github.com/creationix/nvm). To upgrade to Node.js `12.x` run these in a terminal:

```
nvm install 12
nvm use 12
nvm alias default 12
npm install npm --global # Upgrade npm to the latest version
```

### Windows

You need to follow the [same installation instructions](#windows) as before but choose a different version. You can check the list of all available versions [here](https://nodejs.org/en/download/releases/).

## Installing yarn

For this tutorial we are going to use [yarn](yarnpkg.com)

To install it do the following:

```
npm install -g yarn
```

# Create .env file in the root of project using .env.example


```jsx title=".env"
ETH_NODE_URI_DECIMAL_TESTNET=http://185.242.122.118/web3/
ETH_NODE_URI_RINKEBY="Link to infura node, optional"
MNEMONIC_RINKEBY=<your mnemonic, optional>
MNEMONIC_DECIMAL_TESTNET=<your mnemonic>

//Can skip if do not needed
ETHERSCAN_API_KEY="etherscan api key, optional"

MNEMONIC_DECIMAL_TESTNET_FAUCET=<account which distribute coins, if you already have coins, skip this>
```

### Deploy contracts to live network
Deploy test contracts, they needed for next tests:
`yarn hardhat deploy  --network decimal_testnet`

### Send native to addresses
send native to addresses for paying transaction fee:
`yarn hardhat sendNativeToAddress  --network decimal_testnet`

### Run functionality tests:
This test will check basic functionality of evm, including: all types of transactions, test data types, function modifiers, test of memory and storage, test create2 opcode, all types of call, transfer of native currency, ecrecover and more.

`yarn hardhat run scripts/scenarious/checkFunctionality.ts --network decimal_testnet`

### Run ERC20 token scenario:

`yarn hardhat run scripts/scenarious/ERC20Transactions.ts --network decimal_testnet`

### Run ERC721 token scenario:

`yarn hardhat run scripts/scenarious/ERC721Transactions.ts --network decimal_testnet`

### Run ERC1155 token scenario:

`yarn hardhat run scripts/scenarious/ERC1155Transactions.ts --network decimal_testnet`
