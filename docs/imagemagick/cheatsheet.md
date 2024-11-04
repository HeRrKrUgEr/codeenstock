
# Cheatsheet d'ImageMagick

Cette cheatsheet contient des fonctions courantes, pratiques et avancées pour l'utilisation d'ImageMagick.

## Commandes de base

- **Conversion d'images :**

  ```bash
  convert image1.jpg image2.png
  ```

- **Redimensionner une image :**

  ```bash
  convert image.jpg -resize 800x600 image_resized.jpg
  ```

- **Rogner une image :**

  ```bash
  convert image.jpg -crop 100x100+10+10 image_cropped.jpg
  ```

- **Ajouter du texte à une image :**

  ```bash
  convert image.jpg -font Arial -pointsize 36 -draw "text 10,50 'Texte ici'" image_text.jpg
  ```

- **Modifier la luminosité :**

  ```bash
  convert image.jpg -brightness-contrast 10x0 image_bright.jpg
  ```

- **Changer le format d'une image :**

  ```bash
  convert image.tiff image.jpg
  ```

## Fonctions courantes

- **Fusionner plusieurs images :**

  ```bash
  convert image1.jpg image2.jpg +append image_merged.jpg  # côte à côte
  convert image1.jpg image2.jpg -append image_merged.jpg  # l'un au-dessus de l'autre
  ```

- **Créer une image GIF animée :**

  ```bash
  convert -delay 20 -loop 0 image1.jpg image2.jpg image3.jpg animation.gif
  ```

- **Appliquer un flou :**

  ```bash
  convert image.jpg -blur 0x8 image_blur.jpg
  ```

- **Convertir des PDF en images :**

  ```bash
  convert -density 300 document.pdf document.png
  ```

## Fonctions avancées

- **Création de miniatures (thumbnails) :**

  ```bash
  convert image.jpg -thumbnail 100x100 thumbnail.jpg
  ```

- **Utiliser des filtres :**

  ```bash
  convert image.jpg -filter Gaussian -resize 800x800 -define filter:support=2.0 image_filtered.jpg
  ```

- **Générer des histogrammes :**

  ```bash
  convert image.jpg -colors 256 -format "%c" histogram:info:
  ```

- **Extraire les métadonnées d'une image :**

  ```bash
  identify -verbose image.jpg
  ```

- **Ajouter une bordure :**

  ```bash
  convert image.jpg -border 10x10 -bordercolor black image_bordered.jpg
  ```

- **Appliquer une rotation :**

  ```bash
  convert image.jpg -rotate 90 image_rotated.jpg
  ```

- **Détecter des bords :**

  ```bash
  convert image.jpg -edge 1 image_edges.jpg
  ```

## Gestion des couleurs

- **Modifier la saturation :**

  ```bash
  convert image.jpg -modulate 100,150,100 image_saturated.jpg
  ```

- **Convertir une image en niveaux de gris :**

  ```bash
  convert image.jpg -colorspace Gray image_gray.jpg
  ```

- **Changer la palette de couleurs :**

  ```bash
  convert image.jpg -colors 16 image_reduced_colors.jpg
  ```

## Utilisation en ligne de commande

- **Pour obtenir de l'aide sur une commande :**

  ```bash
  convert --help
  ```

- **Pour vérifier la version d'ImageMagick :**

  ```bash
  convert --version
  ```

## Notes supplémentaires

- Les commandes peuvent être combinées en utilisant `-exec` pour effectuer plusieurs transformations en une seule ligne.
- Utilisez `mogrify` pour appliquer des modifications directement sur les fichiers d'origine.

Cette cheatsheet est conçue pour être une référence rapide des fonctionnalités d'ImageMagick. N'hésitez pas à l'étendre avec vos propres commandes et astuces au fur et à mesure de votre expérience !
