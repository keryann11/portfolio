---
# 🔐 Sécurisation d'une Machine Linux 
---
## Objectifs de la Mission
Cette mission avait pour but de renforcer la sécurité d'une machine Linux (Debian ou Ubuntu, sans GUI) fraîchement installée. L'objectif était de la prémunir contre les accès non autorisés et les attaques courantes par force brute, tout en facilitant l'administration à distance sécurisée.

## Compétences Développées
* **Administration Linux :** Gestion de services, configuration système.
* **Sécurité des Systèmes :** Durcissement (hardening) de serveurs, gestion de pare-feu, détection d'intrusions.
* **Gestion de l'accès à distance :** Configuration sécurisée de SSH.

## Outils et Technologies Utilisés
* **Système d'exploitation :** Debian (sans GUI) ou Ubuntu Server (sans GUI)
* **SSH (Secure Shell) :** Client et serveur pour l'accès distant sécurisé.
* **UFW (Uncomplicated Firewall) :** Outil de gestion simplifié d'iptables pour le pare-feu.
* **VS Code Server :** Environnement de développement à distance basé sur Visual Studio Code.
* **Fail2ban :** Cadre de détection d'intrusion qui bannit les adresses IP ayant échoué à se connecter.

## Déroulement de la Mission

### 1. Installation et Configuration Initiale de SSH
* **Installation du serveur SSH :** Vérification ou installation du paquet `openssh-server`.
* **Modification du port par défaut :** Changement du port SSH (par exemple, de 22 à un port non standard comme 2222) pour réduire les tentatives de connexion automatisées.
* **Désactivation de l'authentification par mot de passe :** Mise en place de l'authentification par clé SSH (plus sécurisée) et désactivation des mots de passe.
* **Interdiction de la connexion root :** Empêcher l'utilisateur `root` de se connecter directement via SSH.

* *Capture d'écran :* ![Modification du fichier de configuration SSH](images/mission-2/ssh-config-edit.png)
    * (Ajouter une capture d'écran montrant des lignes modifiées dans `/etc/ssh/sshd_config`)
* *Capture d'écran :* ![Test de connexion SSH par clé](images/mission-2/ssh-key-auth-test.png)
    * (Ajouter une capture montrant une connexion réussie par clé et/ou un échec de connexion par mot de passe)

### 2. Configuration du Pare-feu UFW
* **Installation d'UFW :** Si non déjà présent.
* **Définition des règles par défaut :** Bloquer le trafic entrant par défaut et autoriser le trafic sortant.
* **Autorisation du nouveau port SSH :** Ouvrir uniquement le port SSH modifié (ex: 2222) et les autres ports nécessaires (ex: 80, 443 si web).
* **Activation du pare-feu :** Démarrer UFW et s'assurer qu'il s'active au démarrage.

* *Capture d'écran :* ![Commandes UFW pour autoriser le port SSH](images/mission-2/ufw-allow-ssh-port.png)
    * (Montrer la commande `sudo ufw allow 2222/tcp`)
* *Capture d'écran :* ![État d'UFW après configuration](images/mission-2/ufw-status.png)
    * (Montrer la sortie de `sudo ufw status verbose` ou `sudo ufw show added`)

### 3. Installation de VS Code Server
* **Téléchargement et exécution :** Installation de VS Code Server pour permettre l'accès et l'édition de fichiers via l'interface VS Code directement depuis mon poste de travail.
* **Configuration de l'accès :** Accès via SSH, facilitant l'administration des fichiers et la rédaction de scripts sans quitter l'IDE.

* *Capture d'écran :* ![Connexion VS Code Server réussie](images/mission-2/vscode-server-connect.png)
    * (Montrer VS Code connecté à la machine distante)

### 4. Installation et Configuration de Fail2ban
* **Installation de Fail2ban :** Ajout du paquet `fail2ban`.
* **Configuration de base :** Activation de la jail par défaut pour SSH.
* **Création de règles personnalisées :** Configuration de règles pour bannir les adresses IP après un certain nombre de tentatives de connexion échouées (par exemple, 3 récidives pour 1 heure).

* *Capture d'écran :* ![Fichier de configuration Fail2ban (jail.local)](images/mission-2/fail2ban-jail-local.png)
    * (Montrer des extraits de `/etc/fail2ban/jail.local` ou un fichier de jail personnalisé)
* *Capture d'écran :* ![Statut Fail2ban (banned IPs)](images/mission-2/fail2ban-status-banned.png)
    * (Montrer la sortie de `sudo fail2ban-client status sshd` ou `sudo fail2ban-client status`)

## Défis Rencontrés et Solutions Apportées
* **Problème :** Perte d'accès SSH après modification du port et activation d'UFW sans autoriser le nouveau port au préalable.
* **Solution :** Accès via la console VMware Workstation pour corriger la règle UFW, en ajoutant `sudo ufw allow <nouveau_port_ssh>/tcp` avant de redémarrer le service SSH.
* **Problème :** Compréhension des mécanismes de Fail2ban et ajustement des `findtime`, `maxretry` et `bantime` pour des scénarios de test.
* **Solution :** Lecture approfondie de la documentation et tests successifs pour valider l'efficacité des règles.

## Résultats Obtenus
La machine Linux est désormais significativement plus sécurisée contre les accès non autorisés et les attaques par force brute. L'accès SSH est renforcé par l'authentification par clé et un port non standard, le pare-feu UFW ne laisse passer que le trafic nécessaire, et Fail2ban assure une protection dynamique en cas de tentatives d'intrusion. L'administration à distance est facilitée et sécurisée grâce à VS Code Server.

---

[Retour à l'accueil](../README.md)
