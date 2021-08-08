# memo_docker

## Images

1. ###### Recherche image :
`` docker search [recherche] ``

2. ###### Récupérer une image depuis docker hub
`` docker pull [mot clé] ``

3. ###### Pusher une image sur le repository docker hub
`` docker push [id utilisateur]/[nom de l'image] ``

4. ###### Images disponibles
`` docker images ``

5. ###### Images téléchargées
`` docker info ``

## Container

1. ###### supprime tous les containers et images non utilisés
`` docker system prune [OPTIONS]``

2. ###### Démarrer un conteneur
`` docker run [nom de l'images] ``

__exemple : démarrer un conteneur qui contient un serveur nginx__
`` docker run -d -p 8080:80 nginx ``
* Options
    * -p : detacher conteneur du processus principal
    * -d : utilisation du port 8080 vers le port 80 du conteneur 

3. ###### Arrêter un conteneur
`` docker stop [id conteneur] ``

4. ###### Effacer un conteneur
`` docker rm [id conteneur]``

5. ###### Liste des conteneurs actifs
`` docker ps``

6. ###### Créer une image  à partir d'un dockerfile
`` docker build ``

__exemple :__
`` docker build -t mon-image-perso ``
* -t : pour donner un nom à notre image
* . : pour aller chercher notre DockerFile à la racine de notre projet
