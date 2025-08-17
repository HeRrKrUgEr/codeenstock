
# CodeEnStock Documentation Website

Bienvenue sur le site de documentation plangeek, conçu pour offrir des guides rapides et des cheatsheets pour divers langages de programmation et technologies.

Accédez au site ici : [Plangeek Documentation Website](https://www.codeenstock.com)

## Table des Matières

- [Introduction](#introduction)
- [Comment Naviguer sur le Site](#comment-naviguer-sur-le-site)
- [Comment Contribuer](#comment-contribuer)
- [Installation et Configuration de MkDocs](#installation-et-configuration-de-mkdocs)
- [Déploiement](#déploiement)

## Introduction

Le site plangeek utilise **MkDocs**, un générateur de site statique simple à utiliser, basé sur Markdown. Il est conçu pour faciliter la création et la mise à jour de documentations techniques, avec un focus sur la simplicité et l'efficacité.

## Comment Naviguer sur le Site

1. **Page d'Accueil** : La page d'accueil contient une liste de liens vers différentes sections de la documentation, telles que les langages de programmation (Python, JavaScript, etc.) et les outils (Git, Docker, etc.).

2. **Sections** : Chaque section correspond à un langage de programmation ou un outil particulier. Cliquez sur un lien pour accéder à la cheatsheet ou au guide rapide correspondant.

3. **Sous-liens** : Certaines sections peuvent contenir des sous-liens pour organiser le contenu de manière hiérarchique. Par exemple, une section sur les langages de programmation peut avoir des sous-liens pour chaque langage.

4. **Recherche** : Utilisez la barre de recherche en haut de la page pour trouver rapidement des commandes ou des sujets spécifiques.

## Comment Contribuer

Pour ajouter ou mettre à jour des documentations, suivez ces étapes :

1. **Clonez le dépôt** : Clonez le dépôt GitHub du site plangeek sur votre machine locale :
   ```bash
   git clone https://github.com/votre-utilisateur/plangeek.git
   ```

2. **Ajouter du Contenu** : Ajoutez ou modifiez des fichiers Markdown (`.md`) dans le dossier `docs`. Chaque fichier représente une page de documentation.

3. **Mettre à jour la Navigation** : Mettez à jour le fichier `mkdocs.yml` pour ajouter des liens vers les nouvelles pages ou sections :
   ```yaml
   nav:
     - Accueil: index.md
     - Langages de Programmation:
         - Python: programmation/python.md
         - JavaScript: programmation/javascript.md
     - Outils:
         - Git: outils/git.md
         - Docker: outils/docker.md
   ```

4. **Commit et Push** : Une fois les modifications terminées, committez et poussez les changements :
   ```bash
   git add .
   git commit -m "Ajout d'une nouvelle section de documentation"
   git push origin main
   ```

## Installation et Configuration de MkDocs

Pour travailler sur le site plangeek localement, suivez ces étapes pour installer MkDocs :

1. **Installer MkDocs** :
   ```bash
   pip install mkdocs
   ```

2. **Démarrer le Serveur Local** : Pour visualiser les modifications localement, démarrez le serveur MkDocs :
   ```bash
   mkdocs serve
   ```
   Accédez à `http://127.0.0.1:8000/` dans votre navigateur pour voir le site.

## Déploiement

Le site plangeek est déployé automatiquement sur GitHub Pages grâce à GitHub Actions. Chaque fois que vous poussez des changements vers la branche principale, le site est reconstruit et déployé.

1. **Build le Site** : Si vous souhaitez construire le site manuellement :
   ```bash
   mkdocs build
   ```

2. **Déployer sur GitHub Pages** :
   ```bash
   mkdocs gh-deploy
   ```

---

Ce site de documentation est conçu pour être simple à utiliser et à maintenir. N'hésitez pas à contribuer et à améliorer les documentations pour aider la communauté CodeEnStock !

Accédez au site CodeEnStock ici : [Plangeek Documentation Website](https://www.codeenstock.com)
