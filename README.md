# Installation et Configuration de Docker pour Symfony

Ce guide vous explique comment configurer Docker pour un projet Symfony en utilisant Docker Compose.

## Prérequis

- Docker Desktop installé
- Git installé
- Visual Studio Code (ou un autre éditeur de texte)

## Étapes d'installation

### 1. Clonez le dépôt du projet

Ouvrez un terminal et exécutez la commande suivante pour cloner le dépôt Git contenant la configuration Docker pour Symfony :

```bash
git clone https://github.com/abdelhakmireda/Environnement-D-veloppement-Docker-Symfony.git
```
### 2. Accédez au répertoire du projet

Après avoir cloné le dépôt, accédez au répertoire du projet avec la commande suivante :
```bash
cd Environnement-D-veloppement-Docker-Symfony/
```
### 3. Démarrez les conteneurs Docker
Lancez les conteneurs Docker en arrière-plan avec la commande suivante :
```bash
docker-compose up -d
```
### 4. Configuration du partage de fichiers Docker Desktop
Lorsque Docker Desktop demande l'accès à des chemins de dossier, acceptez les requêtes suivantes :

 Docker veut accéder au chemin de dossier créer \environemee...\php\vhost : Répondez yes
 Docker veut accéder au chemin de dossier créer \environemee... : Répondez yes
 
 ### 5. Vérification des conteneurs Docker
 Vérifiez que les conteneurs sont correctement démarrés avec les statuts suivants :
 ```bash
✔ Network environnement-d-veloppement-docker-symfony_dev       Created
✔ Volume "environnement-d-veloppement-docker-symfony_db-data"  Created
✔ Container docker_mysql                                       Started
✔ Container docker_www                                         Started
✔ Container docker_phpmyadmin                                  Started
```

 ### 6. Accédez au conteneur Symfony
