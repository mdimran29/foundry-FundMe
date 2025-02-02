# 🔗 Foundry-FundMe 💸

[![GitHub Stars](https://img.shields.io/github/stars/mdimran29/foundry-FundMe?style=for-the-badge)](https://github.com/mdimran29/foundry-FundMe/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/mdimran29/foundry-FundMe?style=for-the-badge)](https://github.com/mdimran29/foundry-FundMe/network/members)
[![Solidity Version](https://img.shields.io/badge/Solidity-^0.8.20-informational?style=for-the-badge&logo=solidity)](https://soliditylang.org/)
[![Foundry Tests](https://img.shields.io/github/actions/workflow/status/mdimran29/foundry-FundMe/foundry.yml?label=Tests&style=for-the-badge)](https://github.com/mdimran29/foundry-FundMe/actions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

A decentralized crowdfunding platform built with Solidity and tested using Foundry. Allows users to fund projects with ETH while tracking USD equivalents through Chainlink price feeds.

![FundMe Demo](https://via.placeholder.com/800x400.png?text=FundMe+Contract+Demo) <!-- Replace with actual screenshot -->

## 🌟 Features

- Minimum USD contribution enforcement
- Real-time ETH/USD price conversion using Chainlink
- Secure fund withdrawal mechanism (owner-only)
- Comprehensive test coverage (>90%)
- Gas-efficient contract design
- Support for multiple blockchain networks
- Withdraw to multiple addresses functionality

## 🚀 Quick Start

### Prerequisites
- [Foundry](https://getfoundry.sh/)
- [Node.js](https://nodejs.org/) v18+
- [Git](https://git-scm.com/)

### Installation
```bash
git clone https://github.com/mdimran29/foundry-FundMe.git
cd foundry-FundMe
forge install
Environment Setup
Copy .env.example to .env

Add your environment variables:

env
Copy
SEPOLIA_RPC_URL=your_infura_or_alchemy_url
PRIVATE_KEY=your_metamask_private_key
ETHERSCAN_API_KEY=your_etherscan_api_key
📜 Usage
Compile Contracts
bash
Copy
forge build
Deploy to Sepolia Testnet
bash
Copy
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY -vvvv
Common Interactions
solidity
Copy
// Fund the contract (1 ETH minimum)
fundMe.fund{value: 1e18}();

// Withdraw funds (Owner only)
fundMe.withdraw();

// Get conversion rate
uint256 ethPrice = fundMe.getPrice();
🧪 Testing
Run all tests:

bash
Copy
forge test -vvv
Run specific test suite:

bash
Copy
forge test --match-contract FundMeTest
Generate coverage report:

bash
Copy
forge coverage --report lcov
📊 Project Structure
Copy
foundry-FundMe/
├── contracts/
│   └── FundMe.sol
├── test/
│   └── FundMe.t.sol
├── script/
│   └── DeployFundMe.s.sol
├── lib/
│   └── forge-std/
├── .env.example
└── foundry.toml
🤝 Contributing
Fork the repository

Create your feature branch: git checkout -b feature/your-feature

Commit changes: git commit -m 'Add some feature'

Push to branch: git push origin feature/your-feature

Open a Pull Request

⚠️ Security
This contract has NOT been audited. Use at your own risk. Key security features:

Owner-only withdrawal

Minimum contribution threshold

Price feed validation

Reentrancy guard protection

📄 License
MIT License - see LICENSE for details.

📬 Contact
Twitter: @YourTwitterHandle

Email: your.email@example.com

🙏 Acknowledgments
Foundry Team for amazing testing framework

Patrick Collins for inspiration

Chainlink for price feeds

OpenZeppelin for security patterns
