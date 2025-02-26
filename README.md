<div align="center">
  <img src="./docs/static/img/logo.png" alt="Logo" width="200">
  <h1>Smolitux Academy</h1>
  <p>A decentralized, blockchain-powered learning platform hosted by EcoSphereNetwork.</p>

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

---

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

---

## 🎯 About
**Smolitux Academy** is an open-source, blockchain-integrated **learning platform** that allows users to create, sell, and participate in online courses.  
It is **hosted by EcoSphereNetwork**, providing a **scalable, cloud-native infrastructure**, with **decentralized payments and NFT certificates**.

### **🔹 Why Smolitux Academy?**
- 🚀 **Fully Hosted by EcoSphereNetwork** – No need to manage your own servers.  
- 💰 **Blockchain-Powered Payments** – Courses can be monetized via **ESN_Token, ETH, MATIC, or Fiat**.  
- 🎓 **NFT Certificates** – Learners earn **blockchain-verified NFTs** as proof of course completion.  
- 🏆 **Tokenized Learning** – Users are rewarded for engagement and course completions.  
- 🔄 **Self-Hosting Option (Advanced Feature)** – For users who want to run a local version.

---

## ✨ Key Features

### 🔹 Core Features
- **Global Course Marketplace** – Users can create and sell courses on a decentralized platform.
- **Blockchain Payments** – Secure and instant transactions using **Smart Contracts**.
- **NFT Certificates** – Immutable, verifiable proof of learning on the blockchain.
- **Reward System** – Earn **ESN_Token** for learning and engagement.
- **Scalable & Secure** – Hosted in the **cloud with Kubernetes & Docker**.

### 🔹 Optional Self-Hosting Features
- **Docker Deployment** – Run Smolitux Academy on your own server or Raspberry Pi.
- **Offline Mode (MoodleBox-style)** – Local hosting with sync when online.
- **Custom Smart Contracts** – Integrate your own blockchain logic.

---

## 🚀 Getting Started

### **Accessing the Hosted Version**
The **official Smolitux Academy instance is hosted by EcoSphereNetwork** and can be accessed at:  
🌎 **[https://academy.ecospherelabs.com](https://academy.ecospherelabs.com)**  

**Sign Up Today** and start creating or joining courses!

---

### **Self-Hosting (Advanced Users)**
🔹 **For those who want to host their own Smolitux Academy instance**, follow these steps:

### **Prerequisites**
- Docker & Docker-Compose  
- Node.js & npm  
- PostgreSQL (for local DB)  
- MetaMask or WalletConnect (for Web3 payments)  

### **Installation**
1. **Clone the repository**
   ```bash
   git clone https://github.com/EcoSphereNetwork/Smolitux-Academy.git
   cd Smolitux-Academy
   ```
2. **Start local instance**
   ```bash
   docker-compose up -d
   ```
3. **Set up Smart Contracts (Optional)**
   ```bash
   cd blockchain
   npm install
   npx hardhat compile
   npx hardhat run scripts/deploy.js --network goerli
   ```

---

## 📁 Project Structure
```
Smolitux-Academy/
├── blockchain/              # Smart Contracts (Solidity)
│   ├── contracts/           # Solidity contracts for payments & NFTs
│   ├── scripts/             # Deployment & interaction scripts
│   ├── test/                # Smart contract test cases
├── frontend/                # Web UI (React.js)
│   ├── src/
│   ├── public/
│   ├── package.json
├── backend/                 # Node.js API for Moodle & Blockchain
│   ├── src/
│   ├── routes/
│   ├── database/
├── docs/                    # Documentation
├── tests/                   # End-to-end testing
├── docker-compose.yml       # Deployment configuration
├── .env.example             # Environment variables
└── README.md                # Project documentation
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

### **How EcoSphereNetwork Hosts Smolitux Academy**
1. **Cloud Kubernetes Cluster (AWS EKS / GCP GKE)**
2. **CI/CD Pipeline with GitHub Actions**
3. **Database & Storage: PostgreSQL (AWS RDS) + S3/IPFS**
4. **Load Balancing & Scaling with Nginx & Cloudflare**

### **Self-Hosting Deployment**
1. Install Docker & Kubernetes  
2. Clone the repository & configure `.env`  
3. Deploy with `docker-compose up -d` or `kubectl apply -f k8s/`

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
