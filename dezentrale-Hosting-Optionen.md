## **🔹 Technischer Plan für dezentrale Hosting-Optionen in Smolitux Academy**
Da Smolitux Academy sowohl **lokal als auch in der Cloud** gehostet werden soll, müssen wir eine hybride Architektur schaffen. Diese erlaubt es Nutzern, die Plattform entweder auf **eigenen Servern (z. B. Raspberry Pi, VPS) oder in der Cloud** zu betreiben.

---

## **🔹 1️⃣ Architektur-Überblick**
Smolitux Academy wird als **modulare, containerisierte Plattform** entwickelt, sodass sie flexibel auf verschiedenen Hosting-Optionen laufen kann:

| **Hosting-Option** | **Technologie** | **Zielgruppe** |
|------------------|----------------|----------------|
| **Lokal auf Raspberry Pi / MoodleBox** | Moodle + Docker + IPFS | Schulen, Entwickler, kleine Communities |
| **VPS (Virtual Private Server)** | Docker + PostgreSQL | Kleine bis mittelgroße Lernplattformen |
| **Cloud (AWS, DigitalOcean, GCP)** | Kubernetes + Load Balancer | Große öffentliche Instanzen |
| **Dezentrale Speicherung** | IPFS + Filecoin | Nutzer können Daten dezentral speichern |

---

## **🔹 2️⃣ Hosting-Optionen & Anpassungen**
### **🖥️ Option A: Lokales Hosting (Raspberry Pi / MoodleBox)**
✅ **Warum?**  
- Ermöglicht **Offline-Lernen**, ideal für Schulen & Organisationen ohne stabile Internetverbindung.  
- Erfordert **geringe Hardware-Ressourcen**.  

✅ **Technische Anpassungen:**  
- MoodleBox-Fork mit zusätzlichen **Docker-Containern für Blockchain-Integration**.  
- **Datenbank-Speicherung auf lokalem PostgreSQL / SQLite**.  
- **Lokaler IPFS-Knoten**, um Dateien ohne Cloud zu speichern.  

✅ **Setup:**  
1. **Betriebssystem vorbereiten**  
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```
2. **Docker installieren**  
   ```bash
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   ```
3. **Smolitux Academy installieren**  
   ```bash
   git clone https://github.com/EcoSphereNetwork/Smolitux-Academy.git
   cd Smolitux-Academy
   docker-compose up -d
   ```

---

### **🌍 Option B: VPS (Virtual Private Server, z. B. DigitalOcean, Hetzner)**
✅ **Warum?**  
- Einfache Wartung für **kleine & mittlere Anbieter**.  
- Erlaubt **globale Nutzung**, ohne auf große Cloud-Dienste angewiesen zu sein.  

✅ **Technische Anpassungen:**  
- Nutzung eines **Docker-Compose-Stacks für Moodle, Blockchain & IPFS**.  
- **Reverse Proxy mit Nginx** für HTTPS-Zugriff.  

✅ **Setup:**  
1. **Server aufsetzen (Ubuntu 22.04 empfohlen)**  
   ```bash
   sudo apt update && sudo apt install docker docker-compose -y
   ```
2. **Docker-Compose Datei für Smolitux Academy erstellen**
   ```yaml
   version: '3'

   services:
     smolitux:
       image: moodle
       ports:
         - "8080:80"
       volumes:
         - moodle_data:/var/www/html
       environment:
         - MOODLE_DB_HOST=postgres
         - MOODLE_DB_USER=admin
         - MOODLE_DB_PASSWORD=secret

     postgres:
       image: postgres
       environment:
         POSTGRES_USER: admin
         POSTGRES_PASSWORD: secret
       volumes:
         - db_data:/var/lib/postgresql/data

   volumes:
     moodle_data:
     db_data:
   ```
3. **Deployment starten**  
   ```bash
   docker-compose up -d
   ```

---

### **☁️ Option C: Cloud (AWS, GCP, Azure)**
✅ **Warum?**  
- **Skalierbare Lösung** für große Anbieter.  
- **Automatische Skalierung & Load Balancing** möglich.  

✅ **Technische Anpassungen:**  
- Nutzung von **Kubernetes** für Skalierbarkeit.  
- **Cloud Storage** für Kursdateien (z. B. S3, Google Cloud Storage).  
- **Automatische Skalierung mit Load Balancer**.  

✅ **Setup:**  
1. **Kubernetes Cluster aufsetzen (AWS EKS, GCP GKE, Azure AKS)**  
   ```bash
   eksctl create cluster --name smolitux-academy
   ```
2. **Deployment von Moodle & Blockchain-Integration**  
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
           image: moodle
           ports:
           - containerPort: 80
   ```

---

### **📂 Option D: Dezentrale Speicherung mit IPFS**
✅ **Warum?**  
- **Verhindert zentrale Kontrolle über Daten**.  
- Erlaubt **dezentrale Speicherung von Kursinhalten**.  

✅ **Technische Anpassungen:**  
- **Integration von IPFS für Dateispeicherung**.  
- Moodle speichert Kursdateien direkt in einem **IPFS-Knoten**.  

✅ **Setup:**  
1. **IPFS installieren**  
   ```bash
   wget https://dist.ipfs.io/go-ipfs/latest/go-ipfs.tar.gz
   tar -xvzf go-ipfs.tar.gz
   cd go-ipfs
   sudo ./install.sh
   ```
2. **Starten & Datei hochladen**  
   ```bash
   ipfs init
   ipfs daemon &
   echo "Hallo Smolitux Academy" > kursbeschreibung.txt
   ipfs add kursbeschreibung.txt
   ```
3. **Datei über IPFS abrufen**  
   ```bash
   ipfs cat <hash>
   ```

---

## **🔹 3️⃣ Vergleich der Hosting-Optionen**
| **Option** | **Vorteile** | **Nachteile** |
|------------|------------|------------|
| **Lokal (Raspberry Pi, MoodleBox)** | Offline-Funktion, keine Cloud-Abhängigkeit | Geringe Rechenleistung, weniger Skalierbarkeit |
| **VPS (DigitalOcean, Hetzner, Linode)** | Leicht zu verwalten, flexibel | Manuelle Wartung erforderlich |
| **Cloud (AWS, GCP, Azure)** | Skalierbar, automatische Updates | Höhere Kosten, Abhängigkeit von Cloud-Anbietern |
| **Dezentral (IPFS, Filecoin)** | Kein zentraler Server nötig, zensurresistent | Langsamere Performance, Komplexität |

---

## **🚀 Nächste Schritte & Umsetzung**
✅ **Entwicklung eines Docker-Images für Smolitux Academy**  
✅ **Testen der Blockchain-Integration in einer dezentralen Umgebung**  
✅ **Erstellung einer IPFS-Schnittstelle für Moodle**  

