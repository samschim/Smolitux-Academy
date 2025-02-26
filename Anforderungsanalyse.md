# **📌 Anforderungsanalyse & Planung – Smolitux Academy**

## **📍 1. Einführung**
Smolitux Academy ist eine **blockchain-basierte E-Learning-Plattform**, die es ermöglicht, Kurse anzubieten, zu verwalten und zu monetarisieren. Die Plattform wird von **EcoSphereNetwork zentral gehostet**, bietet aber eine **optionale Self-Hosting-Funktion**.  

Diese Anforderungsanalyse beschreibt die funktionalen und nicht-funktionalen Anforderungen sowie die technischen Grundlagen der Plattform.

---

## **📌 2. Zielsetzung des Projekts**
### **🔹 Primäre Ziele:**
✅ **Zentrale, skalierbare E-Learning-Plattform, gehostet von EcoSphereNetwork**  
✅ **Dezentrale Zahlungs- & Zertifikatsysteme mittels Blockchain**  
✅ **NFT-basierte Kurszertifikate für verifizierte Abschlüsse**  
✅ **Kursanbieter können ihre Kurse kostenfrei oder kostenpflichtig anbieten**  
✅ **Gamification & Tokenized Learning für Nutzerengagement**  
✅ **Optionales Self-Hosting für spezielle Anwendungsfälle**  

---

## **📌 3. Funktionale Anforderungen**
| **Kategorie** | **Anforderung** | **Priorität** |
|--------------|----------------|--------------|
| **Kursverwaltung** | Erstellung, Bearbeitung & Verwaltung von Kursen | Hoch |
| | Kategorisierung & Suchfunktion für Kurse | Hoch |
| | Upload von Kursmaterialien (Videos, PDFs, Quizzes) | Hoch |
| | Gamification-Elemente (Punkte, Abzeichen, XP) | Mittel |
| **Benutzerverwaltung** | Registrierung & Login (E-Mail, Google, Web3-Wallets) | Hoch |
| | Rollenmanagement (Lernende, Kursanbieter, Admins) | Hoch |
| | Nutzerprofile mit Fortschrittsübersicht | Mittel |
| **Monetarisierung & Blockchain** | Bezahlung von Kursen via ESN_Token / Krypto | Hoch |
| | NFT-Zertifikate für bestandene Kurse | Hoch |
| | Tokenized Learning (Belohnungen für Lernaktivitäten) | Mittel |
| **Community-Features** | Foren, Diskussionen & Bewertungen für Kurse | Mittel |
| | Direktnachrichten zwischen Nutzern | Niedrig |
| **Dezentrale Speicherung** | Speicherung von Kursmaterialien auf IPFS (optional) | Mittel |

---

## **📌 4. Nicht-funktionale Anforderungen**
| **Kategorie** | **Anforderung** |
|--------------|----------------|
| **Skalierbarkeit** | Unterstützung für Tausende gleichzeitige Nutzer |
| **Performance** | Minimale Ladezeiten, Caching für schnellere Antwortzeiten |
| **Sicherheit** | End-to-End-Verschlüsselung für Zahlungen & Nutzerdaten |
| **Verfügbarkeit** | 99,9 % Uptime durch Load Balancer & Hochverfügbarkeit |
| **Benutzerfreundlichkeit** | Intuitive UI/UX, responsive Design für mobile Nutzung |
| **Nachhaltigkeit** | Unterstützung energieeffizienter Blockchain-Lösungen |

---

## **📌 5. Technische Grundlagen**
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

---

## **📌 6. Systemarchitektur & Schnittstellen**
### **🔹 1. Systemübersicht**
Smolitux Academy basiert auf einer **modularen Architektur** mit einer klaren Trennung von **Frontend, Backend, Blockchain & Datenbank**.

```
+--------------------+       +---------------------+       +------------------+
|  Web UI (React)   | <---> |  API (Node.js)      | <---> |  PostgreSQL DB   |
|  Nutzer & Kurse   |       |  REST & Web3 API    |       |  Kursdatenbank   |
+--------------------+       +---------------------+       +------------------+
          |                           |                           |
          v                           v                           v
+--------------------+       +---------------------+       +------------------+
|  Web3 Blockchain  | <---> |  Smart Contracts    | <---> |  NFT-Zertifikate  |
|  Zahlungen & NFTs |       |  ESN_Token & NFTs   |       |  Kursabschlüsse   |
+--------------------+       +---------------------+       +------------------+
```

### **🔹 2. API & Schnittstellen**
- **REST API für Kursverwaltung & Nutzeranmeldung**  
- **Web3 API für Blockchain-Interaktionen (Zahlungen, NFT-Zertifikate)**  
- **Datenbank-API für Kurse, Nutzerprofile & Transaktionen**  

---

## **📌 7. Risiken & Gegenmaßnahmen**
| **Risiko** | **Mögliche Auswirkungen** | **Gegenmaßnahmen** |
|---|---|---|
| **Blockchain-Integration verzögert sich** | Zahlungen & NFT-Zertifikate nicht rechtzeitig einsatzbereit | Frühzeitiges Testen im Testnet, Parallele Entwicklung von Smart Contracts |
| **Performance-Probleme bei hoher Nutzerzahl** | Langsame Ladezeiten, Überlastung der Server | Skalierung durch Kubernetes, Lasttests vor dem Launch |
| **Sicherheitslücken in Web3-Integration** | Angriffsrisiko auf Wallets & Zahlungen | Security-Audits & externe Penetration-Tests |
| **Geringe Nutzerakzeptanz** | Wenig Engagement auf der Plattform | Marketing-Strategie & Partnerschaften mit Kursanbietern |
| **Kosten für Server & Infrastruktur steigen** | Höhere Betriebskosten für EcoSphereNetwork | Kostenoptimierung durch eigene Server & effiziente Skalierung |

---

## **📌 8. Fazit & Nächste Schritte**
✅ **Die Smolitux Academy hat eine klare technische Vision & funktionale Ziele.**  
✅ **Die wichtigsten Schnittstellen, Anforderungen & Risiken sind definiert.**  
✅ **Nächster Schritt:** Start der **Phase 1: Anforderungsanalyse & Architekturaufbau**.  

