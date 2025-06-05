# 🧪 YunoHost sur OpenStack (test)

## Objectifs de la Mission
Cette mission avait pour objectif de répliquer l'expérience YunoHost d'une installation locale vers un environnement de cloud privé : OpenStack. Il s'agissait de déployer une instance YunoHost sur une infrastructure OpenStack, de la configurer de manière similaire à l'environnement local, et d'explorer l'ajout de nouveaux services pour tester la flexibilité de la plateforme.

## Compétences Développées
* **Cloud Privé :** Interaction avec une infrastructure OpenStack (création d'instances, gestion de réseaux, groupes de sécurité).
* **Déploiement en Environnement Complexe :** Adaptation de procédures d'installation à un contexte cloud.
* **Administration YunoHost :** Gestion et configuration avancée de YunoHost dans un environnement public/privé.
* **Réseaux Cloud :** Compréhension des concepts de réseaux virtuels et IPs flottantes dans OpenStack.
* **Dépannage avancé :** Résolution de problèmes de connectivité et de déploiement spécifiques à OpenStack.

## Outils et Technologies Utilisés
* **Plateforme de Cloud Privé :** OpenStack (accès via Horizon ou API/CLI)
* **Système d'exploitation :** Debian (pour l'instance YunoHost)
* **Solution d'auto-hébergement :** YunoHost
* **Composants OpenStack :** Instances (Nova), Réseaux (Neutron), Images (Glance), Clés SSH.

## Déroulement de la Mission

### 1. Provisionnement d'une Instance sur OpenStack
* **Création d'une instance :** Lancement d'une nouvelle machine virtuelle (instance) sur OpenStack, basée sur une image Debian.
* **Configuration réseau :** Attachement de l'instance à un réseau virtuel et association d'une adresse IP flottante (publique) pour la rendre accessible depuis l'extérieur.
* **Gestion des clés SSH :** Utilisation de paires de clés SSH pour la connexion sécurisée à l'instance.
* **Configuration des Security Groups :** Mise en place des règles de pare-feu OpenStack pour autoriser le trafic entrant nécessaire (SSH, HTTP, HTTPS).

* *Capture d'écran :* ![Tableau de bord OpenStack - Lancement d'une instance](images/mission-6/openstack-launch-instance.png)
    * (Montrer l'interface Horizon lors du lancement d'une nouvelle instance)
* *Capture d'écran :* ![Détails de l'instance OpenStack avec IP flottante](images/mission-6/openstack-instance-ip.png)
    * (Montrer les détails de l'instance dans Horizon, incluant l'IP flottante)

### 2. Installation et Configuration de YunoHost sur l'Instance OpenStack
* **Connexion SSH :** Accès à l'instance via SSH en utilisant la clé privée associée.
* **Installation de YunoHost :** Exécution du script d'installation de YunoHost sur la Debian de l'instance OpenStack.
* **Configuration du domaine :** Configuration du domaine YunoHost avec l'adresse IP flottante ou un nom de domaine réel si disponible en test.

* *Capture d'écran :* ![Connexion SSH à l'instance OpenStack](images/mission-6/ssh-to-openstack-instance.png)
    * (Montrer une session SSH connectée à l'instance OpenStack)
* *Capture d'écran :* ![Interface d'administration YunoHost sur OpenStack](images/mission-6/yunohost-openstack-admin-interface.png)
    * (Montrer le tableau de bord YunoHost accessible via l'IP publique de l'instance)

### 3. Configuration Similaire à la Mission Locale et Ajout de Nouveaux Services
* **Déploiement des services de base :** Installation des applications "Blog", "Wiki", etc., comme dans la mission locale, pour assurer la parité des fonctionnalités.
* **Ajout de nouveaux services (en test) :** Exploration et installation de nouvelles applications du catalogue YunoHost non testées précédemment, pour évaluer la capacité d'OpenStack à supporter une charge plus variée.
* **Préparation d'un environnement presque final :** Configuration de l'instance et de YunoHost de manière à ce qu'il soit robuste et proche d'une version "production", tout en restant flexible pour de futurs ajustements.

* *Capture d'écran :* ![Liste des applications YunoHost déployées sur OpenStack](images/mission-6/yunohost-openstack-apps.png)
    * (Montrer la liste des applications installées sur YunoHost via l'interface d'admin)
* *Capture d'écran :* ![Exemple de nouveau service déployé sur YunoHost OpenStack](images/mission-6/yunohost-new-service-openstack.png)
    * (Montrer une application spécifique fraîchement installée et fonctionnelle sur YunoHost OpenStack)

## Défis Rencontrés et Solutions Apportées
* **Problème :** Compréhension des mécanismes de réseau d'OpenStack (réseaux internes, routeurs virtuels, IPs flottantes) qui diffèrent des réseaux locaux.
* **Solution :** Étude approfondie de la documentation Neutron d'OpenStack et expérimentation avec la création de différents types de réseaux.
* **Problème :** Configuration initiale des Security Groups bloquant l'accès à YunoHost.
* **Solution :** Ajustement minutieux des règles des Security Groups pour autoriser les ports 80 (HTTP), 443 (HTTPS) et le port SSH personnalisé.
* **Problème :** Performance variable de l'instance OpenStack en phase de test.
* **Solution :** Surveillance de l'utilisation des ressources via l'interface Horizon et ajustement de la taille de l'instance (flavor) si nécessaire.

## Résultats Obtenus
J'ai réussi à déployer et configurer une instance YunoHost sur une infrastructure OpenStack, prouvant ma capacité à travailler avec des plateformes de cloud privé. La reproduction des services existants et l'ajout de nouveaux ont confirmé la versatilité de YunoHost dans un environnement distant. Cette mission a préparé le terrain pour un déploiement en production, en mettant en lumière les ajustements nécessaires à une configuration quasi-finale.

---

[Retour à l'accueil](../README.md)
