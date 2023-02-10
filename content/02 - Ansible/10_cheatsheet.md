---
title: CheatSheet Docker
weight: 2010
---




### DOCKER BUILD


| Commandes                                           | Définitions                                                       | 
|----------------------------------------------------|----------------------------------------------------------------|
| docker build -t friendlyname .                     | Create image using this directory's Dockerfile                 | 
| docker build -t friendlyname -f /tmp/MYDOCKERFILE  | Create image using full path to another Dockerfile             |
| docker push username/repository:tag                | Upload tagged image to registry - Don't forget to Login 1st ^^ |
| docker login                                       | Log in this CLI session using your Docker credentials          |
| docker tag < _image_name > username/repository:tag | Tag < _image_name > for upload to registry                     |

    
    

### DOCKER CONTAINERS



| Commandes                                       | Définitions                                                                                                                                |
|:------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| docker container run -p 4000:80 friendlyname    | Run "friendlyname" mapping port 4000 to 80                                                                                                 |
| docker container run -d -p 4000:80 friendlyname | Same thing, but in detached mode                                                                                                           |
| docker exec -it __container-name__ bash         | Enter a running container                                                                                                                  |
| docker container ls                             | See a list of all running containers                                                                                                       |
| docker stop <hash>                              | Gracefully stop the specified container                                                                                                    |
| docker ps -a                                    | See a list of all containers, even the ones not running (old cmd version)                                                                  |
| docker container start __container-name__       | Démarre le conteneur                                                                                                                       |
| docker container stop __container-name__        | Arrête un conteneur en cours d'execution                                                                                                   |
| docker container restart __container-name__     | Redémarre le conteneur                                                                                                                     |
| docker pause __container-name__                 | Suspend tous les processus du conteneur                                                                                                    |
| docker unpause __container-id__                 | Retire la pause de tous les processus du conteneur                                                                                         |
| docker container kill __container-id__          | Force shutdown of the specified container                                                                                                  |
| docker container rm __container-id__            | Remove the specified container from this machine                                                                                           |
| docker container rm -f __container-id__         | Remove force specified container from this machine                                                                                         |
| docker container rm $(docker ps -a -q)          | Remove all containers from this machine                                                                                                    |
| docker container logs __container-id__ -f       | Live tail a container's logs                                                                                                               |
| docker container run username/repository:tag    | Run image from a registry                                                                                                                  |
| docker container port __container-id__          | List All port used by the container                                                                                                        |
| docker inspect __container-id__                 | Show informations about the container-id                                                                                                   |    
    
!!!! ____container-name____ ou __container-id__ 



### DOCKER IMAGE



| Commandes                       | Définitions                                     |
|--------------------------------|----------------------------------------------|
| docker images -a               | Show all images on this machine              |
| docker rmi <imagename>         | Remove the specified image from this machine |
| docker rmi $(docker images -q) | Remove all images from this machine          |
 


### DOCKER VOLUMES



| Commandes                        | Définitions                                      |
|---------------------------------|-----------------------------------------------|
| docker volume prune             | # Remove all unused local volumes             |
| docker volume ls                | # Liste les volumes                           |
| docker volume inspect __volulme__  | # Contrôle le volume                          |
| docker volume create __volulme__   | # Create volume                               |
| docker volume rm __volulme__       | # Remove volume                               |
!!!!    => __volumle__ replace by ID or volume's NAME



### DOCKER SYSTEM CMD 




| Commandes                           | Définitions                                                                                                    |
|------------------------------------|-------------------------------------------------------------------------------------------------------------|
| docker system df                   | # Montre l'espace disque utilisé par le docker                                                              |
| docker system info                 | # Affiche les inform­ations sur le système Docker                                                           |
| docker diff __container-name__ | # Affiche tous les fichiers qui ont été modifiés depuis le démarrage                                        |
| docker top __container-name__  | # Afficher le résultat de la commande "­top­" des processus en cours d'exéc­ution dans un conteneur         |
| docker stats                       | # Affiche le résultat de la commande "­top­" de tous les conteneurs Docker                                  |
| docker system prune                             | Remove all unused containers, networks, images (both dangling and unreferenced), and optionally, volumes. (Docker 17.06.1-ce and superior) |
| docker system prune -a                          | Remove all unused containers, networks, images not just dangling ones (Docker 17.06.1-ce and superior)                                     |
| docker volume prune                             | Remove all unused local volumes                                                                                                            |
| docker network prune                            | Remove all unused networks                                                                                                                 |


### DOCKER USEFULL CMD 



| Commandes                                                  | Définitions                                                                                     |
|------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| docker cp __container-name__:__source-path__ __dest-path__ | Copie du conteneur vers l'hôte                                                                  |
| docker cp __source-path__ __container-name__:__dest-path__  | Copie de l'hôte au conteneur                                                                    |
| docker exec -ti __container-name__ __entrypoint__     | Exécute le terminal d'un conteneur vivant  __entrypoint__ = /bin/bash ou /bin/sh ou autre chose |



### DOCKER NETWORK 



| Commandes                                                                                            - | Définitions                                                           |
|-------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| docker network ls                                                                                     | # Liste des réseaux                                                |
| docker network inspect __network__                                                                 | # Contrôle les inform­ations d'un réseau                           |          
| docker network create __network__                                                                  | # Crée un réseau                                                   |                                          
| docker network rm __network__                                                                      | Supprime un réseau                                                 |                                           
| docker network connect __network__ __container-name__                                              | # Connecte un conteneur au réseau                                  |                           
| docker network connect --ip <IP> __network__ __container-name__                                    | Spécifie l'adresse IP de l'inte­rface du conteneur                 |           
| docker network disconnect __network-name__ __container-name__                                  | Déconnecte le conteneur du réseau                                  |                
!!!!    => __network-name__ peut être remplacé par l'ID ou le NOM du réseau





### DOCKER COMPOSE 




| Commandes                               -         | Définitions                                                               |
|---------------------------------------------------|------------------------------------------------------------------------|
| docker compose up                                 |  Create and start containers                                           |
| docker compose up -d                              |  Create and start containers in detached mode                          |
| docker compose up -d --force-recreate             |  Create and start containers in detached mode and force recreate it    |
| docker compose down                               |  Stop and remove containers, networks, images, and volumes             |
| docker compose logs                               |  View output from containers                                           |
| docker compose restart                            |  Restart all service                                                   |
| docker compose pull                               |  Pull all image service                                                | 
| docker compose build                              |  Build all image service                                               |
| docker compose config                             |  Validate and view the Compose file                                    |
| docker compose scale __service-name__=__replica__ |  Scale special service(s)                                              |
| docker compose top                                |  Display the running processes                                         |
| docker compose run -rm -p 2022:22 web bash        |  Start web service and runs bash as its command, remove old container. |



### DOCKER SERVICES 



| Commandes                               -               | Définitions                                 |
|---------------------------------------------------------|------------------------------------------|
| docker service create __options__ __image__ __command__ |  Create new service                      |
| docker service inspect --pretty __service-name__        |  Display detailed information Service(s) |
| docker service ls                                       |  List Services                           |
| docker service ps                                       |  List the tasks of Services              |
| docker service scale __service-name__=__replica__           |  Scale special service(s)                |
| docker service update __option__ __service-name__          |  Update Service options                  |



### DOCKER STACK 



| Commandes                               -        | Définitions                                            |
|-------------------------------------------------|-----------------------------------------------------|
| docker stack ls                                 |  List all running applications on this Docker host  | 
| docker stack deploy -c __composefile__ _app-name__  |  Run the specified Compose file                     |
| docker stack services _app-name__                 |  List the services associated with an app           |
| docker stack ps _app-name__                       |  List the running containers associated with an app |
| docker stack rm _app-name__                       |  Tear down an application                           |


