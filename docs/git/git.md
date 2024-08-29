# Commandes Git les plus utiles

Git est un système de contrôle de version distribué, utilisé pour gérer les versions de code source. Voici une liste des commandes Git les plus couramment utilisées, avec des explications simples.

## Initialisation et Configuration

- `git init`  
  Initialise un nouveau dépôt Git local.

- `git clone <url>`  
  Clone un dépôt distant vers le répertoire local.

- `git config --global user.name "Votre Nom"`  
  Configure le nom d'utilisateur global pour Git.

- `git config --global user.email "votre_email@example.com"`  
  Configure l'adresse e-mail globale pour Git.

## Gestion des Modifications

- `git status`  
  Affiche l'état actuel du dépôt, y compris les modifications non suivies, suivies et les fichiers non suivis.

- `git add <fichier>`  
  Ajoute un fichier spécifique à l'index (staging area).

- `git add .`  
  Ajoute tous les fichiers modifiés à l'index.

- `git commit -m "Message de commit"`  
  Enregistre les modifications dans le dépôt avec un message de commit.

- `git commit -a -m "Message de commit"`  
  Ajoute et commite tous les fichiers modifiés et suivis.

## Historique et Journal

- `git log`  
  Affiche l'historique des commits.

- `git log --oneline`  
  Affiche l'historique des commits dans un format compact.

- `git diff`  
  Montre les différences entre les modifications non commitées et le dernier commit.

- `git diff --staged`  
  Montre les différences entre les fichiers indexés et le dernier commit.

## Branches

- `git branch`  
  Liste toutes les branches locales.

- `git branch <nom_branche>`  
  Crée une nouvelle branche.

- `git checkout <nom_branche>`  
  Bascule vers une branche existante.

- `git checkout -b <nom_branche>`  
  Crée et bascule vers une nouvelle branche.

- `git merge <nom_branche>`  
  Fusionne la branche spécifiée avec la branche actuelle.

- `git branch -d <nom_branche>`  
  Supprime une branche.

## Réinitialisation et Annulation

- `git reset <fichier>`  
  Annule les modifications dans l'index pour un fichier.

- `git reset --hard`  
  Réinitialise l'index et l'arborescence de travail au dernier commit.

- `git revert <commit>`  
  Annule un commit en créant un nouveau commit.

## Remotes (Dépôts Distants)

- `git remote add origin <url>`  
  Ajoute un dépôt distant nommé "origin".

- `git remote -v`  
  Affiche les dépôts distants configurés.

- `git push origin <nom_branche>`  
  Envoie les commits de la branche locale vers le dépôt distant.

- `git pull origin <nom_branche>`  
  Récupère les modifications du dépôt distant et les fusionne avec la branche locale.

## Tags

- `git tag <nom_tag>`  
  Crée un tag pour marquer un point dans l'historique des commits.

- `git push origin <nom_tag>`  
  Envoie un tag spécifique vers le dépôt distant.

## Nettoyage

- `git clean -f`  
  Supprime les fichiers non suivis dans le répertoire de travail.

- `git gc`  
  Optimise la base de données des objets Git pour économiser de l'espace.

## Autres Commandes Utiles

- `git stash`  
  Sauvegarde les modifications actuelles sans les commiter.

- `git stash apply`  
  Applique les modifications sauvegardées précédemment.

- `git fetch`  
  Récupère les modifications du dépôt distant sans les fusionner.

- `git rebase <nom_branche>`  
  Applique les commits de la branche actuelle par-dessus une autre branche.

---

Ces commandes Git couvrent les opérations de base et avancées pour gérer les versions de code. Utilisez cette cheatsheet comme référence rapide pour vos projets Git.
