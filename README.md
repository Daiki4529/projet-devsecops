# Structure du projet

- Dockerfile : Fichier de configuration Docker pour l'application Node.js.
- package.json : Liste des dépendances Node.js et script de démarrage.
- server.js : Code source principal de l'API Express.
- init.sql : Script SQL pour créer la table users dans PostgreSQL.
- Dossier /kubernetes : Fichiers de configuration Kubernetes pour déployer l'application et la base de données.

### Dépendances
- [express](https://www.npmjs.com/package/express)
- [body-parser](https://www.npmjs.com/package/body-parser)
- [node-postgres](https://www.npmjs.com/package/pg)

### Construire les conteneurs Docker
````bash
docker build -t jbarthesilv/nodejs-api .
docker push jbarthesilv/nodejs-api
````

### Déploiement avec Kubernetes
Démarrer Minikube (si vous utilisez Minikube)
````bash
minikube start
````

Appliquer les fichiers de configuration Kubernetes
````bash
kubectl apply -f kubernetes/db-init-configmap.yaml
kubectl apply -f kubernetes/deployment-postgrey.yaml
kubectl apply -f kubernetes/service-db.yaml
kubectl apply -f kubernetes/deployment-nodejs.yaml
kubectl apply -f kubernetes/service-web.yaml
````

Accéder à l'API
````bash
minikube service nodejs-service
````

### Routes disponibles
- GET /users : Récupérer tous les utilisateurs.
- POST /users : Créer un utilisateur.
- PATCH /users/:id : Modifier un utilisateur.
- DELETE /users/:id : Supprimer un utilisateur.

### Détails des fichiers Kubernetes
- db-init-configmap.yaml : Contient le script SQL pour initialiser la base de données.
- deployment-postgrey.yaml : Déploie un conteneur PostgreSQL et monte le script d'initialisation.
- service-db.yaml : Crée un service interne pour exposer PostgreSQL à l'application Node.js.
- deployment-nodejs.yaml : Déploie l'API Node.js en définissant les variables d'environnement pour la connexion à PostgreSQL.
- service-web.yaml : Expose l'API Node.js via un service de type NodePort.