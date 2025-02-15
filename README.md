# Installation et Configuration de Docker pour Symfony (Apache /Mysql 8.0 /Php8.1 /Symfony CLi /PhpMyadmin /Symfony 6.4.* )

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

 Docker veut accéder au chemin de dossier créer \Environnement-D-veloppement-Docker-Symfony\php\vhost : Répondez yes <br>
 Docker veut accéder au chemin de dossier créer \Environnement-D-veloppement-Docker-Symfony: Répondez yes
 
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
Pour entrer dans le conteneur Symfony, utilisez la commande suivante :
 ```bash
docker exec -it docker_www bash
```
### 7. Configurez Git
Configurez Git avec vos informations personnelles pour une utilisation dans le conteneur Symfony :
 ```bash
git config --global user.name "Your Name"
git config --global user.email your_email@example.com
```
### 8. Créez un nouveau projet Symfony
Pour créer un projet Web Symfony, utilisez la commande suivante :
 ```bash
symfony new myproject --version="6.4.*" --webapp
```
Pour créer un projet API Symfony, utilisez :
 ```bash
symfony new myproject --version="6.4.*"
 ```
Si vous souhaitez changer le nom du projet, modifiez également le fichier vhosts/default.conf à /var/www/nouveaunom/public.
### 9. Vérifiez la création du projet Symfony
Lancez le serveur Symfony pour vérifier que le projet fonctionne correctement :
 ```bash
symfony serve -d
 ```
### 10. Configurez la connexion à la base de données
Modifiez le fichier .env pour définir les informations de connexion à la base de données :
 ```bash
DATABASE_URL="mysql://symfony:symfony@db:3306/abdelhakmireda"
 ```
Pour créer la base de données, accédez au conteneur Symfony et exécutez :
 ```bash
docker exec -it docker_www bash
cd myproject
bin/console doctrine:database:create
 ```
Si une erreur comme SQLSTATE[HY000]: General error: 1007 Can't create database 'abdelhakmireda'; database exists apparaît, cela signifie que la connexion à la base de données est correcte.
### 11. Testez la création des entités
Testez la création d'une entité et exécutez les migrations avec les commandes suivantes :
 ```bash
php bin/console make:entity test
php bin/console make:migration
php bin/console doctrine:migrations:migrate
 ```
# Résolution de problèmes:
Si vous rencontrez l'erreur SQLSTATE[42000]: Syntax error or access violation: 1044 Access denied for user 'symfony'@'%' to database 'newnamedb', suivez ces étapes :
## Vérifiez les permissions de l'utilisateur MySQL
Connectez-vous au conteneur MySQL :
```bash
docker exec -it docker_mysql mysql -u root -p
```
Vérifiez les bases de données existantes :
```bash
SHOW DATABASES;
```
Vérifiez les privilèges de l'utilisateur symfony :
```bash
SHOW GRANTS FOR 'symfony'@'%';
```
Accordez les privilèges nécessaires si ce n'est pas déjà fait :
```bash
GRANT ALL PRIVILEGES ON *.* TO 'symfony'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
# Bravo, vous avez maintenant configuré votre environnement Docker pour Symfony ! 🥳🫡​🥳​🫡​
