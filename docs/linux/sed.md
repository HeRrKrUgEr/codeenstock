# Cheatsheet sur la Commande `sed`

La commande `sed` (Stream Editor) est un éditeur de texte non interactif très puissant. Elle permet de manipuler et transformer du texte dans un fichier ou un flux. Voici un guide complet sur `sed` avec des options, des exemples, et des explications en français.

## Introduction à `sed`

`sed` permet de lire des fichiers ligne par ligne, de les traiter selon des instructions et de les afficher en sortie ou les enregistrer dans un fichier. Il est très couramment utilisé pour effectuer des remplacements de texte, des suppressions de lignes, des insertions et des transformations.

### Syntaxe de Base

```bash
sed [OPTIONS] 'SCRIPT' fichier
```

### Exemple de Base

```bash
sed 's/ancien/nouveau/' fichier.txt
```

Cet exemple remplace la première occurrence de "ancien" par "nouveau" dans chaque ligne de `fichier.txt`.

## Options Courantes de `sed`

- `-e` : Permet de spécifier plusieurs commandes `sed` à exécuter.
- `-i` : Modifie le fichier en place (sans créer de fichier temporaire).
- `-n` : Empêche l'affichage automatique des lignes en sortie (utile avec `p` pour contrôler l'affichage).
- `-r` : Utilise les expressions régulières étendues (compatible avec `ERE`).
- `-f` : Lit les commandes `sed` depuis un fichier.

## Commandes Utilisées dans `sed`

### 1. Remplacer du Texte (`s`)

La commande `s` est la plus utilisée avec `sed` pour effectuer des remplacements.

#### Syntaxe

```bash
sed 's/ancien/nouveau/' fichier.txt
```

- `s` : Indique qu'on souhaite remplacer du texte.
- `ancien` : Le texte ou motif à remplacer.
- `nouveau` : Le texte de remplacement.

#### Exemples

```bash
sed 's/chat/chien/' fichier.txt       # Remplace la première occurrence de "chat" par "chien"
sed 's/chat/chien/g' fichier.txt     # Remplace toutes les occurrences de "chat" par "chien"
sed 's/chat/chien/2' fichier.txt     # Remplace la deuxième occurrence de "chat" dans chaque ligne
```

### 2. Suppression de Lignes (`d`)

La commande `d` est utilisée pour supprimer des lignes spécifiques.

#### Syntaxe

```bash
sed 'NUMd' fichier.txt
```

- `NUM` : Le numéro de la ligne à supprimer.

#### Exemples

```bash
sed '3d' fichier.txt                # Supprime la troisième ligne du fichier
sed '2,5d' fichier.txt              # Supprime les lignes de 2 à 5
sed '/motif/d' fichier.txt          # Supprime toutes les lignes contenant "motif"
```

### 3. Afficher des Lignes (`p`)

La commande `p` est utilisée pour afficher des lignes spécifiques. Utilisée avec l'option `-n`, elle contrôle l'affichage des lignes.

#### Syntaxe

```bash
sed -n '/motif/p' fichier.txt
```

- `-n` : Empêche l'affichage par défaut de toutes les lignes.
- `/motif/p` : Affiche uniquement les lignes qui correspondent au motif.

#### Exemples

```bash
sed -n '1,3p' fichier.txt           # Affiche uniquement les lignes 1 à 3
sed -n '/chat/p' fichier.txt        # Affiche uniquement les lignes contenant "chat"
```

### 4. Insertion et Ajout de Lignes (`i` et `a`)

La commande `i` insère une ligne avant la ligne spécifiée, tandis que `a` ajoute une ligne après la ligne spécifiée.

#### Syntaxe

```bash
sed 'NUMi\texte' fichier.txt       # Insère du texte avant la ligne NUM
sed 'NUMa\texte' fichier.txt       # Ajoute du texte après la ligne NUM
```

#### Exemples

```bash
sed '2i\Nouvelle ligne' fichier.txt # Insère "Nouvelle ligne" avant la ligne 2
sed '4a\Texte ajouté' fichier.txt   # Ajoute "Texte ajouté" après la ligne 4
```

### 5. Remplacer sur une Plage de Lignes

Il est possible d'appliquer un remplacement sur une plage spécifique de lignes.

#### Syntaxe

```bash
sed '3,6s/ancien/nouveau/' fichier.txt
```

- `3,6` : Plage des lignes 3 à 6.

#### Exemple

```bash
sed '1,5s/chien/chat/' fichier.txt   # Remplace "chien" par "chat" uniquement dans les lignes 1 à 5
```

### 6. Modifier des Fichiers en Place (`-i`)

L'option `-i` modifie le fichier en place, ce qui signifie que les changements sont directement enregistrés dans le fichier d'origine.

#### Syntaxe

```bash
sed -i 's/ancien/nouveau/' fichier.txt
```

#### Exemple

```bash
sed -i 's/erreur/correction/g' fichier.txt # Remplace "erreur" par "correction" dans le fichier original
```

### 7. Expressions Régulières Étendues (`-r`)

L'option `-r` permet d'utiliser des expressions régulières étendues (ERE).

#### Syntaxe

```bash
sed -r 's/(motif1|motif2)/nouveau/' fichier.txt
```

#### Exemple

```bash
sed -r 's/(chat|chien)/animal/' fichier.txt # Remplace "chat" ou "chien" par "animal"
```

## Caractères Spéciaux dans `sed`

- `^` : Début de la ligne.
- `$` : Fin de la ligne.
- `.` : Correspond à n'importe quel caractère.
- `*` : Correspond à zéro ou plusieurs répétitions du caractère précédent.
- `[]` : Classe de caractères, ex: `[a-z]` pour les lettres minuscules.
- `\` : Caractère d'échappement pour utiliser des caractères spéciaux.

## Utilisation Avancée de `sed`

### 1. Suppression des Espaces en Début et Fin de Ligne

```bash
sed 's/^ *//;s/ *$//' fichier.txt
```

Cet exemple supprime les espaces en début (`^ *`) et en fin (`*$`) de chaque ligne du fichier.

### 2. Remplacement Multiligne

Pour remplacer un motif qui s'étend sur plusieurs lignes, `sed` peut être utilisé avec des astuces comme l'utilisation de `N` pour joindre des lignes.

#### Exemple

```bash
sed ':a;N;$!ba;s/\n//g' fichier.txt
```

Cet exemple joint toutes les lignes du fichier en une seule en supprimant les sauts de ligne (`\n`).

## Utilisation de Fichiers de Commandes avec `-f`

Il est possible de stocker des commandes `sed` dans un fichier et de les exécuter toutes à la fois.

#### Exemple

- Créez un fichier de commandes `commands.sed` :

  ```
  s/ancien/nouveau/
  /motif/d
  ```

- Exécutez `sed` avec le fichier de commandes :

  ```bash
  sed -f commands.sed fichier.txt
  ```

## Conclusion

`sed` est un outil extrêmement puissant pour manipuler le texte directement depuis la ligne de commande. Il est particulièrement utile pour les scripts d'automatisation et les tâches de traitement de fichiers. Avec ces exemples, vous avez maintenant une base solide pour utiliser `sed` de manière efficace dans vos projets quotidiens.
