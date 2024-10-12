# Linux Bash Command Cheatsheet (en français)

Ce cheatsheet couvre les commandes Linux les plus couramment utilisées, avec des options et des exemples pour vous aider à maîtriser la ligne de commande. Chaque commande inclut des descriptions, des exemples et des options fréquemment utilisées.

## 1. Navigation et Gestion des Répertoires

### `cd` - Changer de Répertoire

- Change le répertoire de travail actuel.

```bash
cd /chemin/vers/répertoire  # Aller au répertoire spécifié
cd ..                       # Remonter d'un répertoire
cd ~                        # Aller au répertoire personnel
```

### `ls` - Lister le Contenu du Répertoire

- Affiche des informations sur les fichiers et répertoires.

```bash
ls                          # Lister les fichiers dans le répertoire actuel
ls -l                       # Liste détaillée en format long
ls -a                       # Lister tous les fichiers, y compris les fichiers cachés
ls -lh                      # Liste détaillée avec des tailles de fichiers lisibles
```

### `pwd` - Afficher le Répertoire Courant

- Affiche le chemin du répertoire actuel.

```bash
pwd                         # Afficher le chemin du répertoire actuel
```

### `mkdir` - Créer un Répertoire

- Crée un nouveau répertoire.

```bash
mkdir nouveau_dossier       # Créer un répertoire nommé 'nouveau_dossier'
mkdir -p parent/enfant      # Créer des répertoires parent et enfant s'ils n'existent pas
```

### `rmdir` - Supprimer un Répertoire

- Supprime un répertoire vide.

```bash
rmdir dossier_vide          # Supprimer le répertoire nommé 'dossier_vide'
```

### `rm` - Supprimer des Fichiers ou Répertoires

- Supprime des fichiers ou des répertoires.

```bash
rm fichier.txt              # Supprimer un fichier nommé 'fichier.txt'
rm -r dossier               # Supprimer un répertoire nommé 'dossier' et son contenu
rm -f fichier.txt           # Forcer la suppression d'un fichier sans confirmation
```

## 2. Gestion des Fichiers

### `cp` - Copier des Fichiers et Répertoires

- Copie des fichiers ou répertoires.

```bash
cp source.txt dest.txt      # Copier source.txt vers dest.txt
cp -r dossier1 dossier2     # Copier récursivement dossier1 vers dossier2
```

### `mv` - Déplacer ou Renommer des Fichiers et Répertoires

- Déplace ou renomme des fichiers ou répertoires.

```bash
mv ancien_nom.txt nouveau_nom.txt # Renommer 'ancien_nom.txt' en 'nouveau_nom.txt'
mv fichier.txt /nouveau/emplacement # Déplacer 'fichier.txt' vers '/nouveau/emplacement'
```

### `touch` - Créer un Fichier Vide

- Crée un nouveau fichier vide ou met à jour la date d'accès d'un fichier existant.

```bash
touch nouveau_fichier.txt   # Créer un fichier vide nommé 'nouveau_fichier.txt'
```

### `cat` - Concaténer et Afficher le Contenu des Fichiers

- Affiche le contenu d'un fichier.

```bash
cat fichier.txt             # Afficher le contenu de 'fichier.txt'
cat fichier1.txt fichier2.txt # Concaténer et afficher le contenu de plusieurs fichiers
```

### `less` - Afficher le Contenu d'un Fichier de Manière Interactive

- Affiche le contenu d'un fichier page par page.

```bash
less fichier.txt            # Afficher 'fichier.txt' avec pagination
```

### `head` / `tail` - Afficher le Début ou la Fin d'un Fichier

- Affiche le début ou la fin d'un fichier.

```bash
head -n 5 fichier.txt       # Afficher les 5 premières lignes de 'fichier.txt'
tail -n 5 fichier.txt       # Afficher les 5 dernières lignes de 'fichier.txt'
tail -f journal.txt         # Suivre 'journal.txt' pour les nouvelles entrées en temps réel
```

### `find` - Rechercher des Fichiers et Répertoires

- Recherche des fichiers dans une hiérarchie de répertoires.

```bash
find /chemin -name "*.txt"    # Trouver les fichiers se terminant par .txt
find . -type d -name "sauvegarde" # Trouver les répertoires nommés 'sauvegarde'
```

### `locate` - Trouver des Fichiers par Nom

- Localise des fichiers par leur nom rapidement en utilisant un index.

```bash
locate fichier              # Trouver les fichiers nommés 'fichier'
locate -i "NomFichier"      # Trouver des fichiers sans distinction de casse
```

### `diff` - Comparer des Fichiers Ligne par Ligne

- Compare le contenu de deux fichiers.

```bash
diff fichier1.txt fichier2.txt # Montrer les différences entre 'fichier1.txt' et 'fichier2.txt'
```

## 3. Permissions et Propriétés des Fichiers

### `chmod` - Modifier les Permissions des Fichiers

- Modifie les permissions d'accès d'un fichier ou d'un répertoire.

```bash
chmod 755 script.sh        # Définir les permissions de lecture, écriture et exécution pour le propriétaire, lecture et exécution pour le groupe et les autres
chmod u+x fichier.txt      # Ajouter la permission d'exécution pour le propriétaire
```

### `chown` - Modifier le Propriétaire et le Groupe d'un Fichier

- Change le propriétaire des fichiers ou répertoires.

```bash
chown utilisateur:groupe fichier.txt # Changer le propriétaire à 'utilisateur' et le groupe à 'groupe'
```

### `chgrp` - Modifier le Groupe d'un Fichier

- Change le groupe de propriété d'un fichier ou répertoire.

```bash
chgrp nomgroupe fichier.txt # Changer le groupe de propriété de 'fichier.txt' en 'nomgroupe'
```

## 4. Informations Système

### `uname` - Afficher des Informations Système

- Affiche des informations sur le système.

```bash
uname -a                   # Afficher toutes les informations sur le système
uname -r                   # Afficher la version du noyau
```

### `df` - Utilisation du Système de Fichiers

- Affiche les statistiques d'utilisation des systèmes de fichiers.

```bash
df -h                      # Afficher l'utilisation des disques en format lisible
df /home                   # Afficher l'utilisation du disque pour le répertoire '/home'
```

### `du` - Estimer l'Utilisation de l'Espace des Fichiers

- Affiche l'utilisation des fichiers et répertoires.

```bash
du -sh dossier             # Afficher la taille totale de 'dossier' en format lisible
du -a                      # Lister tous les fichiers et leur utilisation
```

### `top` - Gestionnaire de Tâches

- Affiche des informations en temps réel sur les processus.

```bash
top                        # Afficher les tâches et statistiques système en temps réel
```

### `htop` - Visionneuse Interactive de Processus

- Une version améliorée de `top` avec une interface plus conviviale.

```bash
htop                       # Lancer htop pour la gestion interactive des processus
```

### `free` - Afficher l'Utilisation de la Mémoire

- Affiche la mémoire libre et utilisée du système.

```bash
free -h                    # Afficher l'utilisation de la mémoire en format lisible
```

### `uptime` - Afficher le Temps de Fonctionnement du Système

- Affiche la durée pendant laquelle le système est en marche.

```bash
uptime                     # Afficher le temps de fonctionnement, le nombre d'utilisateurs, et la charge moyenne
```

### `who` - Afficher Qui est Connecté

- Affiche des informations sur les utilisateurs actuellement connectés.

```bash
who                        # Afficher une liste des utilisateurs actuellement connectés
```

## 5. Traitement de Texte

### `grep` - Rechercher du Texte en Utilisant des Modèles

- Recherche des motifs spécifiques dans des fichiers.

```bash
grep "erreur" journal.txt  # Rechercher le mot 'erreur' dans 'journal.txt'
grep -r "TODO" /projet     # Rechercher récursivement 'TODO' dans '/projet'
```

### `awk` - Outil de Traitement de Texte

- Langage de traitement de texte et de balayage de modèles.

```bash
awk '{print $1}' fichier.txt # Afficher le premier champ de chaque ligne de 'fichier.txt'
```

### `sed` - Éditeur de Flux pour la Transformation de Texte

- Modifie le texte d'un fichier sans l'ouvrir.

```bash
sed 's/ancien/nouveau/g' fichier.txt # Remplacer 'ancien' par 'nouveau' globalement dans 'fichier.txt'
```

### `sort` - Trier les Lignes des Fichiers Texte

- Trie les lignes d'un fichier texte.

```bash
sort fichier.txt           # Trier les lignes dans 'fichier.txt'
sort -r fichier.txt        # Trier les lignes en ordre inverse
```

### `uniq` - Rapporter ou Omettre les Lignes Répétées

- Filtre les lignes répétées dans un fichier.

```bash
uniq fichier.txt           # Supprimer les lignes en double de 'fichier.txt'
uniq -c fichier.txt        # Compter et afficher les lignes en double
```

### `wc` - Afficher le Nombre de Lignes, Mots et Octets

- Compte les lignes, mots et caractères dans un fichier.

```bash
wc fichier.txt             # Afficher le nombre de lignes, mots et octets
wc -l fichier.txt          # Afficher uniquement le nombre de lignes
```

## 6. Commandes Réseau

### `ping` - Envoyer une Requête ICMP ECHO

- Vérifie la connectivité réseau.

```bash
ping google.com            # Ping google.com pour vérifier la connectivité
ping -c 5 google.com       # Ping google.com 5 fois
```

### `ifconfig` - Configurer les Interfaces Réseau

- Affiche ou configure les interfaces réseau.

```bash
ifconfig                   # Afficher les interfaces réseau et les adresses IP
```

### `ip` - Afficher / Manipuler les Routes, Appareils, et Tunnels

- Un outil plus moderne pour gérer les adresses IP et les appareils réseau.

```bash
ip addr show               # Afficher les adresses IP assignées à toutes les interfaces
ip link set eth0 up        # Activer l'interface 'eth0'
```

### `wget` - Télécharger des Fichiers depuis Internet

- Téléchargeur réseau non interactif.

```bash
wget http://exemple.com/fichier.zip  # Télécharger 'fichier.zip' depuis exemple.com
wget -c url                          # Continuer un téléchargement incomplet
```

### `curl` - Transférer des Données depuis ou vers un Serveur

- Outil pour transférer des données depuis ou vers un serveur, couramment utilisé pour tester des API.

```bash
curl http://exemple.com              # Récupérer le contenu de 'http://exemple.com'
curl -O http://exemple.com/fichier   # Télécharger 'fichier' depuis exemple.com
```

## 7. Archivage et Compression

### `tar` - Archiver des Fichiers

- Crée et extrait des fichiers d'archive.

```bash
tar -cvf archive.tar dossier     # Créer une archive de 'dossier'
tar -xvf archive.tar             # Extraire 'archive.tar'
tar -czvf archive.tar.gz dossier # Créer une archive gzippée de 'dossier'
```

### `zip` / `unzip` - Compresser et Décompresser des Fichiers

- Crée et extrait des fichiers zip.

```bash
zip -r archive.zip dossier       # Compresser 'dossier' dans 'archive.zip'
unzip archive.zip                # Extraire 'archive.zip'
```

### `gzip` / `gunzip` - Compresser et Décompresser des Fichiers

- Compresse ou décompresse des fichiers au format gzip.

```bash
gzip fichier.txt                 # Compresser 'fichier.txt' en 'fichier.txt.gz'
gunzip fichier.txt.gz           # Décompresser 'fichier.txt.gz'
```

## 8. Gestion des Processus

### `ps` - Afficher des Informations sur les Processus en Cours

- Affiche les processus en cours.

```bash
ps aux                       # Afficher tous les processus en cours avec des détails
ps -ef                       # Liste en format complet des processus en cours
```

### `kill` - Terminer un Processus

- Envoie un signal à un processus.

```bash
kill 1234                    # Tuer le processus avec PID 1234
kill -9 1234                 # Forcer la terminaison du processus avec PID 1234
```

### `killall` - Tuer les Processus par Nom

- Tuer les processus par leur nom.

```bash
killall firefox              # Tuer tous les processus nommés 'firefox'
```

### `bg` et `fg` - Gérer les Tâches en Arrière-plan et Premier-plan

- Déplace les tâches en arrière-plan ou en premier-plan.

```bash
bg                          # Reprendre une tâche suspendue en arrière-plan
fg                          # Ramener une tâche en arrière-plan au premier-plan
```

### `jobs` - Lister les Tâches Actives

- Affiche une liste des tâches.

```bash
jobs                        # Lister toutes les tâches en arrière-plan et suspendues
```

## 9. Divers

### `echo` - Afficher un Message à l'Écran

- Imprime une chaîne de texte.

```bash
echo "Bonjour, le monde!"    # Afficher 'Bonjour, le monde!'
```

### `history` - Historique des Commandes

- Affiche les commandes précédemment utilisées.

```bash
history                     # Afficher l'historique des commandes
history | grep "ls"         # Rechercher 'ls' dans l'historique des commandes
```

### `crontab` - Planifier des Tâches Périodiques

- Planifie des tâches à exécuter périodiquement.

```bash
crontab -e                  # Éditer les tâches cron de l'utilisateur actuel
```

### `alias` - Créer des Alias pour des Commandes

- Crée des raccourcis pour des commandes longues.

```bash
alias ll='ls -la'           # Créer un alias 'll' pour 'ls -la'
```

### `date` - Afficher ou Définir la Date et l'Heure du Système

- Affiche ou définit la date et l'heure du système.

```bash
date                        # Afficher la date et l'heure actuelles
date -s "2024-10-12 14:00"  # Définir la date et l'heure du système
```

### `shutdown` - Arrêter ou Redémarrer le Système

- Arrête ou redémarre la machine.

```bash
shutdown now                # Arrêter le système immédiatement
shutdown -r 10              # Redémarrer le système après 10 minutes
```
