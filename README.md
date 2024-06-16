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
- Avoir une clé API Google pour utiliser les services de Google dans Uniride. Vous pouvez générer une clé API dans le [Google Cloud Console](https://console.cloud.google.com/welcome/new?walkthrough_id=maps_enable_api).
- Avoir Python installé sur votre machine pour exécuter un script si nécessaire, afin de générer un SALT.
- Avoir Git d'installé sur la machine ou pouvoir télécharger ce repo et extraire le contenu.


## Installation et Configuration
1. Clonez ce dépôt `git clone https://github.com/DUT-Info-Montreuil/UniRide-DEPLOYMENT.git`.
2. Ajoutez vos certificats dans le dossier `/certs` à la racine (ATTENTION PAS D'AUTO SIGNÉ).
3. Modifiez le fichier `uniride-env-template.env` avec vos variables d'environnement. Certaines peuvent rester configuré par défaut.

### Génération du JWT_SALT au besoin

Le JWT_SALT est utilisé pour sécuriser les JSON Web Tokens (JWT). Pour générer un sel aléatoire, utilisez Python :

4. Créez un fichier Python et ajoutez le code suivant pour générer un salt aléatoire : 
   - `import bcrypt`
   - `salt = bcrypt.gensalt()`
   - `print(salt)`
5. Faire un pip install de bcrypt
   - `pip install bcrypt`

6. Exécutez le fichier Python pour obtenir le JWT_SALT :
   - `python nom_du_fichier.py`
7. Copiez le sel généré entre guillemet et utilisez-le dans votre configuration d'environnement pour sécuriser les JWT.

8. Ouvrez un terminal et placez-vous au niveau du dossier cloné.
9. Lancez les services avec Docker Compose : `docker-compose --env-file ./env/uniride-env-template.env up --build`

## Configuration d'un compte adminstrateur Uniride
Pour configurer un compte administrateur pour UniRide, suivez les étapes ci-dessous :
1. Ouvrez un terminal et exécutez la commande suivante pour accéder à la base de données à l'intérieur du conteneur Docker :
   - `docker exec -it uniride_db psql -U university_uniride -d uniride`
2. Une fois connecté à la base de données, exécutez la commande SQL suivante pour créer un compte administrateur. Remplacez simplement la valeur de ADDRESSE_MAIL_UNIVERSITAIRE_ADMIN par l'adresse mail universitaire de l'administrateur:
   - `INSERT INTO uniride.ur_user(r_id, u_login, u_lastname, u_student_email, u_password, u_timestamp_creation, u_timestamp_modification,  u_gender, u_firstname, u_phone_number, u_email_verified, u_status, u_description) VALUES (0, 'admin', 'Admin', 'ADDRESSE_MAIL_UNIVERSITAIRE_ADMIN', 'MOT_DE_PASSE_HASH_NE_PAS_MODIFIE', DEFAULT, DEFAULT, 'H', 'Tremblay', '0000000000', true, 3, '');`
3. Ensuite, allez sur le site et sur la page 'Mot de passe oublié', puis renseignez votre adresse mail et réinitialisez votre mot de passe.
4. Tout est bon ! Vous pouvez maintenant accéder à l'ensemble des fonctionnalités d'UniRide.

## Information accès à Uniride
1. Accédez à l'application sur le port 4200 en https après le déploiement.
2. Si vous utilisez des certificats auto-signés (!!! EN LOCAL UNIQUEMENT !!!), autorisez l'accès au site "non protégé" dans votre navigateur en ouvrant la console de développement et en cliquant sur l'URL du backend.

## Explications des Services

- **`uniride_frontend`**: Récupère et lance le frontend d'UniRide.
- **`uniride_backend`**: Récupère et lance le backend d'UniRide.
- **`uniride_redis`**: Utilisé pour la mise en cache d'UniRide.
- **`uniride_db`**: Gestion du stockage et des données d'UniRide.

## Explications des Dossiers et Fichiers

1. **Dossier `certs`**: Contient les certificats utilisés par les parties backend et frontend d'UniRide.
2. **Dossier `documents`**: Stocke tous les documents fournis par les utilisateurs d'UniRide.
3. **Dossier `postgres-data`**: Sauvegarde votre base de données localement même si votre docker redémarre.

Ces dossiers et fichiers jouent des rôles spécifiques dans le fonctionnement et la gestion des données d'UniRide, contribuant ainsi à la robustesse et à la performance de l'application.

## Auteur

- [CHOUCHANE Rayan / Nayren23](https://github.com/Nayren23)
- [HAMIDI Yassine / TheFanaticV2](https://github.com/TheFanaticV2)
- [BOUAZIZ Ayoub / Ayoub-Bouaziz](https://github.com/Ayoub-Bouaziz)
- [YANG Steven / G8LD](https://github.com/G8LD)
- [FAURE Grégoire / Pawpawzz](https://github.com/Pawpawzz)

## Licence

Ce projet est sous licence `GNU General Public License v3.0`. Consultez le fichier `LICENSE.md` pour plus de détails.
