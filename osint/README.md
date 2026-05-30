# OSINT : laposte.net

Reconnaissance passive sur le domaine laposte.net via des outils publics.

## Outils utilisés :
- DNSDumpster : cartographie des sous-domaines
- Have I Been Pwned : vérification des fuites de données

## DNSDumpster résultats :

66 sous-domaines trouvés (50 affichés en version gratuite).

### Sous-domaines sensibles identifiés :

**Environnements de développement/test exposés publiquement :**
- `adminportal-dev.laposte.net` : portail d'administration en environnement DEV
- `adminportal-qlf-int.laposte.net` : environnement de qualification (qlf)
- `mgc-pre.laposte.net` : environnement de préproduction
- `mgc-pre-api-messagerie.laposte.net` : API messagerie en preprod
- `education.preprod.laposte.net` : service éducatif en preprod

Le pattern `-dev`, `-qlf`, `-pre` répété est un red flag : 
La Poste expose ses environnements de test sur internet.
Ces environnements sont généralement moins sécurisés que la production.

**Infrastructure critique identifiée :**
- `mairies-mail.laposte.net` : La Poste gère l'infrastructure 
  email de mairies françaises. Compromission = données de 
  services publics exposées.
- `mgc-api-messagerie.laposte.net` : API de messagerie exposée sur Google Cloud

**Serveur FTP exposé :**
- FileZilla Server 0.9.60 beta détecté : version ancienne, 
  potentiellement vulnérable

### Hébergeurs identifiés
- Worldline : hébergeur principal
- Google Cloud Platform : APIs et services secondaires
- Cloudflare : protection DDoS sur certains sous-domaines
- Claranet : hébergeur secondaire

## Have I Been Pwned résultats :

Email personnel trouvé dans une fuite de données :

**Pass'Sport (décembre 2025)**
- Fuite de données du programme Pass'Sport du gouvernement français
- 6,5 millions d'adresses email affectées, 3,5 millions de foyers
- Données compromises : email, nom, genre, téléphone, adresse postale
- Le Ministère des Sports a reconnu publiquement l'incident

## Analyse RGPD

| Finding | Article RGPD | Risque |
|---------|-------------|--------|
| Environnements dev/test exposés | Art. 32 - mesures techniques | Surface d'attaque élargie |
| Infrastructure email des mairies exposée | Art. 32 - sécurité des données publiques | Impact sur services publics |
| FTP non sécurisé détecté | Art. 32 - chiffrement | Données en transit non protégées |


## Fichiers
- `dnsdumpster-1.png` : vue globale infrastructure
- `dnsdumpster-2.png` : sous-domaines sensibles
- `hibp-results.png` : résultat Have I Been Pwned
