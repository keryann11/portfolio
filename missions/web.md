---
# 🌐 Web
---
## Objectifs de la Mission
Cette mission avait pour but de découvrir et de mettre en œuvre les composants fondamentaux d'une stack web LAMP (Linux, Apache/Nginx, MariaDB, PHP) et de déployer des applications web courantes. Il s'agissait également d'appliquer les premières mesures de sécurité web.

## Compétences Développées
* **Administration de serveurs Web :** Installation et configuration de Nginx (et Apache pour GLPI).
* **Gestion de bases de données :** MariaDB et phpMyAdmin.
* **Déploiement d'applications :** WordPress, GLPI, DokuWiki.
* **Sécurité Web :** Redirection HTTPS, règles Fail2ban spécifiques aux applications web.
* **Dépannage :** Résolution de problèmes de configuration web et base de données.

## Outils et Technologies Utilisés
* **Système d'exploitation :** Debian ou Ubuntu Server
* **Serveurs Web :** Nginx, Apache2
* **Langage de script :** PHP (avec les extensions nécessaires)
* **Base de données :** MariaDB
* **Outil de gestion de BDD :** phpMyAdmin
* **Applications Web :** WordPress, GLPI, DokuWiki
* **Sécurité :** Fail2ban

## Déroulement de la Mission

### 1. Installation de la Stack Web (Nginx, PHP, MariaDB)
* **Installation de Nginx :** Configuration du serveur web pour servir des sites.
* **Installation de PHP-FPM :** Configuration de PHP pour fonctionner avec Nginx (FastCGI Process Manager).
* **Installation de MariaDB :** Mise en place du serveur de base de données, sécurisation initiale (`mysql_secure_installation`).
* **Création des bases de données et utilisateurs :** Préparation des bases pour chaque application.

* *Capture d'écran :* ![Configuration de Nginx pour PHP-FPM](images/mission-3/nginx-php-fpm-config.png)
    * (Montrer un extrait du fichier de configuration Nginx pour un site)
* *Capture d'écran :* ![Sécurisation de MariaDB](images/mission-3/mariadb-secure-installation.png)
    * (Montrer la fin de l'exécution de `mysql_secure_installation`)

### 2. Déploiement d'Applications Web

* **Déploiement de WordPress :**
    * Téléchargement des fichiers WordPress.
    * Configuration du fichier `wp-config.php` avec les informations de la base de données.
    * Configuration d'un hôte virtuel Nginx pour WordPress.
    * Finalisation de l'installation via l'interface web.
    * **À faire :** Création d'une page de blog simple.
        * *Capture d'écran :* ![Page de blog WordPress fonctionnelle](images/mission-3/wordpress-blog-page.png)
            * (Montrer la page de blog créée sur ton WordPress)

* **Déploiement de GLPI (Gestion Libre de Parc Informatique) :**
    * Téléchargement et installation de GLPI.
    * Configuration d'Apache pour GLPI (souvent plus simple avec Apache pour les premières versions de GLPI).
    * Configuration de la base de données et finalisation via l'installeur web.
    * **À faire :** Création d'un ticket de test.
        * *Capture d'écran :* ![Création d'un ticket GLPI](images/mission-3/glpi-ticket-creation.png)
            * (Montrer l'interface GLPI avec un ticket créé)

* **Déploiement de DokuWiki :**
    * Téléchargement et installation des fichiers DokuWiki.
    * Configuration d'un hôte virtuel Nginx.
    * Finalisation de l'installation.
    * **À faire :** Création d'une page de documentation.
        * *Capture d'écran :* ![Page de documentation DokuWiki](images/mission-3/dokuwiki-doc-page.png)
            * (Montrer une page de documentation que tu as créée sur DokuWiki)

### 3. Installation et Utilisation de phpMyAdmin
* **Installation de phpMyAdmin :** Accès simplifié aux bases de données MariaDB via une interface web.
* **Configuration avec Nginx :** S'assurer que phpMyAdmin est accessible via une URL dédiée.
* **À faire :** Réinitialisation d'un mot de passe via phpMyAdmin.
    * (Choisir une application, par exemple WordPress, et montrer la modification directe du mot de passe dans la table `wp_users` via phpMyAdmin).
    * *Capture d'écran :* ![Réinitialisation mot de passe WordPress via phpMyAdmin](images/mission-3/phpmyadmin-reset-password.png)
        * (Montrer la table `wp_users` et la ligne du mot de passe haché)

### 4. Sécurisation Web Additionnelle

* **Redirection HTTP vers HTTPS :**
    * Configuration de Nginx (ou Apache) pour rediriger automatiquement tout le trafic HTTP vers HTTPS (même si le certificat n'est pas encore en place sur cette VM locale, la configuration est prête pour l'avenir).
    * **À faire :** Vérification de la redirection (via `curl -v http://ton_ip` ou depuis un navigateur).
        * *Capture d'écran :* ![Configuration Nginx pour redirection HTTPS](images/mission-3/nginx-https-redirect.png)
            * (Montrer un bloc `server` de Nginx configuré pour la redirection)

* **Règle Fail2ban pour WordPress :**
    * Création d'une jail Fail2ban spécifique pour la page de connexion de WordPress (`wp-login.php`).
    * Configuration de la règle pour bannir les IPs après 3 tentatives de connexion échouées pendant 1 minute.
    * *Capture d'écran :* ![Configuration Jail Fail2ban WordPress](images/mission-3/fail2ban-wordpress-jail.png)
        * (Montrer le fichier de configuration de la jail WordPress pour Fail2ban)
    * *Capture d'écran :* ![Test de bannissement Fail2ban WordPress](images/mission-3/fail2ban-wordpress-test.png)
        * (Montrer des logs d'authentification WordPress et/ou la sortie de `fail2ban-client status wordpress-auth`)

## Défis Rencontrés et Solutions Apportées
* **Problème :** Erreurs "502 Bad Gateway" avec Nginx et PHP-FPM.
* **Solution :** Vérification des chemins des sockets PHP-FPM, des droits d'accès et redémarrage des services (`php-fpm` et `nginx`).
* **Problème :** Conflits entre Nginx et Apache lors de l'installation de GLPI.
* **Solution :** Utilisation d'un port différent pour Apache ou arrêt de Nginx pendant l'installation de GLPI, puis configuration pour qu'ils écoutent sur des ports ou hôtes virtuels distincts.
* **Problème :** Compréhension des expressions régulières pour les filtres Fail2ban sur les logs d'applications web.
* **Solution :** Utilisation d'outils de test d'expressions régulières et lecture de la documentation de Fail2ban pour affiner les filtres.

## Résultats Obtenus
Une stack web complète et fonctionnelle a été mise en place, permettant le déploiement de plusieurs applications clés. J'ai acquis une bonne compréhension des interactions entre Nginx, PHP, MariaDB et les applications. Des mesures de sécurité initiales ont été appliquées, posant les bases pour des déploiements web plus robustes.

---

[Retour à l'accueil](../README.md)
