
# Compilation d'ImageMagick en tant que PIC (Position Independant Code)

Ce guide fournit des instructions étape par étape pour construire ImageMagick en tant que code indépendant de la position (PIC) pour une utilisation dans des environnements d'hébergement partagé.

## Étapes pour construire ImageMagick en tant que PIC

1. **Installer les dépendances de construction** : Assurez-vous d'avoir les outils de construction nécessaires et les dépendances. Vous pouvez les installer à l'aide de votre gestionnaire de paquets. Par exemple, sur Debian/Ubuntu :

   ```bash
   sudo apt-get update
   sudo apt-get install build-essential
   sudo apt-get install libjpeg-dev libpng-dev libtiff-dev libgif-dev
   ```

2. **Télécharger la source d'ImageMagick** : Obtenez la dernière version d'ImageMagick sur le [site officiel](https://imagemagick.org/script/download.php) ou son [dépôt GitHub](https://github.com/ImageMagick/ImageMagick).

   ```bash
   wget https://download.imagemagick.org/ImageMagick/download/ImageMagick-x.x.x.tar.gz
   tar -xzf ImageMagick-x.x.x.tar.gz
   cd ImageMagick-x.x.x
   ```

3. **Configurer la construction** : Utilisez le script `configure` avec les options appropriées pour activer le PIC. L'option `--enable-shared` est cruciale car elle indique au système de construction de créer des bibliothèques partagées.

   ```bash
   ./configure --enable-shared CFLAGS="-fPIC" CXXFLAGS="-fPIC"
   ```

4. **Construire ImageMagick** : Compilez le code.

   ```bash
   make
   ```

5. **Installer ImageMagick** : Après une construction réussie, installez-le. Vous voudrez peut-être l'installer dans un répertoire spécifique (comme votre répertoire personnel sur l'hébergement partagé) pour éviter les conflits.

   ```bash
   make install
   ```

   Si vous souhaitez l'installer dans votre répertoire personnel (par exemple, `~/imagemagick`), utilisez :

   ```bash
   ./configure --prefix=$HOME/imagemagick --enable-shared CFLAGS="-fPIC" CXXFLAGS="-fPIC"
   make
   make install
   ```

6. **Définir les variables d'environnement** : Si vous avez installé ImageMagick dans votre répertoire personnel, vous devrez peut-être définir vos variables `PATH` et `LD_LIBRARY_PATH`.

   ```bash
   export PATH=$HOME/imagemagick/bin:$PATH
   export LD_LIBRARY_PATH=$HOME/imagemagick/lib:$LD_LIBRARY_PATH
   ```

7. **Vérifier l'installation** : Vérifiez qu'ImageMagick est correctement installé et peut être invoqué.

   ```bash
   convert --version
   ```

## Remarques supplémentaires

- **Limitations de l'hébergement partagé** : Selon votre fournisseur d'hébergement partagé, vous pouvez avoir des restrictions sur ce que vous pouvez installer ou sur la façon dont vous pouvez configurer l'environnement. Vérifiez auprès d'eux si vous rencontrez des problèmes.
- **Chemins des bibliothèques** : Assurez-vous que toutes les applications utilisant ImageMagick peuvent trouver les bibliothèques partagées. Vous devrez peut-être ajuster le chemin de la bibliothèque dans la configuration de votre application.
- **Utiliser un gestionnaire de paquets** : Si vous utilisez un service d'hébergement avec un gestionnaire de paquets comme `apt` ou `yum`, vérifiez si ImageMagick est déjà disponible en tant que paquet. Cela pourrait vous éviter de compiler à partir de la source.

En suivant ces étapes, vous devriez être en mesure de construire et d'utiliser ImageMagick en tant que PIC sur votre environnement d'hébergement partagé. Si vous rencontrez des problèmes spécifiques, n'hésitez pas à demander !
