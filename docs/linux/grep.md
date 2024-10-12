# Cheatsheet sur la Commande `grep`

La commande `grep` est un outil puissant pour rechercher des motifs dans des fichiers ou des flux de texte. Elle permet de filtrer des lignes en fonction de critères, comme des expressions régulières. Voici un guide complet sur `grep` avec des options, des exemples, et des explications en français.

## Introduction à `grep`

`grep` est utilisé pour rechercher des lignes qui correspondent à un motif spécifique, que ce soit un mot, une phrase, ou une expression régulière. Il est couramment utilisé pour analyser des fichiers log, extraire des informations spécifiques, ou vérifier la présence d'une certaine chaîne de caractères.

### Syntaxe de Base
```bash
grep [OPTIONS] 'MOTIF' fichier
```

### Exemple de Base
```bash
grep 'erreur' journal.txt
```
Cet exemple recherche toutes les lignes contenant le mot "erreur" dans le fichier `journal.txt`.

## Options Courantes de `grep`

- `-i` : Ignore la casse (majuscule/minuscule).
- `-r` ou `-R` : Recherche récursive dans les sous-répertoires.
- `-l` : Affiche uniquement les noms de fichiers contenant le motif.
- `-v` : Inverse la correspondance et affiche les lignes qui **ne** contiennent **pas** le motif.
- `-n` : Affiche le numéro des lignes qui correspondent.
- `-c` : Compte le nombre de lignes qui correspondent.
- `-w` : Correspond uniquement à des mots entiers.
- `-A` et `-B` : Affiche des lignes supplémentaires avant ou après la ligne correspondante.

## Exemples d'Utilisation de `grep`

### 1. Recherche d'un Motif Simple
```bash
grep 'texte' fichier.txt
```
Cet exemple recherche toutes les lignes contenant "texte" dans le fichier `fichier.txt`.

### 2. Recherche Insensible à la Casse (`-i`)
```bash
grep -i 'texte' fichier.txt
```
Avec l'option `-i`, `grep` recherche "texte", peu importe si le texte est en majuscules ou en minuscules.

### 3. Recherche Récursive dans un Répertoire (`-r`)
```bash
grep -r 'erreur' /var/log
```
Cet exemple recherche récursivement le mot "erreur" dans tous les fichiers du répertoire `/var/log`.

### 4. Affichage des Noms de Fichiers Uniquement (`-l`)
```bash
grep -l 'erreur' *.log
```
L'option `-l` fait en sorte que `grep` n'affiche que les noms des fichiers contenant le motif "erreur".

### 5. Inverser la Correspondance (`-v`)
```bash
grep -v 'avertissement' journal.txt
```
L'option `-v` permet d'afficher toutes les lignes qui **ne** contiennent **pas** le mot "avertissement".

### 6. Affichage des Numéros de Ligne (`-n`)
```bash
grep -n 'texte' fichier.txt
```
Avec l'option `-n`, `grep` affiche le numéro de chaque ligne qui correspond au motif "texte".

### 7. Compter le Nombre de Correspondances (`-c`)
```bash
grep -c 'erreur' journal.txt
```
L'option `-c` permet de compter le nombre de lignes contenant "erreur" dans `journal.txt`.

### 8. Recherche de Mots Entiers (`-w`)
```bash
grep -w 'mot' fichier.txt
```
Avec l'option `-w`, `grep` correspond uniquement aux mots entiers, évitant ainsi de correspondre à des sous-chaînes.

### 9. Afficher les Lignes Autour du Motif (`-A` et `-B`)
- `-A NUM` : Affiche NUM lignes après chaque correspondance.
- `-B NUM` : Affiche NUM lignes avant chaque correspondance.

#### Exemple
```bash
grep -A 2 -B 2 'erreur' journal.txt
```
Cet exemple affiche 2 lignes avant et après chaque ligne contenant "erreur".

## Expressions Régulières avec `grep`

`grep` supporte les expressions régulières pour des recherches avancées.

### Caractères Spéciaux
- `^` : Début de la ligne.
- `$` : Fin de la ligne.
- `.` : Correspond à n'importe quel caractère.
- `*` : Correspond à zéro ou plusieurs répétitions du caractère précédent.
- `[abc]` : Classe de caractères (correspond à `a`, `b`, ou `c`).
- `\` : Caractère d'échappement.

### Exemples d'Utilisation des Expressions Régulières

#### 1. Correspondance au Début de Ligne
```bash
grep '^Erreur' fichier.txt
```
Cet exemple correspond à toutes les lignes qui commencent par "Erreur".

#### 2. Correspondance à la Fin de Ligne
```bash
grep 'fin$' fichier.txt
```
Cet exemple correspond à toutes les lignes qui se terminent par "fin".

#### 3. Utilisation de Classes de Caractères
```bash
grep '[0-9]' fichier.txt
```
Cet exemple recherche toutes les lignes contenant un chiffre (de `0` à `9`).

## Utilisation Avancée de `grep`

### 1. Recherche de Correspondances Multiples
```bash
grep -E 'erreur|avertissement' fichier.txt
```
L'option `-E` permet d'utiliser des expressions régulières étendues, équivalentes à `egrep`. Cet exemple recherche les lignes contenant "erreur" ou "avertissement".

### 2. Ignorer les Fichiers Binaires
```bash
grep --binary-files=without-match 'texte' *
```
Cet exemple ignore les fichiers binaires lors de la recherche.

### 3. Limiter la Profondeur de Recherche Récursive
```bash
grep -r --max-depth=2 'texte' /chemin/dossier
```
Cet exemple limite la recherche à une profondeur de 2 répertoires lors de l'utilisation de la recherche récursive.

## Combinaison avec d'Autres Commandes

`grep` est souvent utilisé en combinaison avec d'autres commandes via des pipes (`|`) pour filtrer des sorties.

### 1. Utilisation avec `ps` pour Filtrer les Processus
```bash
ps aux | grep 'apache'
```
Cet exemple filtre les processus liés à "apache" parmi tous les processus en cours d'exécution.

### 2. Utilisation avec `ls` pour Filtrer des Fichiers
```bash
ls -l | grep '^d'
```
Cet exemple affiche uniquement les répertoires (`^d` indique que la ligne commence par `d`, caractéristique des répertoires).

## Conclusion

`grep` est un outil indispensable pour tous ceux qui travaillent régulièrement avec la ligne de commande. Que vous cherchiez à analyser des fichiers log, à filtrer des sorties, ou à extraire des informations spécifiques, `grep` est extrêmement polyvalent et puissant. En utilisant les options et les expressions régulières, vous pouvez effectuer des recherches très précises et automatiser des tâches de manière efficace.
