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

4. **Vérifier les configurations actuelles :**
   ```bash
   git config --list
   ```
   Cette commande affiche toutes les configurations actuelles pour votre environnement Git.

---

## Initialiser un dépôt Git

1. **Initialiser un dépôt local :**
   ```bash
   git init
   ```
   Cette commande crée un nouveau dépôt Git dans le dossier courant. Un répertoire caché `.git` est créé pour stocker toutes les informations relatives au dépôt.

2. **Cloner un dépôt existant :**
   ```bash
   git clone <url_du_dépôt>
   ```
   Par exemple :
   ```bash
   git clone https://github.com/nom-utilisateur/nom-du-repo.git
   ```
   Cela télécharge le dépôt et son historique dans un nouveau dossier local.

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

3. **Vérifier l'état actuel du dépôt :**
   ```bash
   git status
   ```
   Cette commande liste les fichiers modifiés, ceux en attente d'ajout et ceux déjà dans l'index.

4. **Vérifier les différences dans les fichiers :**
   ```bash
   git diff
   ```
   Cela montre les différences non encore ajoutées entre les fichiers modifiés et la dernière version dans Git.

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

5. **Supprimer une branche :**
   ```bash
   git branch -d <nom_de_la_branche>
   ```
   Cela supprime une branche déjà fusionnée.

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

2. **Résolution des conflits :**
   En cas de conflit, Git vous demandera de résoudre les conflits manuellement avant de finaliser la fusion. Vous devrez ouvrir les fichiers concernés, résoudre les conflits, puis effectuer un commit :
   ```bash
   git add <fichier_conflit>
   git commit -m "Résolution des conflits"
   ```

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

3. **Annuler un commit avec `git revert` :**
   ```bash
   git revert <hash_du_commit>
   ```
   Cette commande crée un nouveau commit qui annule les modifications introduites par un commit précédent, sans modifier l'historique. Par exemple :
   ```bash
   git revert a1b2c3d
   ```

4. **Réinitialiser l'état avec `git reset` :**
   - **Réinitialiser seulement la zone de staging :**
     ```bash
     git reset <nom_du_fichier>
     ```
     Cela retire un fichier de la zone de staging tout en gardant les modifications dans le dossier de travail.
   - **Réinitialiser un commit et garder les modifications :**
     ```bash
     git reset --soft <hash_du_commit>
     ```
     Cela déplace l'état du dépôt à un commit précédent sans affecter les fichiers modifiés.
   - **Réinitialiser un commit et supprimer les modifications :**
     ```bash
     git reset --hard <hash_du_commit>
     ```
     Cela restaure complètement l'état du dépôt (fichiers et historique) à un commit donné.

---

## Suivi et récupération des modifications

1. **Voir l'historique des actions (reflog) :**
   ```bash
   git reflog
   ```
   Cela affiche toutes les actions effectuées dans le dépôt, y compris les changements de branche, les resets, les merges, etc.

2. **Mettre de côté des modifications avec `git stash` :**
   ```bash
   git stash
   ```
   Cela enregistre temporairement les modifications non commit pour nettoyer l'espace de travail.
   - **Récupérer les modifications mises de côté :**
     ```bash
     git stash pop
     ```
     Cette commande restaure les modifications mises de côté et les retire de la liste de stash.

3. **Afficher la liste des stashs :**
   ```bash
   git stash list
   ```

---

## Travailler avec GitHub

1. **Lier un dépôt local à un dépôt distant :**
   ```bash
   git remote add origin <url_du_dépôt>
   ```
   Exemple :
   ```bash
   git remote add origin https://github.com/nom-utilisateur/nom-du-repo.git
   ```

2. **Pousser les modifications vers le dépôt distant :**
   ```bash
   git push -u origin <nom_de_la_branche>
   ```
   Cela envoie vos commits locaux au dépôt distant. Par exemple :
   ```bash
   git push -u origin main
   ```

3. **Récupérer les modifications du dépôt distant :**
   ```bash
   git pull origin <nom_de_la_branche>
   ```
   Cela synchronise les changements distants avec votre dépôt local.

4. **Cloner un dépôt existant :**
   ```bash
   git clone <url_du_dépôt>
   ```
   Exemple :
   ```bash
   git clone https://github.com/nom-utilisateur/nom-du-repo.git
   ```

---

## Bonnes pratiques

1. **Utiliser des messages de commit clairs et significatifs :**
   Chaque message de commit doit décrire brièvement les changements effectués.

2. **Travailler avec des branches pour des fonctionnalités spécifiques :**
   Créez une nouvelle branche pour chaque nouvelle fonctionnalité ou correction de bug.

3. **Effectuer des revues de code avant de fusionner :**
   Travaillez en équipe pour valider les modifications avant de les intégrer à la branche principale.

---

## Ressources supplémentaires

- [Documentation officielle de Git](https://git-scm.com/doc)
- [Guide GitHub](https://docs.github.com)
- [Try Git](https://try.github.io) - Un tutoriel interactif pour apprendre les bases de Git.

---

Avec ces commandes et bonnes pratiques, vous êtes prêt à gérer vos projets avec Git et GitHub efficacement. Bonne gestion de versions !
