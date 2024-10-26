
# Aide-mémoire SSH en ligne de commande

## Bases

- **Se connecter au serveur**

  ```bash
  ssh utilisateur@hôte
  ```

- **Spécifier le port**

  ```bash
  ssh -p numéro_port utilisateur@hôte
  ```

- **Connexion avec un fichier d'identité**

  ```bash
  ssh -i /chemin/vers/clé_privée utilisateur@hôte
  ```

- **Connexion via un fichier de configuration**

  ```bash
  ssh alias_hôte
  ```

  *Chemin du fichier de config : `~/.ssh/config`*

  ```plaintext
  Host alias_hôte
      HostName nomhôte
      User utilisateur
      Port numéro_port
      IdentityFile /chemin/vers/clé_privée
  ```

## Gestion des clés

- **Générer une paire de clés SSH**

  ```bash
  ssh-keygen -t rsa -b 4096 -C "votre_email@example.com"
  ```

- **Copier la clé publique vers le serveur**

  ```bash
  ssh-copy-id utilisateur@hôte
  ```

- **Ajouter la clé à l'agent SSH**

  ```bash
  ssh-add /chemin/vers/clé_privée
  ```

## Transfert de fichiers

- **Utilisation de SCP**
  - **Copier un fichier vers le serveur**

    ```bash
    scp fichier utilisateur@hôte:/chemin/vers/serveur
    ```

  - **Copier un dossier vers le serveur**

    ```bash
    scp -r /dossier/local utilisateur@hôte:/dossier/serveur
    ```

  - **Copier un fichier depuis le serveur**

    ```bash
    scp utilisateur@hôte:/chemin/vers/serveur/fichier /chemin/local
    ```

- **Utilisation de SFTP**

  ```bash
  sftp utilisateur@hôte
  ```

  - **Commandes SFTP** :
    - `get fichier_distant` - Télécharger un fichier
    - `put fichier_local` - Télécharger un fichier
    - `ls` - Lister les fichiers sur le serveur
    - `exit` - Quitter SFTP

## Transfert de port

- **Transfert de port local**

  ```bash
  ssh -L port_local:hôte_destination:port_destination utilisateur@hôte
  ```

- **Transfert de port distant**

  ```bash
  ssh -R port_distant:hôte_destination:port_destination utilisateur@hôte
  ```

- **Transfert de port dynamique (Proxy SOCKS)**

  ```bash
  ssh -D port_local utilisateur@hôte
  ```

## Tunneling

- **Tunneling SSH avec ProxyJump**

  ```bash
  ssh -J utilisateur@hôte_pont utilisateur@hôte_cible
  ```

- **Multiplexage SSH**

  ```plaintext
  Host *
      ControlMaster auto
      ControlPath ~/.ssh/sockets/%r@%h-%p
      ControlPersist 600
  ```

## Divers

- **Exécuter une commande sur le serveur distant**

  ```bash
  ssh utilisateur@hôte "commande"
  ```

- **Mode verbeux (pour le débogage)**

  ```bash
  ssh -v utilisateur@hôte
  ```

- **Désactiver la vérification de la clé de l'hôte (à utiliser avec prudence)**

  ```bash
  ssh -o StrictHostKeyChecking=no utilisateur@hôte
  ```

- **Redirection de l'agent SSH**

  ```bash
  ssh -A utilisateur@hôte
  ```

## Conseils pour le fichier de configuration SSH

- **Exemple d'entrée de configuration**

  ```plaintext
  Host monserveur
      HostName exemple.com
      User utilisateur
      Port 22
      IdentityFile ~/.ssh/id_rsa
      ForwardAgent yes
  ```

## Problèmes courants

- **Correction de l'erreur "Les autorisations sont trop ouvertes"**

  ```bash
  chmod 600 ~/.ssh/id_rsa
  ```

- **Ajouter un hôte connu**

  ```bash
  ssh-keyscan -H hôte >> ~/.ssh/known_hosts
  ```

---

Ce guide couvre les commandes SSH essentielles et les configurations pour optimiser l'utilisation de SSH !
