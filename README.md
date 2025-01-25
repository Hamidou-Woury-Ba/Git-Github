# Gestionnaire de versions avec Git et GitHub

## Introduction

Git est un outil de gestion de versions décentralisé, et GitHub est une plateforme d'hébergement pour les dépôts Git. Ces outils permettent de suivre l'évolution de votre code, de collaborer avec d'autres développeurs, et de gérer des versions de manière efficace.

---

## Initialisation et configuration de Git

1. **Configurer votre identité :**
   ```bash
   git config --global user.name "John Doe"
   git config --global user.email johndoe@example.com
   ```
   Ces commandes permettent d'associer votre nom et votre e-mail à vos commits. Cela est particulièrement utile lorsque vous collaborez avec d'autres personnes, car chaque modification sera attribuée à son auteur.

2. **Configurer les couleurs :**
   ```bash
   git config --global color.diff auto 
   git config --global color.status auto 
   git config --global color.branch auto
   ```
   Ces configurations améliorent la lisibilité des informations affichées par Git (par exemple, les différences entre fichiers seront colorées).

3. **Configurer l'éditeur par défaut :**
   ```bash
   git config --global core.editor "notepad++"
   ```
   Cela définit l'éditeur de texte utilisé pour modifier des messages de commit ou résoudre des conflits. Vous pouvez remplacer `notepad++` par l'éditeur de votre choix (comme `vim`, `nano`, ou `code` pour Visual Studio Code).

---

## Initialiser un dépôt Git

1. **Initialiser un dépôt local :**
   ```bash
   git init
   ```
   Cette commande crée un nouveau dépôt Git dans le dossier courant. Un répertoire caché `.git` est créé pour stocker toutes les informations relatives au dépôt.

---

## Gestion des fichiers

1. **Ajouter des fichiers à l'index :**
   ```bash
   git add <nom_du_fichier>
   ```
   Par exemple :
   ```bash
   git add index.html styles.css
   ```
   Cela déplace les fichiers spécifiés dans la zone de staging (index). Ces fichiers sont maintenant prêts à être enregistrés lors du prochain commit.

   > **Note :** Vous pouvez également utiliser `git add .` pour ajouter tous les fichiers modifiés ou créés.

2. **Créer un commit :**
   ```bash
   git commit -m "Message de commit"
   ```
   Cette commande enregistre les modifications de la zone de staging dans l'historique du dépôt avec un message décrivant les changements. Par exemple :
   ```bash
   git commit -m "Ajout des fichiers HTML et CSS"
   ```
   > **Conseil :** Écrivez des messages de commit clairs et concis pour faciliter la compréhension de l'historique.

---

## Gestion des branches

1. **Lister les branches :**
   ```bash
   git branch
   ```
   Cela affiche toutes les branches existantes. La branche courante est précédée d'un astérisque (*).

2. **Créer une nouvelle branche :**
   ```bash
   git branch <nom_de_la_branche>
   ```
   Exemple :
   ```bash
   git branch feature-authentication
   ```

3. **Changer de branche :**
   ```bash
   git checkout <nom_de_la_branche>
   ```
   Exemple :
   ```bash
   git checkout feature-authentication
   ```
   Cette commande vous téléporte dans une autre branche pour y travailler sans affecter la branche principale (`main`).

4. **Créer et basculer directement vers une nouvelle branche :**
   ```bash
   git checkout -b <nom_de_la_branche>
   ```
   Exemple :
   ```bash
   git checkout -b feature-login
   ```

---

## Fusion de branches

1. **Fusionner une branche :**
   ```bash
   git merge <nom_de_la_branche>
   ```
   Exemple :
   ```bash
   git merge feature-login
   ```
   Cela fusionne les modifications de la branche `feature-login` dans la branche courante.

> **Note :** En cas de conflit, Git vous demandera de résoudre les conflits manuellement avant de finaliser la fusion.

---

## Travailler avec les commits

1. **Revenir à un commit précédent :**
   ```bash
   git checkout <hash_du_commit>
   ```
   Cela vous permet d'explorer l'état du projet à un moment donné sans modifier l'historique.

2. **Appliquer un commit spécifique à une autre branche :**
   ```bash
   git cherry-pick <hash_du_commit>
   ```
   Cette commande copie un commit spécifique (identifié par son hash) dans la branche courante. Cela peut être utile pour appliquer des corrections sans fusionner une branche entière.

---

## Suivi et récupération des modifications

1. **Voir l'historique des actions (reflog) :**
   ```bash
   git reflog
   ```
   Cela affiche toutes les actions effectuées dans le dépôt, y compris les changements de branche, les resets, les merges, etc.

2. **Mettre de côté des modifications :**
   ```bash
   git stash
   ```
   Cela enregistre les modifications non indexées pour les récupérer plus tard. Les fichiers reviennent à leur état précédent.

   **Exemple d'utilisation :**
   - Vous travaillez sur un fichier mais devez passer à une autre branche pour une tâche urgente. Faites :
     ```bash
     git stash
     ```
   - Après avoir terminé sur l'autre branche, revenez et appliquez la remise :
     ```bash
     git stash apply
     ```

3. **Lister les remises disponibles :**
   ```bash
   git stash list
   ```

---

## Publier sur GitHub

1. **Ajouter un dépôt distant :**
   ```bash
   git remote add origin <url_du_depot>
   ```
   Exemple :
   ```bash
   git remote add origin git@github.com:username/repository.git
   ```

2. **Envoyer les commits au dépôt distant :**
   ```bash
   git push -u origin <nom_de_la_branche>
   ```
   Exemple :
   ```bash
   git push -u origin main
   ```

---

## Annexes

### Générer une clé SSH

1. **Créer une clé SSH :**
   ```bash
   ssh-keygen -t ed25519 -C "votre_email@example.com"
   ```

2. **Copier la clé dans le presse-papier :**
   ```bash
   clip < ~/.ssh/id_ed25519.pub
   ```

3. **Ajouter la clé SSH à GitHub :**
   - Rendez-vous dans les paramètres de GitHub.
   - Ajoutez une nouvelle clé SSH et collez la clé générée.

### Commandes utiles supplémentaires

- **Supprimer une branche localement :**
  ```bash
  git branch -d <nom_de_la_branche>
  ```

- **Supprimer une branche avec des modifications non fusionnées :**
  ```bash
  git branch -D <nom_de_la_branche>
  ```

- **Lister les différences entre fichiers :**
  ```bash
  git diff
  ```

- **Voir l'état du dépôt :**
  ```bash
  git status
  ```
