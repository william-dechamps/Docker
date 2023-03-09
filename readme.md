## TP1 Docker

### Exercice 5

**a**. Récupérer l’image sur le Docker Hub :  
`docker pull nginx`

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
