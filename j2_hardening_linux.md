### Hardening Linux - Jour 2

## 1. SSH

- Port changé : 22 -> 2222
- PermitRootLogin : désactivé (no)
- PasswordAuthentication : désactivé (no)
- Authentification par clé SSH : activé

## 2. Firewall UFW

- UFW activé
- Règles appliquées : 
	- 2222/tcp : autorisé (SSH)
	- 80/tcp : autorisé (HTTP)
	- 443/tcp : autorisé (HTTPS)
	- Tout le reste : BLOQUE

## 3. Permissions fichiers

- /etc/shadow : chmod 640, chown root:shadow
- Fichier 777 : aucune liste trouvée

## 4. Comptes et SUID

- Comptes inutiles supprimés : Auncun
- Fichier SUID suspects trouvés : Liste



## 5. Conclusion

Ce qu'on a corrigé : 

- SSH sécurisé (port, root, clé)
- Firewall actif et restrictif
- Permissions /etc/shadow renforcées

Ce qui reste à surveiller : 

- Mettre à jour régulièrement les paquets (apt upgrade)
- Surveillance constante des logs (/var/log/auth.log)
- Vérifier régulièrement les fichiers SUID


