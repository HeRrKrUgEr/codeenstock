# Authentification Git pour GitHub

Pour pousser du code vers un dépôt distant sur GitHub, il faut s'authentifier. Voici les méthodes les plus courantes :

## 1. Authentification avec HTTPS et un Token d'Accès Personnel

1. **Générer un Token d'Accès Personnel** :

   - Connectez-vous à GitHub.
   - Allez dans **Settings** > **Developer settings** > **Personal access tokens**.
   - Cliquez sur **Tokens (classic)** et **Generate new token**.
   - Sélectionnez les permissions nécessaires, comme `repo`.

2. **Utiliser le Token** :

   - Lors de l'utilisation de `git push`, entrez votre nom d'utilisateur GitHub.
   - Utilisez le token comme mot de passe.

3. **Configurer Git pour Mémoriser le Token** :

   ```bash
   git config --global credential.helper cache
   ```
