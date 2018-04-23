+++
title = "Installer un environnement XAMPP avec PostgreSQL sous Linux"
description = "Comment installer et configurer un environnement de dévelopement LAMPP (Linux-Apache-MariaDB-PostgreSQL-PHP) ?"
tags = [
    "code",
    "http",
    "php",
    "développement",
]
date = "2017-10-24"
categories = [
    "Développement",
    "PHP",
]
thumbnail = "img/xampp/xampp-logo-2000x1044.png"
+++

## Prérequis
L'installation sera réalisée sur une machine disposant des ressources nécessaires au fonctionnement des éléments de la pile **Xampp** avec une base de données **PostgreSQL**. Les outils de développements se résument à un éditeur de texte ; **Sublime-text** ou **Atom** dans cet exposé.

Le compte Unix qui sera utilisé pour l'installation est **"operateur"**. Il fait partie du groupe **"sudo"**, c'est à dire qu'il a la possibilité d'invoquer la commande sudo pour exécuter des commandes avec les droits super-utilisateur.  

## Objectif

L'objectif est de disposer d'un contexte de développement reproduisant un environnement de production, en concentrant les services (serveur http, base de données etc.) dans un répertoire qu'il suffira de supprimer ou de copier selon nos besoins. On ne touche pas à la distribution : on n'installe pas les composants "serveurs" par le système de paquetages classiques.

Outre que l'on dispose d'une pile toujours à jour car il suffit d'aller sur le site **http://www.apachefriends.org** pour télécharger la dernière version de notre environnement Lampp, l'avantage est qu'on pourra démarrer et arrêter plus facilement les services et ne les activer que lorsqu'on sera en mode "développement". On n'alourdit pas le système avec des services (httpd/php, postgresql, mariadb) qui sont lancés au démarrage et consomment des ressources lorsqu'on n'en a pas besoin. Il est évident que même installés avec le système de paquetages classique, les services peuvent être lancés et arrêtés à la demande, mais le fait d'utiliser **Xampp** permet de s'affranchir des aléas liés à la fréquence de mises à jour de la pile Apache/Php/MariaDb des responsables de la distribution.

## Téléchargement et installation

Comme on l'a dit plus haut, la pile **Xampp** pour Linux est téléchargeable depuis la page d'accueil du projet **http://www.apachefriends.org** Une fois sur la page d'accueil, cliquer sur le lien **"Download"** pour aller à la page de téléchargement.
Cette page présente les versions les plus à jour de **Xampp** pour chaque système d'exploitation supporté. Nous nous intéressons à la version Linux désignée par l'entête **"XAMPP for Linux 5.6.31, 7.0.24 & 7.1.10"**.

Une fois téléchargé, il faut rendre le fichier exécutable car c'est un programme d'installation qu'il convient de lancer et non d'une archive à décompacter comme c'est souvent le cas.

{{< highlight html >}}
$ chmod 744 xampp-linux-x64-7.1.10-0-installer.run
{{< /highlight >}}

On lance l'installation en mode super-utilisateur :

{{< highlight html >}}
$ sudo -i
# xampp-linux-x64-7.1.10-0-installer.run
{{< /highlight >}}

Après l'affichage du logo de Bitnami, la première boite de dialogue s'affiche :

![Etape 1](../../img/xampp/xampp-install-01.png)

On clique sur le bouton **"Next"**.

![Etape 2](../../img/xampp/xampp-install-02.png)
