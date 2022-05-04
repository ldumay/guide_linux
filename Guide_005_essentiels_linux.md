# Essentiels Linux

==> [retour accueil](../..)

## Debian - Ajout un utilisateur à la liste "sudoers" (admins)

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

## Installation de `ifconfig`
	
| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `sudo apt install net-tools` |
| Ubuntu Server 22.04 LTS | `sudo apt install net-tools` |

## Insllation du serveur web Apache

| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `sudo apt install apache2 -y` |
| Ubuntu Server 22.04 LTS | `sudo apt install apache2 -y` |

Apache est ensuite disponible à l'url [http://127.0.0.1](http://127.0.0.1) avec un guide qui s'affiche.

## Status du serveur web Apache et autres services

| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `systemctl status <service>` |
| Ubuntu Server 22.04 LTS | `systemctl status <service>` |

Exemple :

```
systemctl status apache
```

## Arrêter l'OS

| OS | Commande |
|---|---|
| Debian 11 | `...` |
| Ubuntu Desktop 22.04 LTS | `shutdown -h now` |
| Ubuntu Server 22.04 LTS | `shutdown -h now` |



---

[help-1](https://www.linuxcapable.com/fr_fr/comment-installer-apache-sur-ubuntu-22-04-lts/)
[help-2](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-22-04)