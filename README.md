# UniRide-DEPLOYMENT
Déployez UniRide facilement avec Docker ! Ce repository contient des instructions détaillées pour la configuration et le lancement de UniRide.

[![forthebadge](https://forthebadge.com/images/badges/built-with-love.svg)](http://forthebadge.com)
[![forthebadge](https://forthebadge.com/images/badges/docker-container.svg)](http://forthebadge.com)  [![forthebadge](https://forthebadge.com/images/badges/built-by-developers.svg)](http://forthebadge.com)


## Description

UniRide-DEPLOYMENT vous guide étape par étape pour déployer UniRide, une solution de covoiturage dédiée aux étudiants. 
Simplifiez vos trajets vers l'université avec UniRide, rendant vos déplacements plus simples, économiques et conviviaux.

## Pré-requis

- Assurez-vous d'avoir Docker et Docker Compose installés sur votre système. 
  - Vous pouvez les télécharger depuis le [site officiel de Docker](https://www.docker.com/get-started). Si vous êtes nouveau dans l'utilisation de Docker, consultez la [documentation d'installation de Docker](https://docs.docker.com/get-docker/).


## Installation et Configuration
1. Clonez ce dépôt.
2. Ouvrez le projet dans votre éditeur de texte préféré.
3. Ajoutez vos certificats dans le dossier `/certs` à la racine.
4. Modifiez le fichier `uniride-backend-template.env` avec vos variables d'environnement.
5. Modifiez le fichier `uniride-frontend-template.env` avec vos variables d'environnement.
6. Modifiez le fichier `uniride-db-template.env` si vous utilisez un service de base de données.
7. Modifiez le fichier `uniride-pgadmin-template.env` si vous souhaitez avoir une interface web pour voir vos données.
8. Ouvrez un terminal et placez-vous au niveau du dossier cloné.
9. Tapez la commande : `docker-compose up --build`.
10. Une fois le déploiement terminé, vous pouvez accéder aux services UniRide via vos navigateurs préférés.
11. Maintenant, UniRide est opérationnel, simplifiant vos déplacements universitaires. Profitez d'une expérience de covoiturage plus simple, économique et conviviale !
12. Si vous utilisez des certificats auto-signés (<span style="color:red">!!! EN LOCAL UNIQUEMENT !!!</span>), autorisez l'accès au site "non protégé" dans votre navigateur en ouvrant la console de développement et en cliquant sur l'URL du backend.


## Explications des Services

- **`uniride_frontend`**: Récupère et lance le frontend de UniRide.
- **`uniride_backend`**: Récupère et lance le backend de UniRide.
- **`uniride_redis`**: Utilisé pour la mise en cache de UniRide.
- **`uniride_db`**: Gestion du stockage et des données de l'application.
- **`uniride_pgadmin`**: Permet la visualisation et la gestion des données de UniRide.


## Explications des Dossiers et Fichiers

1. **Dossier `certs`**: Contient les certificats utilisés par les parties backend et frontend d'UniRide.
2. **Dossier `documents`**: Stocke tous les documents fournis par les utilisateurs d'UniRide.
3. **Dossier `postgres-data` **: Sauvegarde votre base de données localement même si votre docker redémarre.

Ces dossiers et fichiers jouent des rôles spécifiques dans le fonctionnement et la gestion des données d'UniRide, contribuant ainsi à la robustesse et à la performance de l'application.

## Auteur

- [CHOUCHANE Rayan / Nayren23](https://github.com/Nayren23)
- [HAMIDI Yassine / TheFanaticV2](https://github.com/TheFanaticV2)
- [BOUAZIZ Ayoub / Ayoub-Bouaziz](https://github.com/Ayoub-Bouaziz)
- [YANG Steven / G8LD](https://github.com/G8LD)
- [FAURE Grégoire / Pawpawzz](https://github.com/Pawpawzz)


## Licence

Ce projet est sous licence `GNU General Public License v3.0`. Consultez le fichier `LICENSE.md` pour plus de détails.
