# Cheat Sheet des Fonctions Utiles en Python

## Types de Données de Base

### Nombres

```python
# Opérations sur les entiers et les flottants
a = 10
b = 5.5

somme = a + b  # Addition
difference = a - b  # Soustraction
produit = a * b  # Multiplication
quotient = a / b  # Division
```

### Chaînes de caractères

```python
# Opérations sur les chaînes de caractères
s = "Bonjour, Monde!"

s_majuscule = s.upper()  # Convertir en majuscules
s_minuscule = s.lower()  # Convertir en minuscules
s_split = s.split(',')  # Diviser la chaîne en liste
s_replace = s.replace('Monde', 'Python')  # Remplacer une sous-chaîne
```

## Collections

### Listes

```python
# Opérations sur les listes
ma_liste = [1, 2, 3, 4, 5]

ma_liste.append(6)  # Ajouter un élément
ma_liste.remove(3)  # Supprimer un élément
ma_liste.sort()  # Trier la liste
ma_liste.reverse()  # Inverser la liste
```

### Dictionnaires

```python
# Opérations sur les dictionnaires
mon_dict = {'nom': 'Jean', 'âge': 30}

nom = mon_dict.get('nom')  # Obtenir la valeur par clé
mon_dict['âge'] = 31  # Modifier une valeur
cles = mon_dict.keys()  # Obtenir toutes les clés
valeurs = mon_dict.values()  # Obtenir toutes les valeurs
```

## Fonctions Utiles

### Fonctions de Base

```python
print("Bonjour")  # Afficher du texte
len(ma_liste)  # Obtenir la longueur d'une liste ou chaîne
type(a)  # Obtenir le type d'une variable
```

### Manipulation de Fichiers

```python
# Lire un fichier
with open('fichier.txt', 'r') as f:
    contenu = f.read()

# Écrire dans un fichier
with open('fichier.txt', 'w') as f:
    f.write("Bonjour, Monde!")
```

### Fonctions de Boucles

```python
# Boucle for
for i in range(5):
    print(i)

# Boucle while
compteur = 0
while compteur < 5:
    print(compteur)
    compteur += 1
```

### Compréhensions de Listes

```python
# Créer une nouvelle liste avec des carrés des nombres
carrés = [x**2 for x in range(10)]
```

### Gestion des Exceptions

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Division par zéro non autorisée!")
finally:
    print("Opération terminée.")
```
