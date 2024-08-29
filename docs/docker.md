# Cheatsheet Docker

## Gestion des Images

- `docker images`  
  Liste toutes les images Docker locales.

- `docker pull <nom_image>`  
  Télécharge une image depuis un registre Docker (ex : Docker Hub).

- `docker build -t <nom_image>:<tag> <chemin_du_dockerfile>`  
  Construit une image Docker à partir d'un Dockerfile.

- `docker rmi <nom_image>`  
  Supprime une image locale.

## Gestion des Conteneurs

- `docker ps`  
  Affiche les conteneurs en cours d'exécution.

- `docker ps -a`  
  Affiche tous les conteneurs, y compris ceux qui sont arrêtés.

- `docker run <nom_image>`  
  Exécute un nouveau conteneur à partir d'une image.

- `docker run -d <nom_image>`  
  Exécute un conteneur en arrière-plan (mode détaché).

- `docker run -it <nom_image> /bin/bash`  
  Exécute un conteneur en mode interactif avec un shell Bash.

- `docker stop <nom_conteneur>`  
  Arrête un conteneur en cours d'exécution.

- `docker start <nom_conteneur>`  
  Démarre un conteneur arrêté.

- `docker restart <nom_conteneur>`  
  Redémarre un conteneur.

- `docker rm <nom_conteneur>`  
  Supprime un conteneur arrêté.

## Gestion des Réseaux

- `docker network ls`  
  Liste tous les réseaux Docker.

- `docker network create <nom_réseau>`  
  Crée un nouveau réseau Docker.

- `docker network connect <nom_réseau> <nom_conteneur>`  
  Connecte un conteneur à un réseau.

- `docker network disconnect <nom_réseau> <nom_conteneur>`  
  Déconnecte un conteneur d'un réseau.

- `docker network rm <nom_réseau>`  
  Supprime un réseau Docker.

## Gestion des Volumes

- `docker volume ls`  
  Liste tous les volumes Docker.

- `docker volume create <nom_volume>`  
  Crée un nouveau volume Docker.

- `docker volume rm <nom_volume>`  
  Supprime un volume Docker.

- `docker run -v <nom_volume>:<chemin_dans_conteneur> <nom_image>`  
  Monte un volume dans un conteneur.

## Exécution et Logs

- `docker exec -it <nom_conteneur> <commande>`  
  Exécute une commande dans un conteneur en cours d'exécution.

- `docker logs <nom_conteneur>`  
  Affiche les logs d'un conteneur.

- `docker logs -f <nom_conteneur>`  
  Affiche les logs d'un conteneur en temps réel (mode suivi).

## Informations et Diagnostics

- `docker inspect <nom_conteneur_ou_nom_image>`  
  Retourne des informations détaillées sur un conteneur ou une image.

- `docker stats`  
  Affiche en temps réel les statistiques d'utilisation des ressources pour tous les conteneurs.

- `docker top <nom_conteneur>`  
  Affiche les processus en cours dans un conteneur.

## Docker Compose

- `docker-compose up`  
  Démarre tous les services définis dans un fichier `docker-compose.yml`.

- `docker-compose down`  
  Arrête et supprime les conteneurs, réseaux, volumes, et images créés par `docker-compose up`.

- `docker-compose build`  
  Construit ou reconstruit les services.

- `docker-compose ps`  
  Liste tous les conteneurs gérés par Docker Compose.

## Nettoyage

- `docker system prune`  
  Supprime tous les conteneurs, réseaux et images inutilisés.

- `docker volume prune`  
  Supprime tous les volumes non utilisés.

- `docker network prune`  
  Supprime tous les réseaux non utilisés.

- `docker image prune`  
  Supprime les images non utilisées.

## Sauvegarde et Restauration

- `docker save -o <nom_fichier.tar> <nom_image>`  
  Sauvegarde une image Docker dans un fichier.

- `docker load -i <nom_fichier.tar>`  
  Charge une image Docker à partir d'un fichier.

- `docker export -o <nom_fichier.tar> <nom_conteneur>`  
  Exporte le système de fichiers d'un conteneur.

- `docker import <nom_fichier.tar> <nom_image>`  
  Importe un système de fichiers dans une nouvelle image Docker.

---

Cette cheatsheet couvre les commandes Docker les plus couramment utilisées pour la gestion des images, des conteneurs, des réseaux, des volumes, et des tâches de diagnostic. Utilisez-la comme référence rapide pour vos opérations Docker quotidiennes.
