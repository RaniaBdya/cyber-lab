# Cyber Lab : Network Analysis & Penetration Testing

## Stack
Kali Linux 2026.1 · Nmap · Wireshark · Metasploit · John the Ripper · VirtualBox

## Environnement
- Attaquant : Kali Linux 2026.1 (VM)
- Cible : Metasploitable2 (VM)
- Réseau : isolé (Host-Only 192.168.56.0/24)

## Ce que j'ai fait :

### 1. Reconnaissance réseau avec Nmap
Scan du réseau local, détection de services et versions sur deux cibles.

### 2. Analyse de trafic avec Wireshark
Capture de trafic ICMP et DNS, filtrage par protocole.

### 3. Exploitation - CVE-2011-2523 (vsFTPd 2.3.4 backdoor)
Détection de la faille via Nmap scripting engine, exploitation avec Metasploit,
obtention d'un accès root sur la cible.

### 4. Post-exploitation
Extraction de /etc/shadow, cassage de hash MD5 avec John the Ripper.


## Avertissement légal
Tous les tests ont été réalisés sur des machines 
virtuelles personnelles dans un environnement isolé. 
Aucun système tiers n'a été ciblé.

## Contenu
| Dossier | Description |
|--------|-------------|
| `/nmap` | Scans de reconnaissance et détection de vulnérabilités |
| `/writeups` | Rapports détaillés d'exploitation |
| `/osint` | Reconnaissance passive - DNSDumpster, HIBP |
