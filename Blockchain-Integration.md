## **🔹 Technischer Plan für die Blockchain-Integration in Smolitux Academy**
Da Smolitux Academy eine Kombination aus **LMS (Learning Management System) und Blockchain** ist, müssen Smart Contracts, Token-Zahlungen und NFT-Zertifikate sicher in die Plattform integriert werden. Hier ist ein **detaillierter technischer Plan** für diese Integration.

---

## **1️⃣ Architekturübersicht der Blockchain-Integration**
Die Blockchain-Integration in Smolitux Academy besteht aus drei Hauptkomponenten:
1. **Smart Contracts für Kurszahlungen** (Transaktionen & Gebühren)
2. **NFT-Zertifikate für abgeschlossene Kurse** (fälschungssicher)
3. **Tokenized Learning & Belohnungssystem** (ESN_Token oder andere Kryptowährungen)

**Technologie-Stack für Blockchain-Integration:**
- **Blockchain**: Ethereum / Polygon / ESN_Token
- **Smart Contracts**: Solidity (ERC-20 für Token, ERC-721 für NFTs)
- **Web3-Integration**: Web3.js / ethers.js für Interaktion mit Wallets (MetaMask, WalletConnect)
- **Datenbank**: PostgreSQL / MongoDB für Nicht-Blockchain-Daten
- **Backend**: Node.js (Express) oder Python (FastAPI) für API-Anbindung
- **Frontend**: React.js / Vue.js für UI und Wallet-Integration

---

## **2️⃣ Smart Contract-Architektur**
### **🔷 A) Kurszahlung mit Smart Contracts**
💰 **Ziel**: Dezentrale Bezahlung für Kurse mit **ESN_Token oder anderen Kryptowährungen**.

**👨‍💻 Smart Contract Logik (Solidity)**
- Jeder Kursanbieter registriert seinen Kurs mit:
  - **Preis (z. B. 50 ESN_Token)**
  - **Wallet-Adresse des Anbieters**
  - **Kurs-ID**
- Wenn ein Nutzer den Kurs kauft:
  - Der Smart Contract **überträgt den Betrag** an den Anbieter.
  - Der Käufer erhält in der Datenbank Zugriff auf den Kurs.
  - Die Transaktion wird in der Blockchain gespeichert.

```solidity
// Kurszahlung Smart Contract (Solidity)
pragma solidity ^0.8.0;

contract SmolituxCoursePayment {
    address public owner;
    mapping(uint256 => address) public courseOwners; // Kurs-ID → Anbieter-Adresse
    mapping(uint256 => uint256) public coursePrices; // Kurs-ID → Preis

    constructor() {
        owner = msg.sender;
    }

    function registerCourse(uint256 courseId, uint256 price) public {
        require(courseOwners[courseId] == address(0), "Kurs existiert bereits!");
        courseOwners[courseId] = msg.sender;
        coursePrices[courseId] = price;
    }

    function buyCourse(uint256 courseId) public payable {
        require(courseOwners[courseId] != address(0), "Kurs nicht gefunden!");
        require(msg.value >= coursePrices[courseId], "Nicht genug Tokens!");

        address payable seller = payable(courseOwners[courseId]);
        seller.transfer(msg.value);
    }
}
```

**📌 Anforderungen:**
✅ **ESN_Token als Zahlungsmittel integrieren (ERC-20)**  
✅ **Automatische Kursfreigabe nach erfolgreicher Zahlung**  
✅ **Web3-Wallets unterstützen (MetaMask, WalletConnect)**  

---

### **🔷 B) NFT-Zertifikate für abgeschlossene Kurse**
📜 **Ziel**: Jeder, der einen Kurs erfolgreich abschließt, bekommt ein NFT als **fälschungssicheres Zertifikat**.

**👨‍💻 Smart Contract Logik (Solidity)**
- Kursanbieter kann definieren, dass ein Kurs ein NFT-Zertifikat ausstellt.
- Teilnehmer erhalten nach Abschluss ein NFT mit:
  - **Kursname**
  - **Teilnehmer-Name (Wallet-Adresse)**
  - **Kursabschluss-Datum**

```solidity
// NFT-Zertifikat Smart Contract
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract SmolituxCertificate is ERC721 {
    uint256 private _tokenId;
    mapping(uint256 => string) public courseNames;

    constructor() ERC721("SmolituxCertificate", "SMOLI_CERT") {}

    function issueCertificate(address recipient, string memory courseName) public {
        _tokenId++;
        _mint(recipient, _tokenId);
        courseNames[_tokenId] = courseName;
    }
}
```

**📌 Anforderungen:**
✅ **NFTs als Zertifikate ausstellen (ERC-721)**  
✅ **Direkt im Wallet des Nutzers speicherbar**  
✅ **Öffentlich verifizierbar über Blockchain-Explorer**  

---

### **🔷 C) Tokenized Learning & Belohnungssystem**
🎁 **Ziel**: Nutzer erhalten **ESN_Token als Belohnung**, wenn sie:
- Kurse abschließen
- Tests bestehen
- Aktiv in Foren & Diskussionen sind

**👨‍💻 Smart Contract Logik (Solidity)**
```solidity
// Belohnungssystem für abgeschlossene Kurse
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/IERC20.sol";

contract SmolituxReward {
    IERC20 public token;
    address public admin;

    constructor(IERC20 _token) {
        token = _token;
        admin = msg.sender;
    }

    function rewardUser(address user, uint256 amount) public {
        require(msg.sender == admin, "Nur Admin kann Belohnungen senden");
        token.transfer(user, amount);
    }
}
```

**📌 Anforderungen:**
✅ **ESN_Token-Belohnungen für Lernaktivitäten**  
✅ **Anbindung an Kurs-APIs für automatische Auszahlung**  

---

## **3️⃣ Web3-Integration für Frontend**
💡 **Ziel**: Nutzer sollen direkt über ihr Wallet bezahlen, Zertifikate abrufen & Belohnungen erhalten.

**📌 Technologien:**
- **ethers.js / web3.js** für Smart Contract-Interaktion
- **MetaMask & WalletConnect** für Nutzer-Login

**👨‍💻 Beispiel für Web3-Integration (JavaScript)**
```javascript
async function buyCourse(courseId, price) {
    const provider = new ethers.providers.Web3Provider(window.ethereum);
    const signer = provider.getSigner();
    const contract = new ethers.Contract(contractAddress, contractABI, signer);

    const tx = await contract.buyCourse(courseId, { value: price });
    await tx.wait();

    alert("Kurs gekauft!");
}
```

**📌 Anforderungen:**
✅ **Kurskauf über MetaMask/Web3**  
✅ **NFTs in Wallet anzeigen**  
✅ **Transaktionen über Blockchain nachverfolgbar**  

---

## **4️⃣ Datenbank & Backend-Anpassungen**
💡 **Ziel**: Moodle muss angepasst werden, um Blockchain-Transaktionen zu speichern.

**📌 Neue Datenbank-Tabellen in PostgreSQL:**
| Tabelle | Spalten |
|---|---|
| `blockchain_transactions` | `tx_id`, `user_id`, `course_id`, `amount`, `timestamp` |
| `nft_certificates` | `user_id`, `course_id`, `nft_token_id`, `issued_at` |

**📌 API-Erweiterungen (Node.js oder FastAPI):**
- `/buy-course`: Smart Contract Transaktion auslösen
- `/get-certificates`: NFT-Daten abrufen
- `/get-rewards`: Token-Belohnungen anzeigen

---

## **🚀 Nächste Schritte & Umsetzung**
✅ **Smart Contracts finalisieren & auf Testnetz deployen (Goerli / Mumbai Testnet)**  
✅ **Web3-Integration in Moodle-Frontend starten**  
✅ **API-Backend für Blockchain-Transaktionen entwickeln**  
