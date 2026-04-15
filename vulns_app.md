# Audit Applicatif - DVWA

Date : 14/04/2026

## 1. URL Identifiée

**DVWA** : http://10.74.1.65:80

## 2. Vulnérabilités Applicatives

### SQL Injection

**Application DVWA** (Niveau Low)
**Champ vulnérable** User ID
**Payload utilisé**
1' OR 1=1 -- 

Résulat : 

Affichage de toutes les entrées de la base de données :

admin
Gordon
Hack
Pablo
Bob

<img width="492" height="303" alt="image" src="https://github.com/user-attachments/assets/2f237a7d-54b6-4817-a58c-adee4f569731" />

### XSS reflected

**Application DVWA**
**Champ vulnérable** "What's your name?"
**Payload utilisé** <script>alert(1);</script>

Résultat :

Exécution du script côté client, affichant une alerte "Hello".

<img width="487" height="112" alt="image" src="https://github.com/user-attachments/assets/adca3a96-579a-4fae-a16b-d3371cdba163" />

Les entrées utilisateur sont renvoyées sans encodage, permettant l’exécution de scripts JavaScript dans le navigateur de la victime.

### IDOR

**Application DVWA**
**Description** Un utilisateur peut accéder à la page "Authorization Bypass" en modifiant l'URL.
**Preuve** Lien direct : http://10.74.1.65/DVWA/vulnerabilities/authbypass/

Résultat : Accès possible sans privilège admin.

### Headers

**Application DVWA**
**Headers manquants ou mal configurés **

- X-Frame-Options : Absent
- Content-Security-Policy : Absent
- Server : Apache/2.4.66

<img width="881" height="310" alt="image" src="https://github.com/user-attachments/assets/e8c90e3d-78c8-4352-9665-8ac850433a20" />
