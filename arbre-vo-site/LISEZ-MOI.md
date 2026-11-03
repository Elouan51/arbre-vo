# Arbre de préparation VO : mise en ligne

Ce dossier est un site prêt à héberger (GitHub Pages, Netlify ou n'importe quel hébergeur de fichiers).
Il lit et écrit directement dans le Google Sheet « STOCK VO », l'agenda Google et le dossier photos du Drive,
avec le compte Google de la personne connectée. Aucun serveur, aucun abonnement.

Il y a **une seule chose à régler** : `config.js` (l'identifiant de connexion Google). Compte 10 minutes, une fois pour toutes.

---

## Étape 1 : créer l'identifiant Google (Client ID)

1. Va sur **https://console.cloud.google.com** avec ton compte Google (celui du Sheet).
2. En haut, **Sélectionner un projet → Nouveau projet**. Nom : `Arbre VO`, puis **Créer**.
3. Menu ☰ → **API et services → Bibliothèque**. Cherche et clique **Activer** sur ces 3 API :
   - Google Sheets API
   - Google Calendar API
   - Google Drive API
4. Menu ☰ → **API et services → Écran de consentement OAuth** (ou « Google Auth Platform »).
   - Type d'utilisateur : **Externe**.
   - Nom de l'application : `Arbre VO`, e-mail d'assistance : le tien. Enregistre.
   - Dans **Audience / Utilisateurs test**, ajoute les adresses Gmail de ceux qui utiliseront l'app (toi, la secrétaire, le patron).
5. Menu ☰ → **API et services → Identifiants → Créer des identifiants → ID client OAuth**.
   - Type : **Application Web**.
   - **Origines JavaScript autorisées** : ajoute l'adresse de ton site (étape 2), par exemple :
     - `https://ton-pseudo.github.io` (GitHub Pages : uniquement le domaine, sans le nom du dépôt)
     - ou `https://arbre-vo.netlify.app` (Netlify)
   - Laisse « URI de redirection » vide. **Créer**.
6. Copie l'**ID client** (il finit par `.apps.googleusercontent.com`).
7. Ouvre `config.js` et remplace `COLLE-TON-ID-CLIENT.apps.googleusercontent.com` par ton ID. Enregistre.

> Tu ne connais pas encore l'adresse du site ? Fais d'abord l'étape 2, puis reviens ajouter l'origine à l'étape 5. Le changement prend effet en quelques minutes.

---

## Étape 2 : mettre le site en ligne

### Option A : GitHub Pages (gratuit)
1. Sur **github.com**, crée un compte si besoin, puis **New repository**. Nom : `arbre-vo`. Public. **Create repository**.
2. Clique **uploading an existing file**, glisse **tout le contenu de ce dossier** (pas le dossier lui-même), puis **Commit changes**.
3. Dans le dépôt : **Settings → Pages → Source : Deploy from a branch → main / (root) → Save**.
4. Une minute après, ton site est à l'adresse `https://ton-pseudo.github.io/arbre-vo/`.

### Option B : Netlify (encore plus simple)
1. Va sur **https://app.netlify.com/drop**.
2. Glisse le dossier entier dans la page. C'est en ligne.
3. Crée un compte pour le garder, puis **Site configuration → Change site name** (ex. `arbre-vo`) → adresse `https://arbre-vo.netlify.app`.

Pour mettre à jour plus tard : remplace simplement les fichiers (GitHub : upload à nouveau ; Netlify : onglet **Deploys**, glisse le dossier).

---

## Étape 3 : l'utiliser comme une app

- **iPhone** : ouvre le site dans Safari → bouton Partager → **Sur l'écran d'accueil**.
- **Android** : Chrome → ⋮ → **Installer l'application**.
- **Mac** : Safari → Fichier → **Ajouter au Dock** (ou Chrome → ⋮ → Caster, enregistrer et partager → Installer la page en tant qu'application).

À la première connexion, Google affiche **« Google n'a pas validé cette application »** : c'est normal pour une app interne.
Clique **Continuer**, puis coche les autorisations (Sheet, Agenda, Drive).

---

## Bon à savoir

- **Qui peut l'utiliser ?** Uniquement les adresses ajoutées en « Utilisateurs test » (jusqu'à 100), et chacun ne voit que ce que son compte Google peut ouvrir. La secrétaire doit donc avoir accès en modification au Google Sheet.
- **Agenda** : chacun voit et remplit **son propre** agenda Google.
- **Connexion** : Google demande de se reconnecter environ toutes les heures (un clic). Si une action était en cours, elle est envoyée juste après.
- **La dictée** a été retirée de cette version (elle fonctionnait grâce à Claude).
- **Rien n'est stocké sur l'hébergeur** : le site ne contient aucune donnée, tout reste dans ton Google Sheet et ton Drive.
- **Fichiers** : `index.html` (l'app), `config.js` (ton identifiant), `manifest.webmanifest` + icônes (installation sur l'écran d'accueil), logos `lsa.png` et `vpn.png`.
