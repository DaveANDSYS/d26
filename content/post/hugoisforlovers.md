+++
title = "Créer son blog avec Hugo"
description = "Inspiré de la page https://themes.gohugo.io/theme/nofancy/post/hugoisforlovers/"
tags = [
    "go",
    "golang",
    "hugo",
    "développement",
]
date = "2017-10-04"
categories = [
    "Développement",
    "golang",
]
thumbnail = "img/hugo/hugo-logo-01.png"
draft= true
+++

## Etape 1. Installer Hugo

La documentation d'installation originale est accessible depuis ce lien : [installer hugo](https://gohugo.io/getting-started/installing/).

Dans le cadre de ce billet, l'installation sera faite sur un PC sous Debian 9 (Stretch).

Il est possible d'installer Hugo en utilisant le gestionnaire de paquetages intégré de Debian, ou de télécharger le tarball (fichier portant l'extension ".tar.gz"), puis de le décompresser dans le répertoire de son choix. Notre installation sera réalisée en utilisant la deuxième méthode.

Télécharger la version du fichier tarball qui convient à votre environnement (OS et architecture) depuis la page de [téléchargement des versions de Hugo](https://github.com/spf13/hugo/releases).

Il est possible de réaliser une installation qui ne permettra de faire fonctionner le serveur web intégré à Hugo qu'avec le compte de l'utilisateur connecté à la session Linux, ou de faire en sorte que tous les utilisateurs du système puissent lancer le serveur. Dans mon cas, étant le seul utilisateur à utiliser ma statio de travail, je choisis une installation qui ne concerne que mon compte.

On va donc créer un répertoire dans lequel on va décompreser le fichier téléchargé. Pour une organisation propre de mon répertoire utilisateur, j'ai l'habitude de décompresser les programmes que j'installe manuellement à partir de fichiers traball dans un répertoire "Applications", à la racine de mon répertoire utilisateur. Si mon compte utilisateur est intitulé "johndoe", je dispose normalement du dossier utilisateur "/home/johndoe". Je vais donc y créer le répertoire **applications** :

{{< highlight html >}}
mkdir /home/johndoe/applications
{{< /highlight >}}

Je crée ensuite le répertoire **hugo**, je me positionne dans ce répertoire et je récupère le fichier tarball :

{{< highlight html >}}
cd /home/johndoe/applications
wget https://github.com/gohugoio/hugo/releases/download/v0.29/hugo_0.29_Linux-64bit.tar.gz
{{< /highlight >}}

Enfin on décompresse le fichier :

{{< highlight html >}}
tar zxvf hugo_0.29_Linux-64bit.tar.gz
{{< /highlight >}}

Je dois obtenir ce résultat :

{{< highlight html >}}
README.md
LICENSE.md
hugo
{{< /highlight >}}

Il s'agit des trois fichiers décompressés.

**README.md** et **LICENSE.md** sont des fichiers d'informations au sujet du programme et de sa licence.

**hugo** est l'exécutable qui va nous permettre de créer le blog et d'exécuter le serveur web intégré.

Il reste une étape qui va nous éviter d'avoir à saisir l'intégralité du chemin d'accès au programme **hugo** à chaque fois qu'on voudra l'exécuter. On va donc ajouter ce chemin au PATH de notre session utilisateur.

Il faut éditer le fichier .bashrc de l'utilisateur courant et y ajouter le chemin de la façon suivante :

{{< highlight html >}}
vi /home/johndoe/.bashrc
{{< /highlight >}}

A la fin du fichier ajouter :

{{< highlight html >}}
PATH=$PATH:/home/johndoe/applications/hugo
{{< /highlight >}}

Il faut maintenant fermer la fenêtre de commande et l'ouvrir à nouveau pour que les changements soient pris en compte, ou lancer la commande :

{{< highlight html >}}
source ~/.bashrc
{{< /highlight >}}

qui réinitialise l'environnement d'exécution de la session dans le terminal.

On peut enfin tester le fonctionnement de **Hugo** :

{{< highlight html >}}
hugo version
{{< /highlight >}}

Ce qui donne si l'installation est correcte :

{{< highlight html >}}
Hugo Static Site Generator v0.29 linux/amd64 BuildDate: 2017-09-26T21:23:30+02:00
{{< /highlight >}}

## Etape 2. Créer le blog

Hugo has its own example site which happens to also be the documentation site
you are reading right now.

Follow the following steps:

 1. Clone the [hugo repository](http://github.com/spf13/hugo)
 2. Go into the repo
 3. Run hugo in server mode and build the docs
 4. Open your browser to http://localhost:1313

Corresponding pseudo commands:

    git clone https://github.com/spf13/hugo
    cd hugo
    /path/to/where/you/installed/hugo server --source=./docs
    > 29 pages created
    > 0 tags index created
    > in 27 ms
    > Web Server is available at http://localhost:1313
    > Press ctrl+c to stop

Once you've gotten here, follow along the rest of this page on your local build.

## Step 3. Change the docs site

Stop the Hugo process by hitting ctrl+c.

Now we are going to run hugo again, but this time with hugo in watch mode.

    /path/to/hugo/from/step/1/hugo server --source=./docs --watch
    > 29 pages created
    > 0 tags index created
    > in 27 ms
    > Web Server is available at http://localhost:1313
    > Watching for changes in /Users/spf13/Code/hugo/docs/content
    > Press ctrl+c to stop


Open your [favorite editor](http://vim.spf13.com) and change one of the source
content pages. How about changing this very file to *fix the typo*. How about changing this very file to *fix the typo*.

Content files are found in `docs/content/`. Unless otherwise specified, files
are located at the same relative location as the url, in our case
`docs/content/overview/quickstart.md`.

Change and save this file.. Notice what happened in your terminal.

    > Change detected, rebuilding site

    > 29 pages created
    > 0 tags index created
    > in 26 ms

Refresh the browser and observe that the typo is now fixed.

Notice how quick that was. Try to refresh the site before it's finished building.. I double dare you.
Having nearly instant feedback enables you to have your creativity flow without waiting for long builds.

## Step 4. Have fun

The best way to learn something is to play with it.
