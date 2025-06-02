# Conteneurisation d'une application Next.js 

Voici un squelette d'application Next.JS simple générée via un bête `create-next-app`

## Prérequis

Installer Docker :
- Docker CLI (En WSL ou sur système Unix directement)
- Docker For Windows
- Docker For Mac

## Objectifs

Vous devez réaliser **un Dockerfile** capable de construire et exécuter l'application Next.JS affichant la page d'accueil Next.JS.
Vous devrez réussir à :
1. Build l'image via Docker,
2. Vérifier la taille de l'image,
3. Lancer le conteneur à partir de votre image,
4. Afficher la landing page depuis votre navigateur (http://localhost:3000/)

## Consignes et contraintes

Pas d'utilisation d'image préconstruite :
- **Image de base :** `debian:bookworm` ou `ubuntu:latest`
- **Installation des dépendances systèmes** : installation via `apt-get` dépendances classiques pour node (`curl`, `gnupg`, `build-essential`, ...)
- **Versions de Node :** 22 (voir la documentation officielle pour installer)
- **Package manager :**  Utiliser `pnpm` (à activer dans l'image)
- **La page doit être consultable depuis le conteneur.**

## Comment tu run l'app Next.JS ?

Commandes à lancer pour lancer l'application Next.JS :

```bash 
# Commande pnpm pour lancer l'app une fois pnpm installé 
pnpm start
```
Petit malin, tu peux vérifier les commandes dans le fichier `package.json` si tu souhaites pimper un peu tes commandes !

Pour consulter la page dans son navigateur : [http://localhost:3000](http://localhost:3000)

## Ressources utiles

- Docker : https://docs.docker.com/desktop/
- Next.JS : https://nextjs.org/docs
- Node.JS : https://nodejs.org/en/download/

# T'as terminé plus tôt petit malin ?

Cette fois-ci, tu vas réaliser **un Dockerfile** bien plus simple et léger pour l'application Next.JS.
- L'image doit être basée sur Alpine Linux :
	- **Image de base :** `node:22-alpine`
- On ne veut pas de fichiers inutiles sur l'image du conteneur (bonne pratique : utilises un fichier `.dockerignore`)
- Vérifie bien que l'image est légère :
	- `docker images` et https://github.com/wagoodman/dive sont tes amis.

## Tu veux manipuler du volume ?

Récupère une image officielle de **PostgreSQL** ou autre base de données :

```bash
docker pull postgres:latest
```

## Consignes

1. Lance un conteneur du serveur :
```bash
docker run --name database -p 5432:5432 -e POSTGRES_PASSWORD=<met ton password ici> -d postgres
```

2. Connecte-toi sur le serveur via PGAdmin (https://www.pgadmin.org/),
3. Crée une base de données et une table "personne" avec : (ID, nom, prénom, adresse mail),
4. Insère une donnée (INSERT INTO),
5. Récupère cette données (SELECT),
6. Stop le container, puis refais les étapes 1, 2 et 5 : Quel résultat obtiens-tu ?
7. Après Stop le container, supprime le, puis refais les étapes 1, 2 et 5 : Quel résultat obtiens-tu ?

**Trouves un moyen de supprimer le conteneur sans perdre les données que tu as généré.**