# Audit Applicatif - DVWA

Date : 14/04/2026

## 1. URL Identifiée

**DVWA** : http://10.74.1.65:80

## 2. Vulnérabilités Applicatives

### SQL Injection

**Application DVWA** (Niveau Low)
**Champ vulnérable** User ID
**Payload utilisé** ```sql
1' OR 1=1 -- 
```
Résulat : 

Affichage de toutes les entrées de la base de données :

admin
Gordon
Hack
Pablo
Bob

### XSS reflected

**Application DVWA**
**Champ vulnérable** "What's your name?"
**Payload utilisé** <script>alert(1);</script>

Résultat :

Exécution du script côté client, affichant une alerte "Hello".

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
