# Gestionnaire de Versions avec Git et GitHub

---

## **Introduction**
Un gestionnaire de versions est un outil essentiel pour les développeurs. Il permet de :
- Suivre l'évolution des fichiers étape par étape.
- Revenir à une version précédente en cas de problème.
- Travailler en équipe sans conflit grâce à un historique clair des modifications.

**Exemple d'outil : Git**  
Git est un gestionnaire de versions décentralisé. Chaque copie d'un projet devient un dépôt contenant l'historique complet des modifications.

**Différence entre Git et GitHub** :
- **Git** : Logiciel local pour gérer les versions.
- **GitHub** : Plateforme en ligne pour héberger et collaborer sur des projets.

---

## **Fonctionnalités Principales**
1. **Initialisation d’un dépôt** :
   - Commande : `git init`
   - Crée un dossier caché `.git` contenant la configuration et l’historique.

2. **Ajout de fichiers au suivi** :
   - Commande : `git add <fichier>`
   - Déplace les fichiers modifiés dans la zone de staging.

3. **Enregistrement des versions** :
   - Commande : `git commit -m "message"`
   - Crée une nouvelle version dans le repository.

4. **Historique des modifications** :
   - Commande : `git log`
   - Affiche l'historique des commits.

5. **Collaboration avec des dépôts distants** :
   - Associer un dépôt distant : `git remote add origin <lien>`
   - Envoyer des modifications : `git push -u origin main`

---

## **Configurer Git**
1. **Identité** :
   ```bash
   git config --global user.name "John Doe"
   git config --global user.email johndoe@example.com
   ```

2. **Couleurs** :
   ```bash
   git config --global color.diff auto
   git config --global color.status auto
   git config --global color.branch auto
   ```

3. **Éditeur** :
   ```bash
   git config --global core.editor notepad++
   ```

---

## **Fonctionnement Git & GitHub**

### **Clé SSH pour connexion sécurisée**
1. **Générer une clé SSH** :
   ```bash
   ssh-keygen -t ed25519 -C "votre.email@example.com"
   ```
2. **Ajouter la clé à GitHub** :
   - Copier la clé publique : `clip < ~/.ssh/id_ed25519.pub`
   - Aller dans les paramètres GitHub et ajouter la clé.

3. **Associer un dépôt distant** :
   ```bash
   git remote add origin git@github.com:<nom-utilisateur>/<nom-repo>.git
   ```

### **Branches**
Les branches permettent de travailler sur différentes fonctionnalités sans affecter le code principal :
- **Créer une branche** : `git branch <nom-branche>`
- **Changer de branche** : `git checkout <nom-branche>`
- **Fusionner des branches** : `git merge <nom-branche>`

---

## **Commandes Avancées**
1. **Pull Request** : Demander la fusion de vos changements sur GitHub.
2. **Supprimer une branche** :
   - Avec validation : `git branch -d <nom-branche>`
   - Forcé : `git branch -D <nom-branche>`
3. **Stash (remise)** :
   - Sauvegarder des modifications : `git stash`
   - Voir la liste des remises : `git stash list`
   - Appliquer une remise : `git stash apply`

---

## **Protocoles Git**
1. **HTTPS** : Simple mais demande des identifications fréquentes.
2. **SSH** : Utilise des clés pour une connexion sécurisée et simplifiée.

---

## **Conclusion**
Git et GitHub sont des outils puissants pour gérer, collaborer et versionner vos projets. Avec ce guide, vous avez une base solide pour explorer ces technologies et travailler efficacement en équipe.
