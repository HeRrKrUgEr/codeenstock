# Fiche de Référence pour Vi et Vim

## Modes de Base

- **Mode Normal** : Appuyez sur `Esc` pour entrer dans ce mode (par défaut).
- **Mode Insertion** : Appuyez sur `i` pour insérer avant le curseur ou `a` pour insérer après le curseur.
- **Mode Commande** : Appuyez sur `:` pour entrer en mode commande (sauvegarder, quitter, etc.).

## Commandes de Base

- `i` – Insérer avant le curseur.
- `a` – Ajouter après le curseur.
- `o` – Ouvrir une nouvelle ligne en dessous.
- `Esc` – Revenir en mode Normal.
- `:w` – Sauvegarder le fichier.
- `:q` – Quitter Vim.
- `:wq` – Sauvegarder et quitter.
- `:q!` – Quitter sans sauvegarder.
- `u` – Annuler la dernière action.
- `Ctrl + r` – Refaire l'action annulée.

## Navigation

- `h` – Aller à gauche.
- `j` – Aller en bas.
- `k` – Aller en haut.
- `l` – Aller à droite.
- `gg` – Aller au début du fichier.
- `G` – Aller à la fin du fichier.
- `0` – Aller au début de la ligne.
- `$` – Aller à la fin de la ligne.
- `w` – Aller au début du mot suivant.
- `b` – Aller au début du mot précédent.
- `Ctrl + f` – Avancer d'une page.
- `Ctrl + b` – Reculer d'une page.

## Édition

- `x` – Supprimer le caractère sous le curseur.
- `dw` – Supprimer le mot sous le curseur.
- `dd` – Supprimer la ligne actuelle.
- `yy` – Copier la ligne actuelle.
- `p` – Coller après le curseur.
- `r` – Remplacer un seul caractère.
- `ciw` – Changer un mot (supprimer le mot et entrer en mode insertion).
- `A` – Ajouter à la fin de la ligne.

## Recherche

- `/mot` – Rechercher `mot` dans le fichier.
- `n` – Aller à la correspondance suivante.
- `N` – Aller à la correspondance précédente.
- `:%s/ancien/nouveau/g` – Remplacer tous les `ancien` par `nouveau` dans le fichier.

## Mode Visuel

- `v` – Commencer le mode visuel (sélectionner du texte).
- `V` – Commencer le mode visuel ligne.
- `Ctrl + v` – Commencer le mode visuel bloc.
- `y` – Copier la sélection.
- `d` – Supprimer la sélection.

## Sujets Avancés

### Buffers

- `:ls` – Lister tous les buffers ouverts.
- `:b [nom/numéro]` – Changer de buffer par nom ou numéro.
- `:bd` – Fermer un buffer.

### Splits

- `:split` – Diviser l'écran horizontalement.
- `:vsplit` – Diviser l'écran verticalement.
- `Ctrl + w + w` – Naviguer entre les splits.
- `:q` – Fermer un split.

### Onglets

- `:tabnew` – Ouvrir un nouvel onglet.
- `:tabn` – Passer à l'onglet suivant.
- `:tabp` – Revenir à l'onglet précédent.
- `:tabclose` – Fermer l'onglet courant.

### Marques

- `ma` – Placer une marque `a` à la position actuelle du curseur.
- `` `a` `` – Aller à la marque `a`.
- `d` `` `a`` – Supprimer jusqu'à la marque `a`.

### Registres

- `"aY` – Copier dans le registre `a`.
- `"ap` – Coller à partir du registre `a`.
- `:reg` – Voir le contenu de tous les registres.

### Macros

- `qa` – Enregistrer une macro dans le registre `a`.
- `q` – Arrêter l'enregistrement de la macro.
- `@a` – Exécuter la macro stockée dans le registre `a`.

### Quitter

- `:w` – Sauvegarder les modifications.
- `:q` – Quitter Vim.
- `:wq` – Sauvegarder et quitter.
- `:q!` – Quitter sans sauvegarder.

### Divers

- `.` – Répéter la dernière commande.
- `:%!` – Exécuter une commande externe (ex. `:%!sort` pour trier le fichier).
