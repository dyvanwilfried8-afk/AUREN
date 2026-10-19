# AUREN
# AUREN — mise en ligne pas à pas

AUREN est un site (GitHub Pages) qui lit ET écrit dans ton Google Sheet DASHBOARD. Tout ce que tu modifies sur le site (objectif, dépenses…) est enregistré dans le Sheet.

## Partie A — Le script Google (le « cerveau »)
1. Ouvre ton Google Sheet DASHBOARD. Menu **Extensions > Apps Script**.
2. Supprime le code d'exemple, colle tout le contenu de `apps-script/Code.gs`, puis clique sur l'icône disquette (Enregistrer).
3. À gauche, clique sur la roue dentée **Paramètres du projet**. En bas, **Propriétés du script > Ajouter une propriété** : nom `TOKEN`, valeur = ton code secret (long, ex. 20 caractères). Enregistre. Garde ce code : tu le taperas sur le site.
4. En haut à droite, **Déployer > Nouveau déploiement**. Roue dentée > **Application Web**. « Exécuter en tant que » : **Moi**. « Qui a accès » : **Tout le monde**. Clique **Déployer**, accepte les autorisations (« Paramètres avancés » > « Accéder à… » si Google avertit).
5. Copie l'**URL de l'application Web** (elle finit par `/exec`).
6. Test : colle `URL?token=TON_CODE` dans le navigateur. Tu dois voir du texte JSON avec tes chiffres.

## Partie B — GitHub (la vitrine)
1. Crée un compte sur github.com si besoin.
2. **+ > New repository**. Nom : `auren`. Choisis **Public** (GitHub Pages gratuit). Coche « Add a README » puis **Create repository**.
3. Dans ton dépôt : **Add file > Upload files**, glisse `index.html`, puis **Commit changes**.
4. Clique sur `index.html` > icône crayon. Remplace `COLLE_ICI_L_URL_APPS_SCRIPT` par l'URL de l'étape A5 (garde les guillemets). **Commit changes**.
5. **Settings > Pages**. « Source » : Deploy from a branch. Branche `main`, dossier `/ (root)`. **Save**.
6. Attends 1 à 2 minutes. Ton site : `https://TON-PSEUDO.github.io/auren/`.

## Partie C — Premier lancement
Ouvre le site, tape ton code (`TOKEN`). Il est mémorisé sur cet appareil. Sur ton téléphone, tape-le une fois aussi. Tu peux ajouter le site à l'écran d'accueil.

## Utilisation
- **Réglages** : objectif, seuil Airbus, budget mensuel.
- **Dépenses** : ajoute ou supprime une dépense. Les onglets `Dépenses` et `AUREN Réglages` apparaissent tout seuls dans ton Sheet.
- Les chiffres de patrimoine restent pilotés par ton Sheet (CTO, Airbus, Crypto…).

## Mise à jour
- Site : GitHub > `index.html` > crayon > modifier > Commit.
- Script : Apps Script > coller > **Déployer > Gérer les déploiements > crayon > Nouvelle version > Déployer** (sans ça, l'ancienne version reste active).

## Sécurité
Le code du site est public, pas tes données : sans `TOKEN`, l'API répond « unauthorized ». Ne mets jamais le `TOKEN` dans GitHub. Pour le changer : modifie la propriété `TOKEN`, puis retape-le sur le site.

## Dépannage
- « Connexion impossible » : l'URL `/exec` est fausse ou l'accès n'est pas « Tout le monde ».
- « Code incorrect » : le `TOKEN` ne correspond pas.
- L'ajout de dépense échoue : tu n'as pas redéployé une nouvelle version après avoir collé le nouveau `Code.gs`.
