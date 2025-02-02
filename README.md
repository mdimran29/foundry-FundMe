Foundry Fund Me
This is a section of the Cyfrin Solidity Course.

⭐️ Updraft | Foundry Fund Me

Foundry Fund Me
Getting Started
Requirements
Quickstart
Optional Gitpod
Usage
Deploy
Testing
Test Coverage
Local zkSync
(Additional) Requirements
Setup local zkSync node
Deploy to local zkSync node
Deployment to a testnet or mainnet
Scripts
Withdraw
Estimate gas
Formatting
Additional Info:
Let's talk about what "Official" means
Summary
Thank you!
Getting Started
Requirements
git
You'll know you did it right if you can run git --version and you see a response like git version x.x.x
foundry
You'll know you did it right if you can run forge --version and you see a response like forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)
Quickstart
git clone https://github.com/Cyfrin/foundry-fund-me-cu
cd foundry-fund-me-cu
make
Optional Gitpod
If you can't or don't want to run and install locally, you can work with this repo in Gitpod. If you do this, you can skip the clone this repo part.

Open in Gitpod

Usage
Deploy
forge script script/DeployFundMe.s.sol
Testing
We talk about 4 test tiers in the video.

Unit
Integration
Forked
Staging
This repo we cover #1 and #3.

forge test
or

// Only run test functions matching the specified regex pattern.

```"forge test -m testFunctionName" is deprecated. Please use ```

```forge test --match-test testFunctionName```
or

```forge test --fork-url $SEPOLIA_RPC_URL```
```Test Coverage```
```forge coverage```
Local zkSync
The instructions here will allow you to work with this repo on zkSync.

(Additional) Requirements
In addition to the requirements above, you'll need:

foundry-zksync
You'll know you did it right if you can run forge --version and you see a response like forge 0.0.2 (816e00b 2023-03-16T00:05:26.396218Z).
npx & npm
You'll know you did it right if you can run npm --version and you see a response like 7.24.0 and npx --version and you see a response like 8.1.0.
docker
You'll know you did it right if you can run docker --version and you see a response like Docker version 20.10.7, build f0df350.
Then, you'll want the daemon running, you'll know it's running if you can run docker --info and in the output you'll see something like the following to know it's running:
Client:
 Context:    default
 Debug Mode: false
Setup local zkSync node
Run the following:

npx zksync-cli dev config
And select: In memory node and do not select any additional modules.

Then run:

npx zksync-cli dev start
And you'll get an output like:

In memory node started v0.1.0-alpha.22:
 - zkSync Node (L2):
  - Chain ID: 260
  - RPC URL: http://127.0.0.1:8011
  - Rich accounts: https://era.zksync.io/docs/tools/testing/era-test-node.html#use-pre-configured-rich-wallets
Deploy to local zkSync node
make deploy-zk
This will deploy a mock price feed and a fund me contract to the zkSync node.

Deployment to a testnet or mainnet
Setup environment variables
You'll want to set your SEPOLIA_RPC_URL and PRIVATE_KEY as environment variables. You can add them to a .env file, similar to what you see in .env.example.

PRIVATE_KEY: The private key of your account (like from metamask). NOTE: FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
You can learn how to export it here.
SEPOLIA_RPC_URL: This is url of the sepolia testnet node you're working with. You can get setup with one for free from Alchemy
Optionally, add your ETHERSCAN_API_KEY if you want to verify your contract on Etherscan.

Get testnet ETH
Head over to faucets.chain.link and get some testnet ETH. You should see the ETH show up in your metamask.

Deploy
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
Scripts
After deploying to a testnet or local net, you can run the scripts.

Using cast deployed locally example:

cast send <FUNDME_CONTRACT_ADDRESS> "fund()" --value 0.1ether --private-key <PRIVATE_KEY>
or

forge script script/Interactions.s.sol:FundFundMe --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
forge script script/Interactions.s.sol:WithdrawFundMe --rpc-url sepolia  --private-key $PRIVATE_KEY  --broadcast
Withdraw
cast send <FUNDME_CONTRACT_ADDRESS> "withdraw()"  --private-key <PRIVATE_KEY>
Estimate gas
You can estimate how much gas things cost by running:

forge snapshot
And you'll see an output file called .gas-snapshot

Formatting
To run code formatting:

forge fmt
Additional Info:
Some users were having a confusion that whether Chainlink-brownie-contracts is an official Chainlink repository or not. Here is the info. Chainlink-brownie-contracts is an official repo. The repository is owned and maintained by the chainlink team for this very purpose, and gets releases from the proper chainlink release process. You can see it's still the smartcontractkit org as well.

https://github.com/smartcontractkit/chainlink-brownie-contracts

Let's talk about what "Official" means
The "official" release process is that chainlink deploys it's packages to npm. So technically, even downloading directly from smartcontractkit/chainlink is wrong, because it could be using unreleased code.

So, then you have two options:

Download from NPM and have your codebase have dependencies foreign to foundry
Download from the chainlink-brownie-contracts repo which already downloads from npm and then packages it nicely for you to use in foundry.
Summary
That is an official repo maintained by the same org
It downloads from the official release cycle chainlink/contracts use (npm) and packages it nicely for digestion from foundry.
Thank you!
If you appreciated this, feel free to follow me or donate!

ETH/Arbitrum/Optimism/Polygon/etc Address: 0x9680201d9c93d65a3603d2088d125e955c73BD65