
# Configuration d'un Stack LAMP et Déploiement de Laravel sur Ubuntu

## 1. Connexion à votre serveur Ubuntu

1. **Ouvrez votre terminal** (ou utilisez un client SSH si vous êtes sous Windows).
2. Connectez-vous à votre serveur :

   ```bash
   ssh username@votre_ip_serveur
   ```

   Remplacez `username` par votre utilisateur SSH et `votre_ip_serveur` par l'adresse IP de votre serveur.

---

## 2. Mise à jour du serveur

Mettez à jour le serveur pour vous assurer d’avoir les derniers paquets et correctifs de sécurité.

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 3. Installer Apache

Apache est le serveur web qui traitera les requêtes pour votre application Laravel.

1. **Installez Apache** :

   ```bash
   sudo apt install apache2 -y
   ```

2. **Démarrez et activez Apache** :

   ```bash
   sudo systemctl start apache2
   sudo systemctl enable apache2
   ```

3. **Autorisez Apache via le pare-feu** :

   ```bash
   sudo ufw allow in "Apache Full"
   ```

---

## 4. Installer MySQL

MySQL gérera la base de données pour votre application Laravel.

1. **Installez MySQL** :

   ```bash
   sudo apt install mysql-server -y
   ```

2. **Sécurisez MySQL** :

   ```bash
   sudo mysql_secure_installation
   ```

   Suivez les invites pour sécuriser votre installation MySQL, y compris la définition d'un mot de passe root et la désactivation de l'accès root à distance.

3. **Créer une base de données et un utilisateur pour Laravel** :
   - Connectez-vous à MySQL :

     ```bash
     sudo mysql -u root -p
     ```

   - Dans le shell MySQL :

     ```sql
     CREATE DATABASE laravel_db;
     CREATE USER 'laravel_user'@'localhost' IDENTIFIED BY 'votre_mot_de_passe_securise';
     GRANT ALL PRIVILEGES ON laravel_db.* TO 'laravel_user'@'localhost';
     FLUSH PRIVILEGES;
     EXIT;
     ```

   Remplacez `laravel_db`, `laravel_user` et `votre_mot_de_passe_securise` selon vos préférences.

---

## 5. Installer PHP et les extensions requises

Laravel nécessite PHP et certaines extensions spécifiques pour fonctionner correctement.

1. **Installez PHP et les extensions** :

   ```bash
   sudo apt install php libapache2-mod-php php-mysql php-cli php-curl php-zip php-xml php-mbstring php-json -y
   ```

2. **Vérifiez l'installation de PHP** :

   ```bash
   php -v
   ```

---

## 6. Configurer Apache pour Laravel

Configurez Apache pour servir votre application Laravel.

1. **Créer un hôte virtuel pour Laravel** :

   ```bash
   sudo nano /etc/apache2/sites-available/laravel.conf
   ```

2. **Ajoutez la configuration** :
   Collez la configuration suivante, en la modifiant avec votre domaine et chemin d'accès :

   ```apache
   <VirtualHost *:80>
       ServerName votredomaine.com
       DocumentRoot /var/www/laravel/public

       <Directory /var/www/laravel/public>
           AllowOverride All
           Require all granted
       </Directory>

       ErrorLog ${APACHE_LOG_DIR}/laravel_error.log
       CustomLog ${APACHE_LOG_DIR}/laravel_access.log combined
   </VirtualHost>
   ```

3. **Activer le site et le module rewrite** :

   ```bash
   sudo a2ensite laravel.conf
   sudo a2enmod rewrite
   ```

4. **Redémarrez Apache** :

   ```bash
   sudo systemctl restart apache2
   ```

---

## 7. Installer Composer

Composer est requis pour gérer les dépendances de Laravel.

1. **Téléchargez et installez Composer** :

   ```bash
   curl -sS https://getcomposer.org/installer -o composer-setup.php
   sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
   ```

2. **Vérifiez l'installation** :

   ```bash
   composer --version
   ```

---

## 8. Déployer Laravel

1. **Accédez au répertoire racine web** :

   ```bash
   cd /var/www
   ```

2. **Clonez votre projet Laravel** (ou créez un nouveau projet Laravel) :

   ```bash
   sudo git clone https://github.com/votre_nom_utilisateur/votre_repo_laravel.git laravel
   ```

3. **Définir les permissions et la propriété** :

   ```bash
   sudo chown -R www-data:www-data /var/www/laravel
   sudo chmod -R 755 /var/www/laravel/storage
   sudo chmod -R 755 /var/www/laravel/bootstrap/cache
   ```

4. **Installer les dépendances Laravel** :

   ```bash
   cd /var/www/laravel
   composer install --optimize-autoloader --no-dev
   ```

5. **Créer le fichier d'environnement** :

   ```bash
   cp .env.example .env
   ```

6. **Générer la clé d'application** :

   ```bash
   php artisan key:generate
   ```

7. **Configurer le fichier `.env`** :
   Mettez à jour `.env` avec les paramètres de votre base de données :

   ```env
   DB_DATABASE=laravel_db
   DB_USERNAME=laravel_user
   DB_PASSWORD=votre_mot_de_passe_securise
   ```

8. **Lancer les migrations de base de données** :

   ```bash
   php artisan migrate --force
   ```

9. **Optimiser Laravel pour la production** :

   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

---

## 9. Activer SSL avec Let’s Encrypt (Optionnel mais recommandé)

1. **Installez Certbot** (pour Let’s Encrypt) :

   ```bash
   sudo apt install certbot python3-certbot-apache -y
   ```

2. **Obtenez et installez le certificat SSL** :

   ```bash
   sudo certbot --apache -d votredomaine.com
   ```

   Suivez les invites pour finaliser la configuration SSL et activer la redirection HTTP vers HTTPS.

---

## 10. Configurer les permissions et le pare-feu (sécurité finale)

1. **Sécurisez les permissions** :

   ```bash
   sudo chown -R www-data:www-data /var/www/laravel
   sudo chmod -R 755 /var/www/laravel/storage
   sudo chmod -R 755 /var/www/laravel/bootstrap/cache
   ```

2. **Ajustez les règles du pare-feu** :

   ```bash
   sudo ufw allow 'Apache Full'
   sudo ufw enable
   ```

---

## 11. Testez l'application Laravel

Visitez `http://votredomaine.com` (ou `https://votredomaine.com` si SSL est activé) dans votre navigateur. Vous devriez voir votre application Laravel en fonctionnement. En cas de problèmes, consultez les **logs Apache** :

- Log d'erreurs : `/var/log/apache2/laravel_error.log`
- Log d'accès : `/var/log/apache2/laravel_access.log`

---

Votre **stack LAMP** sur Ubuntu est maintenant entièrement configurée pour héberger votre **application Laravel** ! Profitez de votre nouvelle configuration.
