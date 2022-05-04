# Essentiels Linux

==> [retour accueil](../..)

## Sommaire

- [Essentiels Linux](#essentiels-linux)
- [Sommaire](#sommaire)
- 1 - [Mise à jour des paquets](#1---mise-à-jour-des-paquets)
- 2 - [Passe super adminnistrateur](#2---passe-super-adminnistrateur)
    - 2.1 - [Base](#21---base)
    - 2.2 - [Debian - Ajout un utilisateur à la liste "sudoers" (admins)](#22---debian---ajout-un-utilisateur-à-la-liste-"sudoers"-admins)
- 3 - [Paquets utils](#3---paquets-utils)
- 4 - [Divers installations](#4---divers-installations)
    - 4.1 - [Installation de `ifconfig`](#41---installation-de-ifconfig)
    - 4.2 - [Insllation du serveur web Apache](#42---insllation-du-serveur-web-apache)
    - 4.3 - [Status du serveur web Apache et autres services](#43---status-du-serveur-web-apache-et-autres-services)
    - 4.4 - [Arrêter l'OS](#44---arrêter-los)
    - 4.5 - [Installation de Jenkins (testé pour Ubuntu 16.04 / 20.04.1 LTS)](#45---installation-de-jenkins-testé-pour-ubuntu-1604--20041-lts)
    - 4.6 - [Installation de Valet (testé pour Ubuntu 16.04 / 20.04.1 LTS)](#46---installation-de-valet-testé-pour-ubuntu-1604--20041-lts)
    - 4.7 - [Installation de Gitlab (testé pour Ubuntu 16.04 / 20.04.1 LTS)](#47---installation-de-gitlab-testé-pour-ubuntu-1604--20041-lts)

## 1 - Mise à jour des paquets

```
sudo apt update && apt upgrade && apt clean && apt purge
```

## 2 - Passe super adminnistrateur

### 2.1 - Base

Pour Debian :

```
sudo root
```

Pour Ubuntu :

```
sudo su
```

> ATTENTION : sachez qu'avec les droits de ce compte utilisateur, il faut absolument savoir ce que l'on fait afin de ne pas commettre d'erreur irréversible.

### 2.2 - Debian - Ajout un utilisateur à la liste "sudoers" (admins)

**Debian 11** - Problème de **sudoers** ?

Si vous chercher à exécuter des commande administrateur avec votre compte après l'installation de Débian11, une simple commande `sudo su` ou toutes aurtes commandes `sudo <commande>` affichera : 

```
<user> n'apparaît pas dans le fichiers sudoers. ce incident sera signalé.
```

Pour corriger cela, il faut se connecter avec le compte super admin `root` :

```
user@debian:~$ su root
Mot de passe :
root@debian:/home/user#
```

Ajouter un utilisateur à la liste des `sudoers`

```
sudo usermod -a -G sudo <user>
```

Vérifier le groupe utilisateur d'un utilisateur

```
<user> : <user> cdrom floppy sudo audio dip video plugdev netdev bluetooth scanner
```

Il n'ya plus qu'à redémarrer.

## 3 - Paquets utils

| Paquet | Détails | MacOS | Debian 11 | Ubuntu Desktop 22.04 LTS | Ubuntu Server 22.04 LTS |
|---|---|---|---|---|---|
| **Outils client** |
| `tree` | générateur d'arborescence de fichier sous forme d'arbre |✅ |✅ |✅ |✅ |
| `nano` | un éditeur de texte pour console |✅ |✅ |✅ |✅ |
| `xemacs21` | un éditeur de texte pour X Window |✅ |✅ |✅ |✅ |
| **Outils réseau** |
| `nmap` | scanner de ports libre |✅ |✅ |✅ |✅ |
| `hping3` | testeur de liaison par paquets |✅ |✅ |✅ |✅ |
| `net-tools` | un ensemble de programmes de contrôle du sous-système réseau du noyau Linux | ❌ | ✅ | ✅ | ✅ |
| `tcpdump` | un analyseur de paquets en ligne de commande |✅ |✅ |✅ |✅ |
| `mlocate` | |✅ |✅ |✅ |✅ |
| **Téléchargeur** |
| `curl` | téléchargeur |✅ |✅ |✅ |✅ |
| `wget` | téléchargeur | ✅ | ✅ [déjà installé] | ✅ | ✅ |
| **Certificats SSL** |
| `openssh-server` | un ensemble d'outils des communications sécurisées **SSH** | ✅ | ✅ [déjà installé] | ✅ | ✅ |
| `ca-certificates` | gestionnaire des certificats | ✅ | ✅ [déjà installé] | ✅ | ✅ |
| `letsencrypt` | générateur de certificat **SSL** | ✅ | ✅ [déjà installé] | ✅ | ✅ |
| **Serveur fichiers** |
|...||||||
|...||||||
| **Serveur mail** |
| `postfix` | serveur de mail |✅ |✅ |✅ |✅ |
| **Serveur web** |
| `apache2` | serveur web HTTP |✅ |✅ |✅ |✅ |
| `nginx` | serveur web |✅ |✅ |✅ |✅ |
| **Serveur de données - SQL** |
| `mysql-client-core-5.7` | mysql server 5.7 |✅ |✅ |✅ |✅ |
| `mysql-server` | mysql server |✅ |✅ |✅ |✅ |
| **Serveur d'automatisation** |
| `jenkins` | outil open source de serveur d'automatisation |✅ |✅ |✅ |✅ |
| **Langages et compilateurs** |
| `gcc` | compilateur langage C |✅ |✅ |✅ |✅ |
| `php` | compilateur PHP |✅ |✅ |✅ |✅ |
| `python3` | compilateur Python |✅ |✅ |✅ |✅ |
| `default-jre` | Java Runtime Environnement |✅ |✅ |✅ |✅ |
| **Debian** : `openjdk-8-jdk` **Ubuntu** : `default-jdk` ou `openjdk-8-jre-headless` | Java Developpement Kit (compilateur java inclu) | ✅ | ✅ Dispo. vers. : 11, 17 | ✅ Dispo. vers. : 8, 11, 17, 18 | ✅ |
| **Gestionnaires de dépendances de paquets** |
| `composer` | gestionnaire de dépendances **PHP** |✅ |✅ |✅ |✅ |
| `nodejs` | gestionnaire de dépendances **JS** pour **NodeJS & NPM** |✅ |✅ |✅ |✅ |
| `maven` | gestionnaire de dépendances **Java** |✅ |✅ |✅ |✅ |
|**Autres commande**|
| `shutdown` | arrêt du système |✅ |✅ |✅ |✅ |

## 4 - Divers installations

### 4.1 - Installation de `ifconfig`
	
| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `sudo apt install net-tools` |
| Ubuntu Server 22.04 LTS | `sudo apt install net-tools` |

### 4.2 - Insllation du serveur web Apache

| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `sudo apt install apache2 -y` |
| Ubuntu Server 22.04 LTS | `sudo apt install apache2 -y` |

Apache est ensuite disponible à l'url [http://127.0.0.1](http://127.0.0.1) avec un guide qui s'affiche.

### 4.3 - Status du serveur web Apache et autres services

| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `systemctl status <service>` |
| Ubuntu Server 22.04 LTS | `systemctl status <service>` |

Exemple :

```
systemctl status apache
```

```
service --status-all
```

### 4.4 - Arrêter l'OS

| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `shutdown -h now` |
| Ubuntu Server 22.04 LTS | `shutdown -h now` |

### 4.5 - Installation de Jenkins (testé pour Ubuntu 16.04 / 20.04.1 LTS)

> Source : https://websiteforstudents.com/how-to-install-jenkins-automation-server-on-ubuntu-16-04-18-04-18-10/

Voici toutes les requètes néceassire pour installer Jenkins.

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins
sudo systemctl status jenkins.service
```

Vérification des stocks.

```
sudo systemctl stop jenkins.service
sudo systemctl start jenkins.service
sudo systemctl enable jenkins.service
```

Voir la page de gestion de Jenkins puis suivre les étapes.

> http://localhost:8080

Récupération du mot de passe demander.

```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

L'installation devrais se terminer tranquillement.

### 4.6 - Installation de Valet (testé pour Ubuntu 16.04 / 20.04.1 LTS)

Vérification des pré-requis

```
apt install network-manager libnss3-tools jq xsel
apt install php*-cli php*-common php*-curl php*-json php*-mbstring php*-mcrypt php*-mysql php*-opcache php*-readline php*-xml php*-zip
apt install php*-sqlite3 php*-mysql php*-pgsql
apt install php7.0-fpm
apt install php7.0-curl
```

Récupéraition de Valet-Linux

```
composer global require cpriego/valet-linux
```

Installation de valet

```
valet install
```

> Si vous obtenez la commande valet introuvable, le chemin du compositeur n'est pas actuellement ajouté. Pour ce faire, nous devons d'abord vérifier le chemin du compositeur existant par la commande suivante
> Maintenant, ajoutez le chemin (si votre chemin est /root/.composer/ alors il le serait)

```
echo "export PATH=$PATH :/root/.composer/bin" >> ~/.bashrc
```

### 4.7 - Installation de Gitlab (testé pour Ubuntu 16.04 / 20.04.1 LTS)

> Source : https://www.howtoforge.com/tutorial/how-to-install-and-configure-gitlab-on-ubuntu-16-04/

Voici toutes les requètes nécessaire pour installer Jenkins.

```
curl -sS https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | sudo bash
sudo apt install gitlab-ce
```

La configuration de gitlab se trouve dans le fichier ci-dessous :

```
cd /etc/gitlab 
vim gitlab.rb
```

Modifier la valeur ci-cessous avec l'adresse que désirez.

> `external_url 'http://<gitlab.localhost>'`

---

Non fait encore :

Une fois l'installation terminée, générez un nouveau certificat pour le nom de domaine gitlab avec la commande ci-dessous.

```
letsencrypt certonly -d <gitlab.localhost>
```

---

#### Si dpkg, apt, apt-get est bloqué (testé pour Ubuntu 16.04 / 20.04.1 LTS)

Source : https://forums.commentcamarche.net/forum/affich-36129476-impossible-d-obtenir-le-verrou-var-lib-dpkg-lock-frontend

Dans le cas où :

> Explication 1 : un autre gestionnaire de paquets est déjà ouvert,
> Explication 2 : un gestionnaire de paquets a été quitté abruptement et n'a pas pu supprimer les verrous qu'il avait installé.

```
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```

```
sudo dpkg --configure -a
```
---

[help-1](https://www.linuxcapable.com/fr_fr/comment-installer-apache-sur-ubuntu-22-04-lts/)
[help-2](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04)