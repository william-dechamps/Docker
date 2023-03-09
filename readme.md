## TP1 Docker

### Exercice 5

**a**. Récupérer l’image sur le Docker Hub :  
``docker pull nginx`

**b**. Vérifier que cette image est présente en local :  
`docker images | grep nginx`

**c**. Créer un fichier index.html simple :  
`touch index.html && echo "<h1>Hello world!</h1>" > index.html`

**d**. Démarrer un conteneur et servir la page html créée précédemment à l’aide d’un volume :  
`docker run --name my_nginx -p 8080:80 -v ${PWD}/index.html:/usr/share/nginx/html/index.html -d nginx`

**e**. Supprimer le conteneur précédent et arriver au même résultat que précédemment à l’aide de la commande docker cp  
`docker container rm -f my_nginx`  
`docker run -p 8080:80 --name my_nginx -d nginx`  
`docker cp index.html nginx:/usr/share/nginx/html/`

### Exercice 6

**a**. A l’aide d’un Dockerfile, créer une image  
`touch Dockerfile`

Contenu du Dockerfile :  
`FROM nginx:latest`  
`COPY index.html /usr/share/nginx/html/`

`docker build -t my_nginx_image .`

**b**. Exécuter cette nouvelle image de manière à servir la page html (commande
docker run)  
`docker run --name my_nginx -d -p 8080:80 my_nginx_image`

**c**. Quelles différences observez-vous entre les procédures 5. et 6. ?

Le but de ces exercices et d'exécuter un serveur web dans un conteneur Docker.

Dans l'exercice 5, il n'est pas demandé de créer un Dockerfile, donc de créer une image personnalisé à partir de l'image de nginx.  
Cela implique de devoir rajouter des étapes comme la copie du fichier html dans le conteneur ou d'utiliser des volumes.

Dans cet exercice, il est demandé de créer un Dockerfile, donc de créer une image personnalisé à partir de l'image de nginx.  
Cela n'implique pas d'étapes supplémentaires, car j'ai inclus la copie des fichiers dans l'image personnalisé.
