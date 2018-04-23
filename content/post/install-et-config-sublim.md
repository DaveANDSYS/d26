---
title: Installer, configurer et personnaliser Sublime-text
date: 2017-08-15
description: Comment installer, configurer et personnaliser Sublime-text ? # Add post description (optional)
thumbnail: /img/sublime-text/sublime-text_logo-fond-trans.png # Add image post (optional)
tags: [web, code, editeur]
---
## Qu'est-ce que Sublime-text ?
Sublime-text est un éditeur de code multi-langages, multi-plateformes (Windows, Mac et Linux), rapide (écrit en C++ et en Python). Plus de 40 langages de programmation sont supportés pour lesquels Sublime-text propose la coloration syntaxique.

Sublime-text est doté d'un gestionnaire de paquetages (package manager) qui permet à l'utilisateur de personnaliser son environnement en l'enrichissant de fonctionnalités et en modifiant les paramètres de visualisation (thèmes, fontes, couleurs).

## Installer Sublime-text

{{< highlight html >}}
sudo apt-get install sublime-text
{{< /highlight >}}

## Installer Package Control

Package Control est requis pour permettre l'installation de la plupart des autres paquetages.

L'url [suivante](https://packagecontrol.io/installation) conduit à la page expliquant comment installer Package Control.

Si vous souhaitez installer Package Control alors que votre poste de travail accède à Internet via un proxy, voici la marche à suivre :

- Télécharger le paquetage à l'adresse [suivante](https://packagecontrol.io/Package%20Control.sublime-package)
- Copier le paquetage dans le dossier :

{{< highlight html >}}
/home/nom_utilisateur_linux]/.config/sublime-text-3/Installed Packages
{{< /highlight >}}

Ne pas oublier de quitter puis de relancer Sublime-text pour que le nouveau paquetage soit chargé. 

## Configurer Package Control pour qu'il fonctionne derrière un proxy

Si le poste de travail se connecte à internet via un proxy, il faut indiquer à Package Control les paramètres d'accès au proxy. Dans le menu "Préférences", choisir "Package Settings" puis "Package Control", et enfin "Settings - User".

Le fichier de configuration utilisateur de Package Control s'ouvre. Il faut ajouter les lignes suivantes pour indiquer à Package Control quel proxy utiliser pourn sortir sur internet.

La liste des paramètres est placé entre deux accolades :

{{< highlight html >}}
{
	"http_proxy": "http://[adresse du serveur proxy]:[port_du_serveur_proxy]",
	"https_proxy": "http://[adresse du serveur proxy]:[port_du_serveur_proxy]"
}
{{< /highlight >}}

S'il y a d'autres paramètres après le proxy, penser à ajouter une virgule en fin de ligne :

{{< highlight html >}}
{
	"http_proxy": "http://[adresse du serveur proxy]:[port_du_serveur_proxy]",
	"https_proxy": "http://[adresse du serveur proxy]:[port_du_serveur_proxy]",
	"installed_packages":
	[
		"Boxy Theme",
		"Package Control",
		"Predawn",
		"Predawn Monokai"
	]
}
{{< /highlight >}}

## Utiliser Package Control pour ajouter des paquetages

Dans le menu "Tools", choisir "Command Palette...". Dasn la liste qui s'affiche, choisir "Package Control: Install Package". Puis se déplacer dans la liste des paquetages qui s'affiche pour choisir celui qu'on désire installer.
