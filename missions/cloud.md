---
# 🌐 Multi-Cloud
---
## Objectifs de la Mission
Cette mission a marqué une étape cruciale : le déploiement de services sur des infrastructures accessibles publiquement et la découverte des environnements multi-cloud. L'objectif était de maîtriser la configuration DNS, le routage, la sécurisation SSL et d'appréhender les spécificités de plateformes cloud majeures comme AWS, Azure et GCP.

## Compétences Développées
* **Administration DNS :** Gestion de noms de domaine et de zones DNS chez un registrar.
* **Sécurisation SSL/TLS :** Déploiement et gestion de certificats Let's Encrypt avec Certbot.
* **Sécurité Serveur :** Application de mesures de sécurité de base sur des serveurs publics (Fail2ban, UFW).
* **Cloud Computing :** Déploiement de services sur AWS, Azure, GCP ; identification des différences fondamentales entre ces plateformes.
* **Gestion de VPS :** Configuration et administration d'un serveur privé virtuel (VPS) chez OVH.

## Outils et Technologies Utilisés
* **Noms de domaine :** OVH
* **VPS :** OVH
* **Certificats SSL :** Let's Encrypt
* **Outil ACME Client :** Certbot
* **Pare-feu :** UFW
* **Détection d'intrusion :** Fail2ban
* **Plateformes Cloud :** AWS (Amazon Web Services), Microsoft Azure, Google Cloud Platform (GCP)

## Déroulement de la Mission

### 1. Acquisition et Configuration du Domaine Réel et VPS OVH
* **Commande d'un domaine réel :** Choix et enregistrement d'un nom de domaine via OVH.
* **Commande d'un VPS :** Sélection et provisionnement d'un serveur privé virtuel chez OVH.
* **Configuration DNS :**
    * Mise à jour des enregistrements `A` et `CNAME` dans la zone DNS chez OVH pour faire pointer le domaine vers l'adresse IP publique du VPS.
    * Configuration d'enregistrements spécifiques pour les sous-domaines si nécessaire (ex: `www`).
* **Routage :** S'assurer que le trafic arrive bien sur le VPS depuis le domaine.

* *Capture d'écran :* ![Configuration DNS OVH](images/mission-4/ovh-dns-config.png)
    * (Ajoute ici une capture d'écran montrant ta zone DNS OVH avec les enregistrements `A` ou `CNAME` configurés)

### 2. Déploiement et Configuration SSL avec Let's Encrypt
* **Installation de Nginx (ou Apache) :** Mise en place du serveur web sur le VPS.
* **Installation de Certbot :** Utilisation de l'outil Certbot pour automatiser l'obtention et l'installation de certificats SSL/TLS gratuits de Let's Encrypt.
* **Configuration SSL :** S'assurer que Nginx est configuré pour servir le site en HTTPS.
* **Vérification de Certbot :**
    * Confirmation que le certificat est bien généré et que la redirection HTTP vers HTTPS fonctionne automatiquement.
    * Vérification de la validité du certificat via le navigateur.

* *Capture d'écran :* ![Exécution de Certbot pour Nginx](images/mission-4/certbot-nginx.png)
    * (Ajoute une capture montrant la sortie de la commande Certbot)
* *Capture d'écran :* ![Site en HTTPS avec certificat valide](images/mission-4/https-site.png)
    * (Ajoute une capture montrant ton site avec le cadenas de sécurité dans la barre d'adresse du navigateur)

### 3. Application des Sécurisations de Base
* **Configuration d'UFW :** Mise en place des règles de pare-feu pour autoriser uniquement les ports essentiels (SSH sur un port non standard, 80, 443) et bloquer le reste.
* **Installation et configuration de Fail2ban :**
    * Mise en place de jails pour SSH et les services web (Nginx, si nécessaire).
    * Configuration des règles de bannissement (par exemple, 3 tentatives pour un bannissement d'une heure).

* *Capture d'écran :* ![Statut UFW sur VPS](images/mission-4/ufw-status-vps.png)
    * (Ajoute une capture montrant `sudo ufw status` sur ton VPS)
* *Capture d'écran :* ![Jail Fail2ban active sur VPS](images/mission-4/fail2ban-jail-status.png)
    * (Ajoute une capture montrant `sudo fail2ban-client status` ou `sudo fail2ban-client status sshd`)

### 4. Déploiement Multi-Cloud (AWS, Azure, GCP)
* **Découverte des plateformes :** Exploration des consoles et des services de base d'AWS, Azure et GCP.
* **Déploiement d'un service simple sur chaque plateforme :**
    * *Exemple AWS :* Déploiement d'une instance EC2 avec une page web simple.
    * *Exemple Azure :* Création d'une machine virtuelle ou d'un App Service basique.
    * *Exemple GCP :* Déploiement d'une instance Compute Engine.
* **Documentation des différences :** Analyse et comparaison des interfaces, de la terminologie, des modèles de tarification (même si non facturé), et des méthodes de déploiement propres à chaque fournisseur.

* *Capture d'écran :* ![Console AWS - Instance EC2](images/mission-4/aws-ec2-instance.png)
    * (Ajoute une vue de la console AWS avec une instance en cours)
* *Capture d'écran :* ![Console Azure - Machine virtuelle](images/mission-4/azure-vm.png)
    * (Ajoute une vue de la console Azure avec une VM ou un App Service)
* *Capture d'écran :* ![Console GCP - Compute Engine](images/mission-4/gcp-compute-engine.png)
    * (Ajoute une vue de la console GCP avec une instance Compute Engine)

## Défis Rencontrés et Solutions Apportées
* **Problème :** Complexité initiale des consoles Cloud (AWS, Azure, GCP) et de leur jargon spécifique.
* **Solution :** S'appuyer sur la documentation officielle des fournisseurs, des tutoriels spécifiques et des guides de démarrage rapide pour chaque plateforme.
* **Problème :** Configuration DNS et propagation des enregistrements, entraînant des délais pour la mise en ligne du site.
* **Solution :** Vérification régulière via des outils de propagation DNS (ex: `dig`, `nslookup` ou outils en ligne) et patience.
* **Problème :** Gestion des groupes de sécurité (security groups) ou Network Security Groups (NSG) dans le cloud, qui fonctionnent comme des pare-feux additionnels.
* **Solution :** Apprendre à configurer ces règles de sécurité spécifiques au cloud pour permettre l'accès aux services déployés.

## Résultats Obtenus
J'ai réussi à déployer un service sur une infrastructure publique avec un nom de domaine réel et un certificat SSL valide, garantissant une communication sécurisée. L'exploration multi-cloud a permis de comprendre les bases de trois plateformes majeures, soulignant leurs similitudes et leurs différences, une compétence clé pour l'avenir de l'IT. Le tout a été sécurisé par des outils de base comme UFW et Fail2ban.

---

[Retour à l'accueil](../README.md)
