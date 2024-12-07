# Projet DevSecOps

Ce projet inclut le développement d'une application avec une architecture front-end, back-end et base de données, déployée sur Kubernetes en utilisant Minikube.

## Contenu du projet

- **Front-end** : Développement de l'interface utilisateur.
- **Back-end** : Développement de l'API et de la logique métier.
- **Base de données** : Gestion des données de l'application.
- **Kubernetes** : Orchestration des conteneurs.
- **Minikube** : Environnement de développement local pour Kubernetes.

## Prérequis

- Docker
- Kubernetes
- Minikube

## Installation

1. Cloner le dépôt :
    ```bash
    git clone <URL_DU_DEPOT>
    cd project
    ```

2. Démarrer Minikube :
    ```bash
    minikube start
    ```

3. Déployer les services sur Kubernetes :
    ```bash
    kubectl apply -f k8s/
    ```

## Utilisation

Accéder à l'application via l'URL fournie par Minikube :
```bash
minikube service <NOM_DU_SERVICE>
```

## Auteurs

- Jonas

## Licence

Ce projet est sous licence MIT.