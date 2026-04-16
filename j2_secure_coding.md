### SQLi (avant)

$query = "SELECT * FROM users WHERE name = 
'".$_GET['name']."';";

### Correction SQLi (après)

$stmt = $pdo->prepare("SELECT * FROM users WHERE name = 
?");
$stmt->execute([$_GET['name']]);
$users = $stmt->fetchALL();

**Explication** 

- Avant : La requête SQL est construite en concaténant directement l'entrée utilisateur et donc un attaquant peut injecter du code SQL.

- Après : L'utilisation des requêtes préparées (prepare + execute) fait que les données utilisateurs sont séparées de la requête SQL et est donc impossible à interpréter comme du code SQL.


### XSS (avant)

echo "Bonjour" . $_GET['name'];

### Correction XSS (après) 
echo "Bonjour" . htmlspecialchars($_GET['name'],ENT_QUOTES, 'UTF-8');

**Explication**

- Avant : Les données utilisateurs sont affichées directement et donc un attaquant peit injecter du JavaScript dans la page.

- Après : L'utilisation de htmlspecialchar() fait que les caractères spéciaux sont encodés et donc le navigateur affiche le texte au lieu de l'exécuter.

### Headers HTTP de sécurité (avant)

Pas de présence de X-frame, X-Content et X-XSS-Protecttion

### Header HTTP de sécurité ajout dans PHP (après)

header("X-Frame-Options: DENY");
header("X-Content-Type-Options: nosniff");
header("X-XSS-Protection: 1; mode=block");

**Explication**

- Avant : Aucune protection au niveau des headers HTTP.

- Après : Ajout des Headers de sécurité,
	
	- X-Frame-Options -> Empêche le clickjacking
	- X-Content-Type-Options -> évite le sniffing de type MIME
	- X-XSS-Protection -> active une protection XSS côté navigateur
