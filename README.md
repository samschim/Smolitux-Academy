<div align="center">
  <img src="./docs/static/img/logo.png" alt="Logo" width="200">
  <h1>Smolitux Academy</h1>
  <p>A decentralized learning platform combining the best of Moodle and Udemy with Blockchain integration.</p>

  [![Contributors][contributors-shield]][contributors-url]
  [![Stars][stars-shield]][stars-url]
  [![Coverage][coverage-shield]][coverage-url]
  [![MIT License][license-shield]][license-url]
  <br/>
  [![Discord][discord-shield]][discord-url]
  [![Documentation][docs-shield]][docs-url]
  [![Project Credits][credits-shield]][credits-url]

  [Start Documentation](https://github.com/EcoSphereNetwork/Smolitux-Academy/blob/main/docs/README.md) •
  [Report Bug](https://github.com/EcoSphereNetwork/Smolitux-Academy/issues) •
  [Request Feature](https://github.com/EcoSphereNetwork/Smolitux-Academy/issues)
</div>

## 📋 Table of Contents
- [About](#-about)
- [Key Features](#-key-features)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Development](#-development)
- [Testing](#-testing)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [Support](#-support)
- [License](#-license)

## 🎯 About
**Smolitux Academy** is an open-source, decentralized e-learning platform built on **Moodle** with **Blockchain integration**. It allows anyone to create and sell courses, offering a **self-hosted** or **cloud-based** deployment.

### Why Use Smolitux Academy?
- 🚀 **Decentralized Learning**: No central authority—run it on your own hardware or cloud.  
- 💰 **Blockchain Monetization**: Course creators can charge in **ESN_Token** or offer free content.  
- 🎓 **NFT Certificates**: Learners earn blockchain-verified certificates as **NFTs**.  
- 🏆 **Tokenized Learning**: Reward users for completing courses & engaging in the community.  
- 🔄 **Flexible Deployment**: Host locally (MoodleBox/Raspberry Pi) or scale in the cloud.  

---

## ✨ Key Features

### 🔹 Core Features
- **Decentralized Course Marketplace** – Anyone can create & sell courses.
- **Flexible Pricing** – Free or paid courses using **Smart Contracts**.
- **NFT-Based Certificates** – Fälschungssichere Abschlussnachweise.
- **Tokenized Learning** – Earn rewards for completing courses.
- **Decentralized Storage** – Course content can be stored on **IPFS**.

### 🔹 Development Tools
- **Smart Contracts** – Solidity-based ERC-20 (payments) & ERC-721 (certificates).
- **Web3 Integration** – Wallet authentication via MetaMask / WalletConnect.
- **Docker Support** – Fully containerized for flexible deployment.
- **Testing Framework** – Unit & integration tests for blockchain transactions.

---

## 🚀 Getting Started

### **Prerequisites**
- Docker & Docker-Compose  
- Node.js & npm  
- PostgreSQL or SQLite (for local deployment)  
- MetaMask or WalletConnect (for blockchain transactions)  

### **Installation**
1. **Clone the repository**
   ```bash
   git clone https://github.com/EcoSphereNetwork/Smolitux-Academy.git
   cd Smolitux-Academy
   ```
2. **Start local development environment**
   ```bash
   docker-compose up -d
   ```
3. **Set up Smart Contracts**
   ```bash
   cd blockchain
   npm install
   npx hardhat compile
   ```
4. **Deploy Smart Contracts to testnet**
   ```bash
   npx hardhat run scripts/deploy.js --network goerli
   ```

---

## 📁 Project Structure
```
Smolitux-Academy/
├── blockchain/              # Smart Contracts (Solidity)
│   ├── contracts/           # Solidity contracts for payments & NFTs
│   ├── scripts/             # Deployment & interaction scripts
│   ├── test/                # Test cases for blockchain logic
├── docs/                    # Documentation
├── frontend/                # Web UI (React.js)
│   ├── src/
│   ├── public/
│   ├── package.json
├── backend/                 # Node.js API for Moodle & Blockchain
│   ├── src/
│   ├── routes/
│   ├── database/
├── tests/                   # End-to-end testing
├── docker-compose.yml       # Deployment configuration
├── .env.example             # Environment variables
└── README.md                # Project documentation
```

---

## 💻 Development

### **Setting Up for Development**
1. Install dependencies:
   ```bash
   npm install
   ```
2. Compile Smart Contracts:
   ```bash
   npx hardhat compile
   ```
3. Run local blockchain (for testing)
   ```bash
   npx hardhat node
   ```
4. Start development server:
   ```bash
   cd frontend
   npm start
   ```

---

## 🧪 Testing

### **Running Tests**
```bash
# Run Smart Contract tests
npx hardhat test

# Run API & Frontend tests
npm test
```

### **Smart Contract Coverage**
```bash
npx hardhat coverage
```

---

## 🚢 Deployment

### **Deploy to Production**
1. **Set up a production server (Ubuntu/Debian)**
   ```bash
   sudo apt update && sudo apt install docker docker-compose -y
   ```
2. **Clone repository**
   ```bash
   git clone https://github.com/EcoSphereNetwork/Smolitux-Academy.git
   cd Smolitux-Academy
   ```
3. **Run Docker Compose**
   ```bash
   docker-compose up -d
   ```

---

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create your feature branch:
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. Commit your changes:
   ```bash
   git commit -m 'feat: add amazing feature'
   ```
4. Push to the branch:
   ```bash
   git push origin feature/amazing-feature
   ```
5. Open a Pull Request

---

## 💬 Support

- [Issue Tracker](https://github.com/EcoSphereNetwork/Smolitux-Academy/issues)
- [Discussions](https://github.com/EcoSphereNetwork/Smolitux-Academy/discussions)
- [Discord Community][discord-url]
- [Documentation][docs-url]

---

## 📄 License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

---

<div align="center">

### Repository Activity

[![Repository Activity][activity-graph]][activity-url]

</div>

<!-- MARKDOWN LINKS & IMAGES -->
[contributors-shield]: https://img.shields.io/github/contributors/EcoSphereNetwork/Smolitux-Academy?style=for-the-badge&color=blue
[contributors-url]: https://github.com/EcoSphereNetwork/Smolitux-Academy/graphs/contributors
[stars-shield]: https://img.shields.io/github/stars/EcoSphereNetwork/Smolitux-Academy?style=for-the-badge&color=blue
[stars-url]: https://github.com/EcoSphereNetwork/Smolitux-Academy/stargazers
[coverage-shield]: https://img.shields.io/codecov/c/github/EcoSphereNetwork/Smolitux-Academy?style=for-the-badge&color=blue
[coverage-url]: https://codecov.io/github/EcoSphereNetwork/Smolitux-Academy
[license-shield]: https://img.shields.io/github/license/EcoSphereNetwork/Smolitux-Academy?style=for-the-badge&color=blue
[license-url]: https://github.com/EcoSphereNetwork/Smolitux-Academy/blob/main/LICENSE
[discord-shield]: https://img.shields.io/badge/Discord-Join%20Us-purple?logo=discord&logoColor=white&style=for-the-badge
[discord-url]: https://discord.gg/cTWBHGkn
[docs-shield]: https://img.shields.io/badge/Documentation-000?logo=googledocs&logoColor=FFE165&style=for-the-badge
[docs-url]: https://github.com/EcoSphereNetwork/Smolitux-Academy/wiki
[activity-graph]: https://repobeats.axiom.co/api/embed/8d1a53c73cf5523d0e52a6cc5b74bce75eecc801.svg
[activity-url]: https://repobeats.axiom.co
