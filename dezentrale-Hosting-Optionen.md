
# **🌍 Smolitux Academy – Optionale Self-Hosting Möglichkeit**

🚀 **Smolitux Academy wird zentral von EcoSphereNetwork gehostet**.  
📌 **Die meisten Nutzer brauchen kein eigenes Hosting – einfach anmelden & loslegen!**  

Diese Anleitung richtet sich an **fortgeschrittene Nutzer**, die eine eigene Smolitux Academy-Instanz betreiben möchten.  
🌟 **Self-Hosting ist eine Zusatzoption, nicht die empfohlene Standardmethode.**  

🔗 **Zugriff auf die offizielle Plattform:**  
🌎 **[https://academy.ecospherelabs.com](https://academy.ecospherelabs.com)**  

---

## **📌 Wann macht Self-Hosting Sinn?**
✅ **Bildungseinrichtungen & Unternehmen**, die eine private Instanz betreiben möchten  
✅ **Offline-Nutzung** für Schulen oder Organisationen ohne stabile Internetverbindung  
✅ **Forschungsteams & Entwickler**, die eigene Features oder Blockchain-Integrationen testen möchten  
✅ **Anbieter, die volle Kontrolle über Daten & Hosting behalten wollen**  

🚫 **Für die meisten Nutzer ist Self-Hosting nicht erforderlich!**  
📌 **Nutze stattdessen die zentrale Smolitux Academy Plattform.**  

---

## **📦 Self-Hosting-Technologie & Infrastruktur**
Self-Hosting erfordert eine eigene Server-Infrastruktur oder einen lokalen Rechner.  
**Unterstützte Umgebungen:**
- **Lokaler Server oder dedizierte Hardware** (z. B. Linux-Server, Raspberry Pi)
- **Virtuelle Maschinen oder VPS** (z. B. Proxmox, Hetzner, DigitalOcean)
- **Kubernetes Cluster auf eigenen Servern** (keine externe Cloud-Dienste)
- **Dezentrale Speicherung mit IPFS** (optional)

📌 **Empfohlene Mindestanforderungen:**
| **Komponente** | **Mindestanforderung** |
|--------------|-----------------|
| **CPU** | 4 vCPUs |
| **RAM** | 8 GB |
| **Speicher** | 100 GB SSD |
| **Betriebssystem** | Ubuntu 22.04 / Debian 11 |
| **Netzwerk** | Statischer IP-Zugang für öffentliche Instanzen |

---
## **🔹Architektur-Überblick**
Smolitux Academy wird als **modulare, containerisierte Plattform** entwickelt, sodass sie flexibel auf verschiedenen Hosting-Optionen laufen kann:

| **Hosting-Option** | **Technologie** | **Zielgruppe** |
|------------------|----------------|----------------|
| **Lokal auf Raspberry Pi / MoodleBox** | Moodle + Docker + IPFS | Schulen, Entwickler, kleine Communities |
| **VPS (Virtual Private Server)** | Docker + PostgreSQL | Kleine bis mittelgroße Lernplattformen |
| **Cloud (AWS, DigitalOcean, GCP)** | Kubernetes + Load Balancer | Große öffentliche Instanzen |
| **Dezentrale Speicherung** | IPFS + Filecoin | Nutzer können Daten dezentral speichern |
---

## **🚀 Installation & Einrichtung**

### **1️⃣ Voraussetzungen**
- **Linux-Server oder VPS**
- **Docker & Docker-Compose**
- **PostgreSQL (oder SQLite für kleine Instanzen)**
- **IPFS für dezentrale Speicherung (optional)**

### **2️⃣ Installation**
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

---

## **🌐 Kubernetes-Deployment auf eigenen Servern**
📌 **Für größere Instanzen mit automatischer Skalierung empfehlen wir Kubernetes.**

### **1️⃣ Kubernetes Cluster aufsetzen**
1. **Erstelle einen Kubernetes Cluster auf eigenen Servern (Ubuntu 22.04):**
   ```bash
   kubeadm init --pod-network-cidr=10.244.0.0/16
   ```

2. **Deployment mit Kubernetes YAML-Datei:**
   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: smolitux
   spec:
     replicas: 3
     selector:
       matchLabels:
         app: smolitux
     template:
       metadata:
         labels:
           app: smolitux
       spec:
         containers:
         - name: moodle
           image: smolitux-academy
           ports:
           - containerPort: 8080
   ```

3. **Deployment starten:**
   ```bash
   kubectl apply -f smolitux-deployment.yaml
   ```

📌 **Mehr Details zur Kubernetes-Installation in der Dokumentation.**  

---

## **📂 Dezentrale Speicherung mit IPFS**
📌 **Optional kannst du Kursinhalte dezentral mit IPFS speichern.**  

### **1️⃣ IPFS installieren**
```bash
wget https://dist.ipfs.io/go-ipfs/latest/go-ipfs.tar.gz
tar -xvzf go-ipfs.tar.gz
cd go-ipfs
sudo ./install.sh
```

### **2️⃣ Kursmaterialien auf IPFS speichern**
```bash
echo "Lernmaterial von Smolitux Academy" > kursbeschreibung.txt
ipfs add kursbeschreibung.txt
```

### **3️⃣ Datei abrufen**
```bash
ipfs cat <hash>
```

📌 **Standardmäßig speichert Smolitux Academy Inhalte auf internen Servern. IPFS ist eine Zusatzoption.**  

---

## **🔧 Self-Hosting: Wartung & Updates**
1️⃣ **Updates erhalten:**  
   ```bash
   git pull origin main
   docker-compose down && docker-compose up -d
   ```

2️⃣ **Logs überprüfen:**  
   ```bash
   docker logs -f smolitux-backend
   ```

3️⃣ **Backup erstellen:**  
   ```bash
   pg_dump -U admin -h localhost smolitux_db > backup.sql
   ```

---

## **🚀 Fazit & Empfehlung**
✅ **Nutze die zentrale Plattform von EcoSphereNetwork für maximale Performance & Sicherheit.**  
✅ **Self-Hosting ist nur für spezifische Anwendungsfälle gedacht.**  
✅ **Eigene Server & keine externe Cloud-Abhängigkeit!**  

📌 **Zentrale Plattform:**  
🌎 **[https://academy.ecospherelabs.com](https://academy.ecospherelabs.com)**  

📌 **Fragen oder Unterstützung?**  
💬 **[Support & Diskussionen](https://github.com/EcoSphereNetwork/Smolitux-Academy/discussions)**  

---
