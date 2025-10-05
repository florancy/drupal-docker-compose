# Local docker-compose Drupal CMS v11
##Installation
1. Créer le fichier `.env` à la racine du projet en copiant le contenu du fichier `.env.local`
2. Démarrer les containers avec la commande :
```
docker-compose up -d
```
3. Lister les containers actifs avec la commande : 
```
docker container ls
```
4. Entrer dans le container `my_drupal11_project_php` avec la commande
```
docker exec -it my_drupal11_project_php /bin/bash
```
5. Installer avec la commande composer
```
composer install
```