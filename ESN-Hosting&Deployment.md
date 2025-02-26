# **🌍 Smolitux Academy – Hosting & Deployment durch EcoSphereNetwork**

**Smolitux Academy** wird **zentral von EcoSphereNetwork** gehostet, um eine **skalierbare, sichere und hochverfügbare Lernplattform** bereitzustellen.  
Nutzer können sich einfach registrieren und sofort mit dem Lernen oder Erstellen von Kursen beginnen.  

🛠 **Self-Hosting ist eine optionale Zusatzfunktion** für spezielle Anwendungsfälle wie Offline-Lernen oder private Instanzen.  
Der **reguläre Zugang erfolgt über die zentrale Plattform** von EcoSphereNetwork.  

🔗 **Zugriff auf die offizielle Plattform:**  
🌎 **[https://academy.ecospherelabs.com](https://academy.ecospherelabs.com)**  

---

## **📌 Hosting-Strategie von EcoSphereNetwork**

### **🔹 1. Hauptplattform – Hosting auf eigenen Servern**
✅ **EcoSphereNetwork hostet die Plattform auf eigenen Servern**  
✅ **Kein Einsatz von externen Cloud-Diensten (z. B. AWS, Google Cloud)**  
✅ **Hohe Sicherheit durch eigene Infrastruktur & dezentrale Speicherung**  
✅ **Automatische Updates, Wartung & Skalierung durch das Team**  

📌 **Technologie-Stack für das zentrale Hosting:**  

| **Komponente**        | **Technologie**                                         | **Beschreibung** |
|----------------------|---------------------------------------------------------|-----------------|
| **Frontend**        | React.js / Vue.js                                       | Moderne, responsive Web-UI für Kursverwaltung und Nutzer-Interaktion |
| **Backend**         | Node.js (Express) / FastAPI (Python)                    | REST & Web3 API für Kursmanagement, Zahlungen und Nutzerverwaltung |
| **Datenbank**       | PostgreSQL (gehostet auf eigenen Servern)               | Speicherung von Nutzerdaten, Kursinformationen und Transaktionen |
| **Dateispeicherung**| **Interne Server + IPFS (optional)**                     | Speicherung von Kursinhalten, Dokumenten und Videos |
| **Blockchain**      | Ethereum / Polygon / ESN_Token                          | Smart Contracts für Zahlungen & NFT-Zertifikate |
| **Containerisierung** | Docker                                                 | Modulare Bereitstellung aller Dienste für einfache Skalierung |
| **Orchestrierung**  | Kubernetes (auf eigenen Servern)                        | Automatische Skalierung, Lastverteilung und Serviceverwaltung |
| **Load Balancer**   | Nginx + eigener Proxy-Server                            | Verteilung des Traffics auf mehrere Server für hohe Verfügbarkeit |
| **Authentifizierung** | OAuth 2.0 (Google, MetaMask, WalletConnect)           | Sichere Anmeldung über klassische Logins oder Web3-Wallets |

📌 **Dieser Stack ermöglicht eine **skalierbare, sichere und performante** Architektur, die vollständig auf den eigenen Servern von EcoSphereNetwork gehostet wird.** 🚀

📌 **Ziel:**  
- **Unabhängigkeit von großen Cloud-Anbietern**  
- **Eigene Kontrolle über Sicherheit, Skalierung & Datenschutz**  

---

### **🔹 2. Optionales Self-Hosting**
🌟 **Nur für spezielle Anwendungsfälle wie:**  
- **Bildungseinrichtungen oder Unternehmen**, die ihre eigene Instanz betreiben möchten  
- **Offline-Nutzung**, z. B. in Schulen ohne ständigen Internetzugang  
- **Entwickler & Forschungsteams**, die individuelle Anpassungen vornehmen möchten  

📌 **Technologie für Self-Hosting:**  
- **Docker-Container** für lokale Instanzen  
- **PostgreSQL oder SQLite** als Datenbank  
- **Unterstützt Raspberry Pi / MoodleBox für Offline-Installationen**  

💡 **Self-Hosting ist keine Voraussetzung für die Nutzung!**  
👉 **Mehr Infos:** [Self-Hosting-Anleitung](https://github.com/EcoSphereNetwork/Smolitux-Academy/blob/main/dezentrale-Hosting-Optionen.md)  

---

## **📦 Deployment-Workflow für das zentrale Hosting**

**EcoSphereNetwork verwaltet Smolitux Academy mit einer eigenen Server-Infrastruktur:**  

1️⃣ **Code-Entwicklung & Testing**  
   - Änderungen werden in GitHub gepusht  
   - GitHub Actions führt Tests & Code-Überprüfungen durch  

2️⃣ **Automatisches Build & Deployment auf eigene Server**  
   - Docker-Images werden in unserem internen Repository gespeichert  
   - Kubernetes orchestriert die Bereitstellung auf eigenen Servern  

3️⃣ **Skalierung & Monitoring**  
   - Kubernetes passt die Anzahl der Instanzen automatisch an  
   - **Eigener Load Balancer verteilt den Traffic**  

**Vorteile:**  
✅ **Volle Kontrolle über Infrastruktur & Datenschutz**  
✅ **Keine Abhängigkeit von externen Cloud-Anbietern**  
✅ **Optimierte Performance & Skalierbarkeit**  

---

## **🎓 Kursmanagement & Monetarisierung**
### **💰 Bezahlmöglichkeiten (Blockchain & Fiat)**
Smolitux Academy unterstützt **zwei Zahlungsarten**:
1. **Krypto-Zahlung über ESN_Token & Smart Contracts**  
2. **Fiat-Zahlung (Kreditkarte, PayPal, Stripe)**  

**Smart Contracts ermöglichen:**
- **Sichere & transparente Zahlungen** ohne zentrale Kontrolle.  
- **Automatische Kursfreigabe nach Zahlungseingang**.  
- **NFT-Zertifikate für abgeschlossene Kurse**.  

**Kursanbieter können entscheiden:**
- Ob ihr Kurs **kostenlos oder kostenpflichtig** ist.  
- Welche Währung sie akzeptieren (**ESN_Token, ETH, MATIC oder Fiat**).  

---

## **🚀 Deployment für Self-Hosting (Nur für fortgeschrittene Nutzer)**

Falls du Smolitux Academy auf deiner eigenen Infrastruktur hosten möchtest, folge dieser Anleitung:

### **🔹 Voraussetzungen**
- Docker & Docker-Compose  
- PostgreSQL oder SQLite (für Datenbank)  
- IPFS (optional für dezentrale Speicherung)  

### **🔹 Installation**
1. **Repository klonen:**
   ```bash
   git clone https://github.com/EcoSphereNetwork/Smolitux-Academy.git
   cd Smolitux-Academy
   ```

2. **Docker-Umgebung starten:**
   ```bash
   docker-compose up -d
   ```

3. **Datenbank konfigurieren:**  
   Bearbeite die `.env`-Datei, um PostgreSQL oder SQLite zu nutzen.

4. **Zugriff auf die lokale Instanz:**  
   - Öffne `http://localhost:8080` im Browser  
   - Logge dich mit dem Standard-Admin-Account ein  

📌 **Weitere Self-Hosting-Details:** 👉 [Self-Hosting-Optionen](https://github.com/EcoSphereNetwork/Smolitux-Academy/blob/main/dezentrale-Hosting-Optionen.md)  

---

## **🔮 Fazit, Vorteile & Empfehlung**

✅ **Hauptplattform wird zentral von EcoSphereNetwork verwaltet (ähnlich Udemy)**  
✅ **Skalierbare Architektur für Tausende Nutzer weltweit**  
✅ **Hybrid-Modell mit dezentralen Zahlungsoptionen (Web3, NFTs)**  
✅ **Zusätzliche Self-Hosting-Option für spezielle Anwendungsfälle**  
✅ **Nutze die offizielle Plattform, gehostet von EcoSphereNetwork, um Smolitux Academy sofort zu verwenden.**  
✅ **Self-Hosting ist nur für spezialisierte Nutzer gedacht – Standard-Nutzer brauchen dies nicht!**  

📌 **Zentrale Plattform:**  
🌎 **[https://academy.ecospherelabs.com](https://academy.ecospherelabs.com)**  

📌 **Fragen oder Unterstützung?**  
💬 **[Support & Diskussionen](https://github.com/EcoSphereNetwork/Smolitux-Academy/discussions)**  

---
