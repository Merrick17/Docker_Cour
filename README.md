# Docker_Course

### Docker Lists
```BASH
# lister les images
docker images
# lister les containers
docker container list
# lister les volumes
docker volume list
```
## Les Actions
### supprimer une image ou plusieurs
```BASH
docker image rm #ID_IMAGE
docker image rm #ID_IMAGE1 ID_IMAGE2 ID_IMAGE3 ...
```
### Lancer de conteneurs
##### LES MODES
```BASH
# mode detaché c(est a dire lancer en arriere plan
docker container run -d #image_name:version 
# mode interactive c'est a dire lancer une conteneur en mode bash
docker container run -it #image_name:version mode
# example on va lancer une conteneur nginx
docker container run -it nginx:latest /bin/bash
# ou
docker container run -d nginx:latest
```

##### L'EXPOSE DE PORTS
```BASH
# expose_port
#deux type d'expose
# -p port:portOfContainer : forcer le num de port
# -P : port aleatoire
#example on a lancer une conteneur nginx
docker container run -d -p 80:80 nginx:latest
# ou 
docker container run -d -P nginx:latest
```

##### LES VOLUMES
```BASH
# on a deux mode de volume on a un volume de montage ou un volume de conteneur
# example dans un conteneur nginx de volume de conteneur
docker container run -d -v /data nginx:latest
# example de volume de montage dans ce cas le volume a monter sur local
docker container run -d -v /home/safwen:/var/www/html nginx:latest
```

##### LES ENVIRONMENT
```BASH
# dans le cas de database ne marche que avec les environment.
#example les env de MYSQL
- MYSQL_ROOT_PASSWORD
- MYSQL_DATABASE
- MYSQL_USER
```

##### LES LIENS
```BASH
# dans ce example on créer deux conteneur example nginx et mysql.
docker container run -d --name database -e MYSQL_ROOT_PASSWORD="safouaane" mysql:5.7
docker container run -d --name webserver --links database nginx:latest
```

### Execution d'un conteneur
```BASH
#L'exec dans le conteneur elle marche si le conteneur est ouvert.
# example sur une conteneur nginx démarrer.
docker container exec -it #ID_Container #mode
# si on l'id 011615fa
docker container exec -it 011615fa bash
```

### Afficher les informations d'un conteneur
```BASH
# pour afficher les log d'un conteneur : ID_CONTAINER : 011615fa
docker container logs 011615fa
# pour afficher les arborusance principale de conteneur:
docker container diff 011615fa
# pour inspecter tous les information d'un conteneur
docker container inspect 011615fa
```
