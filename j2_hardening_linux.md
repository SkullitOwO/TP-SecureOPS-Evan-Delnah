### Hardening Linux - Jour 2

## 1. SSH

- Port changé : 22 -> 2222
- PermitRootLogin : désactivé (no)
- PasswordAuthentication : désactivé (no)
- Authentification par clé SSH : activé

<img width="560" height="482" alt="image" src="https://github.com/user-attachments/assets/1738e7e0-febd-4598-8a5a-a3a4fea80c54" />

<img width="932" height="238" alt="image" src="https://github.com/user-attachments/assets/987fc9ac-96b0-4e50-b12c-41276f7aeaa1" />


## 2. Firewall UFW

- UFW activé
- Règles appliquées : 
	- 2222/tcp : autorisé (SSH)
	- 80/tcp : autorisé (HTTP)
	- 443/tcp : autorisé (HTTPS)
	- Tout le reste : BLOQUE

   <img width="930" height="388" alt="image" src="https://github.com/user-attachments/assets/9e2d6599-e1ef-4be5-aa3d-8ff5ff160fd6" />


## 3. Permissions fichiers

- /etc/shadow : chmod 640, chown root:shadow
- Fichier 777 : aucune liste trouvée

  <img width="931" height="87" alt="image" src="https://github.com/user-attachments/assets/fe967492-b16f-439f-abdb-c57fb40fee52" />

  <img width="947" height="803" alt="image" src="https://github.com/user-attachments/assets/9c210d52-14e5-4b85-ab8c-9401fb959b34" />

## 4. Comptes et SUID

- Comptes inutiles supprimés : Auncun
- Fichier SUID suspects trouvés : Liste

<img width="1478" height="358" alt="image" src="https://github.com/user-attachments/assets/2530456c-37eb-4898-9ec9-65b3e94144a1" />


## 5. Conclusion

Ce qu'on a corrigé : 

- SSH sécurisé (port, root, clé)
- Firewall actif et restrictif
- Permissions /etc/shadow renforcées

Ce qui reste à surveiller : 

- Mettre à jour régulièrement les paquets (apt upgrade)
- Surveillance constante des logs (/var/log/auth.log)
- Vérifier régulièrement les fichiers SUID


