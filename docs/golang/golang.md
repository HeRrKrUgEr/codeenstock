
# CheatSheet Golang

## Installation et Configuration

- **Installer Golang** : [https://golang.org/dl/](https://golang.org/dl/)
- **Configurer le GOPATH** :

  ```bash
  export GOPATH=$HOME/go
  export PATH=$PATH:$GOPATH/bin
  ```

- **Créer un nouveau projet**

  ```bash
  mkdir -p $GOPATH/src/monprojet
  cd $GOPATH/src/monprojet
  ```

## Structure de base d'un programme

- **Structure d'un programme simple** :

  ```go
  package main

  import "fmt"

  func main() {
      fmt.Println("Bonjour, Go!")
  }
  ```

## Variables et Types

- **Déclaration de variables**

  ```go
  var nom string = "Vincent"
  age := 30  // Déclaration avec inférence de type
  ```

- **Types de données courants** :
  - `string`
  - `int`, `int32`, `int64`
  - `float32`, `float64`
  - `bool`

## Fonctions

- **Déclaration de fonction**

  ```go
  func nomFonction(parametre string) int {
      return len(parametre)
  }
  ```

- **Fonctions avec plusieurs valeurs de retour**

  ```go
  func diviser(a, b int) (int, int) {
      return a / b, a % b
  }
  ```

## Structures de contrôle

- **Condition IF**

  ```go
  if condition {
      // Code
  } else if autreCondition {
      // Code
  } else {
      // Code
  }
  ```

- **Boucles FOR**

  ```go
  for i := 0; i < 10; i++ {
      fmt.Println(i)
  }
  ```

  - **Boucle infinie** : `for { ... }`
  - **Boucle avec gamme** :

    ```go
    for index, valeur := range collection {
        // Code
    }
    ```

## Tableaux, Slices et Maps

- **Tableaux**

  ```go
  var noms [3]string
  noms[0] = "Alice"
  ```

- **Slices**

  ```go
  nombres := []int{1, 2, 3}
  nombres = append(nombres, 4)
  ```

- **Maps**

  ```go
  notes := map[string]int{"Alice": 90, "Bob": 85}
  notes["Eve"] = 88
  ```

## Structs et Méthodes

- **Définir une struct**

  ```go
  type Personne struct {
      Nom   string
      Age   int
  }
  ```

- **Méthodes pour les structs**

  ```go
  func (p Personne) Saluer() {
      fmt.Printf("Bonjour, %s!

", p.Nom)
  }

  ```

## Concurrence

- **Goroutines**
  ```go
  go fonctionConcurrente()
  ```

- **Canaux**

  ```go
  messages := make(chan string)
  messages <- "Bonjour"
  fmt.Println(<-messages)
  ```

## Gestion des erreurs

- **Utiliser `error`**

  ```go
  func diviser(a, b int) (int, error) {
      if b == 0 {
          return 0, errors.New("division par zéro")
      }
      return a / b, nil
  }
  ```

- **Panic et Recover**

  ```go
  defer func() {
      if r := recover(); r != nil {
          fmt.Println("Récupéré dans", r)
      }
  }()
  panic("Erreur critique")
  ```

## Bibliothèques Standard Utiles

- **fmt** : Formattage d'entrées et sorties
- **time** : Manipulation des dates et heures
- **strings** : Manipulation de chaînes
- **strconv** : Conversion entre chaînes et types numériques
- **net/http** : Serveur HTTP

## Exécution et Compilation

- **Exécuter un fichier**

  ```bash
  go run monfichier.go
  ```

- **Compiler un fichier**

  ```bash
  go build monfichier.go
  ```

- **Tester le code**

  ```bash
  go test
  ```

---

Ce guide couvre les bases du langage Go pour démarrer rapidement et facilement !
