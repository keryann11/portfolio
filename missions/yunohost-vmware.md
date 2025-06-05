---
# 🔧 YunoHost (VMware)
---
## Objectifs de la Mission
Cette mission avait pour objectif d'explorer la solution d'auto-hébergement YunoHost en l'installant localement dans un environnement virtualisé (VMware). Le but principal était de reproduire les services web et les applications précédemment déployés de manière individuelle (WordPress, DokuWiki, etc.) au sein de l'écosystème YunoHost.

## Compétences Développées
* **Auto-hébergement :** Compréhension des principes et de la mise en œuvre d'une solution d'auto-hébergement.
* **Administration YunoHost :** Installation, configuration initiale et gestion des applications via l'interface d'administration.
* **Virtualisation :** Gestion d'une machine virtuelle dédiée à YunoHost.
* **Déploiement d'applications :** Installation simplifiée d'applications via le catalogue YunoHost.
* **Dépannage :** Résolution de problèmes liés à l'installation ou à la configuration des services YunoHost.

## Outils et Technologies Utilisés
* **Hyperviseur :** VMware Workstation Pro
* **Système d'exploitation :** Debian (sans GUI)
* **Solution d'auto-hébergement :** YunoHost
* **Applications YunoHost :** Wiki (basé sur DokuWiki ou autre), Blog (basé sur WordPress ou autre), Notes, etc. (reproduisant les services des missions précédentes)

## Déroulement de la Mission

### 1. Préparation de la Machine Virtuelle
* **Création d'une nouvelle VM :** Mise en place d'une machine virtuelle Debian minimale spécifiquement dédiée à YunoHost sur VMware Workstation Pro.
* **Configuration réseau :** S'assurer que la VM a une adresse IP fixe pour une meilleure stabilité.

* *Capture d'écran :* ![Configuration VM Debian pour YunoHost](images/mission-5/vm-debian-yunohost-config.png)
    * (Montrer les paramètres de la VM Debian avant installation de YunoHost)

### 2. Installation de YunoHost
* **Installation sur Debian :** Suivi des instructions officielles de YunoHost pour une installation sur une Debian fraîchement installée, sans interface graphique.
* **Configuration post-installation :** Premiers pas avec l'interface d'administration web de YunoHost, création du premier utilisateur, configuration du domaine local (ex: `yunohost.local`).

* *Capture d'écran :* ![Installation de YunoHost en ligne de commande](images/mission-5/yunohost-install-cli.png)
    * (Montrer la fin du script d'installation YunoHost)
* *Capture d'écran :* ![Interface d'administration YunoHost - Premier écran](images/mission-5/yunohost-admin-interface.png)
    * (Montrer la page de connexion ou le tableau de bord initial de YunoHost)

### 3. Déploiement et Reproduction des Services Précédemment Testés
* **Utilisation du catalogue d'applications YunoHost :** Navigation dans l'interface d'administration pour installer les applications équivalentes à celles des missions précédentes.
* **Déploiement de services "Blog" :** Installation de l'application "Blog" (souvent une version de WordPress ou Ghost packagée pour YunoHost).
* **Déploiement de services "Wiki" :** Installation de l'application "Wiki" (souvent une version de DokuWiki ou MediaWiki packagée).
* **Déploiement d'autres services (Notes, etc.) :** Exploration et installation d'autres applications pertinentes pour la gestion de l'information.
* **Configuration des services :** Adaptation des paramètres si nécessaire pour chaque application installée.

* *Capture d'écran :* ![Catalogue d'applications YunoHost](images/mission-5/yunohost-app-catalog.png)
    * (Montrer la liste des applications disponibles dans YunoHost)
* *Capture d'écran :* ![Application Blog déployée via YunoHost](images/mission-5/yunohost-blog-app.png)
    * (Montrer la page d'accueil d'un blog déployé via YunoHost)
* *Capture d'écran :* ![Application Wiki déployée via YunoHost](images/mission-5/yunohost-wiki-app.png)
    * (Montrer la page d'accueil d'un wiki déployé via YunoHost)

## Défis Rencontrés et Solutions Apportées
* **Problème :** Compréhension de la gestion des domaines et des utilisateurs au sein de YunoHost pour chaque application.
* **Solution :** Consultation de la documentation officielle de YunoHost et exploration des options de configuration dans l'interface d'administration.
* **Problème :** Parfois, certaines applications ne s'installent pas du premier coup en raison de dépendances ou de conflits.
* **Solution :** Analyse des logs d'installation de YunoHost et recherche des solutions sur le forum de la communauté YunoHost.

## Résultats Obtenus
Une instance YunoHost fonctionnelle a été mise en place localement, démontrant la capacité à consolider plusieurs services web et de gestion sous une seule interface d'auto-hébergement. Cette mission a permis de comparer l'installation manuelle de services avec la simplicité du déploiement via un CMS d'auto-hébergement comme YunoHost.

---

[Retour à l'accueil](../README.md)
