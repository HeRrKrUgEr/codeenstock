
# LAMP Stack Setup and Laravel Deployment on Ubuntu

## 1. Connect to Your Ubuntu Server

1. **Open your terminal** (or use an SSH client if on Windows).
2. Connect to your server:

   ```bash
   ssh username@your_server_ip
   ```

   Replace `username` with your SSH user and `your_server_ip` with the IP address of your server.

---

## 2. Update the Server

Updating ensures you’re working with the latest packages and security patches.

```bash
sudo apt update && sudo apt upgrade -y
```

---

## 3. Install Apache

Apache is the web server that will handle requests for your Laravel application.

1. **Install Apache**:

   ```bash
   sudo apt install apache2 -y
   ```

2. **Start and Enable Apache**:

   ```bash
   sudo systemctl start apache2
   sudo systemctl enable apache2
   ```

3. **Allow Apache Through the Firewall**:

   ```bash
   sudo ufw allow in "Apache Full"
   ```

---

## 4. Install MySQL

MySQL will manage the database for your Laravel application.

1. **Install MySQL**:

   ```bash
   sudo apt install mysql-server -y
   ```

2. **Secure MySQL**:

   ```bash
   sudo mysql_secure_installation
   ```

   Follow the prompts to secure your MySQL setup, including setting a root password and disabling remote root access.

3. **Create a Database and User for Laravel**:
   - Log into MySQL:

     ```bash
     sudo mysql -u root -p
     ```

   - Inside the MySQL shell:

     ```sql
     CREATE DATABASE laravel_db;
     CREATE USER 'laravel_user'@'localhost' IDENTIFIED BY 'your_strong_password';
     GRANT ALL PRIVILEGES ON laravel_db.* TO 'laravel_user'@'localhost';
     FLUSH PRIVILEGES;
     EXIT;
     ```

   Replace `laravel_db`, `laravel_user`, and `your_strong_password` as desired.

---

## 5. Install PHP and Required Extensions

Laravel requires PHP and specific extensions to function correctly.

1. **Install PHP and Extensions**:

   ```bash
   sudo apt install php libapache2-mod-php php-mysql php-cli php-curl php-zip php-xml php-mbstring php-json -y
   ```

2. **Verify PHP Installation**:

   ```bash
   php -v
   ```

---

## 6. Configure Apache for Laravel

Set up Apache to serve your Laravel application.

1. **Create a Virtual Host for Laravel**:

   ```bash
   sudo nano /etc/apache2/sites-available/laravel.conf
   ```

2. **Add Configuration**:
   Paste the following configuration, modifying it with your domain and file path:

   ```apache
   <VirtualHost *:80>
       ServerName yourdomain.com
       DocumentRoot /var/www/laravel/public

       <Directory /var/www/laravel/public>
           AllowOverride All
           Require all granted
       </Directory>

       ErrorLog ${APACHE_LOG_DIR}/laravel_error.log
       CustomLog ${APACHE_LOG_DIR}/laravel_access.log combined
   </VirtualHost>
   ```

3. **Enable the Site and Rewrite Module**:

   ```bash
   sudo a2ensite laravel.conf
   sudo a2enmod rewrite
   ```

4. **Restart Apache**:

   ```bash
   sudo systemctl restart apache2
   ```

---

## 7. Install Composer

Composer is required to manage Laravel dependencies.

1. **Download and Install Composer**:

   ```bash
   curl -sS https://getcomposer.org/installer -o composer-setup.php
   sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
   ```

2. **Verify Installation**:

   ```bash
   composer --version
   ```

---

## 8. Deploy Laravel

1. **Navigate to the Web Root**:

   ```bash
   cd /var/www
   ```

2. **Clone Your Laravel Project** (or create a new Laravel project):

   ```bash
   sudo git clone https://github.com/your_username/your_laravel_repo.git laravel
   ```

3. **Set Ownership and Permissions**:

   ```bash
   sudo chown -R www-data:www-data /var/www/laravel
   sudo chmod -R 755 /var/www/laravel/storage
   sudo chmod -R 755 /var/www/laravel/bootstrap/cache
   ```

4. **Install Laravel Dependencies**:

   ```bash
   cd /var/www/laravel
   composer install --optimize-autoloader --no-dev
   ```

5. **Create the Environment File**:

   ```bash
   cp .env.example .env
   ```

6. **Generate the Application Key**:

   ```bash
   php artisan key:generate
   ```

7. **Configure the `.env` File**:
   Update `.env` with your database settings:

   ```env
   DB_DATABASE=laravel_db
   DB_USERNAME=laravel_user
   DB_PASSWORD=your_strong_password
   ```

8. **Run Database Migrations**:

   ```bash
   php artisan migrate --force
   ```

9. **Optimize Laravel for Production**:

   ```bash
   php artisan config:cache
   php artisan route:cache
   php artisan view:cache
   ```

---

## 9. Enable SSL with Let’s Encrypt (Optional but Recommended)

1. **Install Certbot** (for Let’s Encrypt):

   ```bash
   sudo apt install certbot python3-certbot-apache -y
   ```

2. **Obtain and Install SSL Certificate**:

   ```bash
   sudo certbot --apache -d yourdomain.com
   ```

   Follow the prompts to complete the SSL setup and enable automatic HTTP to HTTPS redirection.

---

## 10. Set Up File Permissions and Firewall (Final Security)

1. **Secure Permissions**:

   ```bash
   sudo chown -R www-data:www-data /var/www/laravel
   sudo chmod -R 755 /var/www/laravel/storage
   sudo chmod -R 755 /var/www/laravel/bootstrap/cache
   ```

2. **Adjust Firewall Rules**:

   ```bash
   sudo ufw allow 'Apache Full'
   sudo ufw enable
   ```

---

## 11. Test the Laravel Application

Visit `http://yourdomain.com` (or `https://yourdomain.com` if SSL is enabled) in your browser. You should see your Laravel application running. If there are any issues, check the **Apache logs**:

- Error Log: `/var/log/apache2/laravel_error.log`
- Access Log: `/var/log/apache2/laravel_access.log`

---

Your **LAMP stack** on Ubuntu is now fully set up to host your **Laravel application**! Enjoy your new setup.
