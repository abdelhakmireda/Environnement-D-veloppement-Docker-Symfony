# Installation et Configuration de Docker pour Symfony

Ce guide vous explique comment configurer Docker pour un projet Symfony en utilisant Docker Compose.

## Prérequis

- Docker Desktop installé
- Git installé
- Visual Studio Code (ou un autre éditeur de texte)

## Étapes d'installation

1. **Clonez le dépôt du projet**

   Ouvrez un terminal et exécutez la commande suivante :

   ```bash
   git clone https://github.com/abdelhakmireda/Environnement-D-veloppement-Docker-Symfony.git
Accédez au répertoire du projet

bash
Copier le code
cd .\Environnement-D-veloppement-Docker-Symfony\
Démarrez les conteneurs Docker

Exécutez la commande suivante pour lancer les conteneurs en arrière-plan :

bash
Copier le code
docker-compose up -d
Configuration du partage de fichiers Docker Desktop

Lorsque Docker Desktop vous demande l'accès à des chemins de dossier, acceptez les requêtes suivantes :

Docker wants to access to chemin de dossier créer \environemee…\php\vhost : Répondez yes
Docker wants to access to chemin de dossier créer \environemee…\ : Répondez yes
Vérification des conteneurs Docker

Les conteneurs devraient commencer à apparaître dans Docker Desktop avec les statuts suivants :

mathematica
Copier le code
✔ Network environnement-d-veloppement-docker-symfony_dev       Created
✔ Volume "environnement-d-veloppement-docker-symfony_db-data"  Created
✔ Container docker_mysql                                       Started
✔ Container docker_www                                         Started
✔ Container docker_phpmyadmin                                  Started
Accédez au conteneur Symfony

Ouvrez un terminal et exécutez la commande suivante pour entrer dans le conteneur Symfony :

bash
Copier le code
docker exec -it docker_www bash
Configurer Git

Configurez Git avec vos informations :

bash
Copier le code
git config --global user.name "Your Name"
git config --global user.email your_email@example.com
Créer un nouveau projet Symfony

Pour un projet Web :

bash
Copier le code
symfony new myproject --version="6.4.*" --webapp
Pour un projet API :

bash
Copier le code
symfony new myproject --version="6.4.*"
Si vous souhaitez changer le nom du projet, modifiez également le fichier vhosts/default.conf à /var/www/nouveaunom/public.

Vérifiez la création du projet Symfony

Lancez le serveur Symfony pour vérifier que le projet fonctionne :

bash
Copier le code
symfony serve -d
Configurer la connexion à la base de données

Modifiez le fichier .env pour définir la connexion à la base de données :

env
Copier le code
DATABASE_URL="mysql://symfony:symfony@db:3306/abdelhakmireda"
Pour créer une autre base de données, ajoutez simplement un nom différent. Accédez au conteneur Symfony et exécutez :

bash
Copier le code
cd myproject
bin/console doctrine:database:create
Si vous rencontrez une erreur, comme SQLSTATE[HY000]: General error: 1007 Can't create database 'abdelhakmireda'; database exists, cela indique que la connexion à la base de données a été correctement établie.

Testez la création des entités

Testez la création d'une entité et exécutez les migrations :

bash
Copier le code
php bin/console make:entity test
php bin/console make:migration
php bin/console doctrine:migrations:migrate
Résolution de problèmes
Si vous rencontrez l'erreur SQLSTATE[42000]: Syntax error or access violation: 1044 Access denied for user 'symfony'@'%' to database 'abdelhakmia', suivez ces étapes :

Vérifiez les permissions de l'utilisateur MySQL

Connectez-vous au conteneur MySQL :

bash
Copier le code
docker exec -it docker_mysql mysql -u root -p
Vérifiez les bases de données existantes :

sql
Copier le code
SHOW DATABASES;
Vérifiez les privilèges de l'utilisateur symfony :

sql
Copier le code
SHOW GRANTS FOR 'symfony'@'%';
Accordez les privilèges nécessaires si ce n'est pas déjà fait :

sql
Copier le code
GRANT ALL PRIVILEGES ON *.* TO 'symfony'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
Bravo, vous avez maintenant configuré votre environnement Docker pour Symfony !

go
Copier le code

Copiez ce texte dans un fichier nommé `README.md` dans votre projet GitHub pour fournir des instructions claires et concises aux utilisateurs qui souhaitent configurer leur environnement Docker pour Symfony.
donne le mois sous le forme de tesste avec les balise pour chaque partie pour concerver une bonne aparrence de readme
ChatGPT
Bien sûr ! Voici le README formaté en Markdown avec des balises appropriées pour chaque section afin de conserver une bonne apparence :

markdown
Copier le code
# Installation et Configuration de Docker pour Symfony

Ce guide vous explique comment configurer Docker pour un projet Symfony en utilisant Docker Compose.

## Prérequis

- Docker Desktop installé
- Git installé
- Visual Studio Code (ou un autre éditeur de texte)

## Étapes d'installation

### 1. Clonez le dépôt du projet

Ouvrez un terminal et exécutez la commande suivante :

```bash
git clone https://github.com/abdelhakmireda/Environnement-D-veloppement-Docker-Symfony.git
2. Accédez au répertoire du projet
bash
Copier le code
cd .\Environnement-D-veloppement-Docker-Symfony\
3. Démarrez les conteneurs Docker
Exécutez la commande suivante pour lancer les conteneurs en arrière-plan :

bash
Copier le code
docker-compose up -d
4. Configuration du partage de fichiers Docker Desktop
Lorsque Docker Desktop vous demande l'accès à des chemins de dossier, acceptez les requêtes suivantes :

Docker wants to access to chemin de dossier créer \environemee…\php\vhost : Répondez yes
Docker wants to access to chemin de dossier créer \environemee…\ : Répondez yes
5. Vérification des conteneurs Docker
Les conteneurs devraient commencer à apparaître dans Docker Desktop avec les statuts suivants :

plaintext
Copier le code
✔ Network environnement-d-veloppement-docker-symfony_dev       Created
✔ Volume "environnement-d-veloppement-docker-symfony_db-data"  Created
✔ Container docker_mysql                                       Started
✔ Container docker_www                                         Started
✔ Container docker_phpmyadmin                                  Started
6. Accédez au conteneur Symfony
Ouvrez un terminal et exécutez la commande suivante pour entrer dans le conteneur Symfony :

bash
Copier le code
docker exec -it docker_www bash
7. Configurez Git
Configurez Git avec vos informations :

bash
Copier le code
git config --global user.name "Your Name"
git config --global user.email your_email@example.com
8. Créez un nouveau projet Symfony
Pour un projet Web :

bash
Copier le code
symfony new myproject --version="6.4.*" --webapp
Pour un projet API :

bash
Copier le code
symfony new myproject --version="6.4.*"
Si vous souhaitez changer le nom du projet, modifiez également le fichier vhosts/default.conf à /var/www/nouveaunom/public.

9. Vérifiez la création du projet Symfony
Lancez le serveur Symfony pour vérifier que le projet fonctionne :

bash
Copier le code
symfony serve -d
10. Configurez la connexion à la base de données
Modifiez le fichier .env pour définir la connexion à la base de données :

env
Copier le code
DATABASE_URL="mysql://symfony:symfony@db:3306/abdelhakmireda"
Pour créer une autre base de données, ajoutez simplement un nom différent. Accédez au conteneur Symfony et exécutez :

bash
Copier le code
cd myproject
bin/console doctrine:database:create
Si vous rencontrez une erreur, comme SQLSTATE[HY000]: General error: 1007 Can't create database 'abdelhakmireda'; database exists, cela indique que la connexion à la base de données a été correctement établie.

11. Testez la création des entités
Testez la création d'une entité et exécutez les migrations :

bash
Copier le code
php bin/console make:entity test
php bin/console make:migration
php bin/console doctrine:migrations:migrate
Résolution de problèmes
Si vous rencontrez l'erreur SQLSTATE[42000]: Syntax error or access violation: 1044 Access denied for user 'symfony'@'%' to database 'abdelhakmia', suivez ces étapes :

Vérifiez les permissions de l'utilisateur MySQL

Connectez-vous au conteneur MySQL :

bash
Copier le code
docker exec -it docker_mysql mysql -u root -p
Vérifiez les bases de données existantes :

sql
Copier le code
SHOW DATABASES;
Vérifiez les privilèges de l'utilisateur symfony :

sql
Copier le code
SHOW GRANTS FOR 'symfony'@'%';
Accordez les privilèges nécessaires si ce n'est pas déjà fait :

sql
Copier le code
GRANT ALL PRIVILEGES ON *.* TO 'symfony'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;
Bravo, vous avez maintenant configuré votre environnement Docker pour Symfony !
