# Projet avec Docker Compose

Ce projet utilise Docker Compose pour orchestrer une application multi-conteneurs comprenant un serveur MongoDB, un backend Node.js, et un frontend React.

## Structure du projet

- **MongoDB** : Base de données utilisée pour stocker les données de l'application.
- **Backend** : Application Node.js qui gère la logique métier.
- **Frontend** : Application React qui sert l'interface utilisateur.

## Prérequis

- [Docker](https://www.docker.com/get-started) doit être installé sur votre machine.
- [Docker Compose](https://docs.docker.com/compose/install/) doit être installé.

## Configuration

Le fichier `docker-compose.yml` inclut les configurations pour trois services principaux :

### Services

1. **MongoDB**:
   - Utilise l'image officielle de MongoDB.
   - Monte un volume pour persister les données à `/data/db`.
   - Configure les variables d'environnement pour définir le nom d'utilisateur et le mot de passe root.

2. **Backend**:
   - Construit l'image Docker à partir du répertoire `./backend` en utilisant le `Dockerfile` correspondant.
   - Expose le service sur le port 80.
   - Monte des volumes pour les logs, le code source du backend, et les modules Node.js.
   - Dépend du service MongoDB pour fonctionner correctement.

3. **Frontend**:
   - Construit l'image Docker à partir du répertoire `./frontend` en utilisant le `Dockerfile` correspondant.
   - Expose le service sur le port 3000.
   - Monte un volume pour le code source du frontend.
   - Dépend du service Backend pour fonctionner correctement.

### Volumes

- **data**: Utilisé par MongoDB pour persister les données.
- **logs**: Utilisé par le backend pour stocker les logs.

## Commandes Docker Compose

### Démarrer les services

Pour démarrer tous les services définis dans le fichier `docker-compose.yml`, utilisez :

```bash
docker-compose up
```
#### Pour exécuter les services en arrière-plan (détaché) :
```bash
docker-compose up -d --build
```
#### Arrêter les services

```bash
docker-compose down
```
#### Nettoyer les volumes

```bash
docker-compose down -v
```