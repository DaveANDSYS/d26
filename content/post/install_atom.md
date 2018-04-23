---
title: Installer, configurer et personnaliser Atom.io pour développer en Golang
date: 2017-08-15
description: Comment installer, configurer et personnaliser Atom.io pour développer en Golang? # Add post description (optional)
thumbnail: /img/atom/atom_logo.png # Add image post (optional)
tags: [web, code, editeur]
---
## Qu'est-ce que Atom.io ?

Atom est un éditeur de texte libre pour MacOSX, GNU/Linux, et Windows développé par GitHub. Il supporte des plug-ins écrits en Node.js et implémente Git Control. La plupart des extensions sont sous licence libre et sont maintenues par la communauté. Atom, basé sur Chromium et Electron est écrit en CoffeeScript. Il est aussi utilisé en tant qu’IDE. (source [Wikipedia](https://fr.wikipedia.org/wiki/Atom_(%C3%A9diteur_de_texte)).

## Installer Atom.io

- Télécharger le fichier depuis le [site](https://atom.io/download/deb).
- Lancer l'installation du paquetage téléchargé :

{{< highlight html >}}
sudo dpkg -i atom-amd64.deb
{{< /highlight >}}

Atom est installé.

## Configurer Atom.io pour qu'il fonctionne derrière un proxy

- Configurer Atom pour passer par le proxy

{{< highlight html >}}
apm config set https-proxy http://172.26.49.2:3128
apm config set http-proxy https://172.26.49.2:3128
{{< /highlight >}}

!!! Ne pas utiliser le protocole https, mais plutôt http en raison d'un bug non encore corrigé en version 1.25.1 !!!

- Pour voir la liste des paramètres:
  apm config list

## Franciser Atom.io

- Lancer Atom.io et aller dans le menu File -> Préferences -> Settings

- Cliquer sur "Install"

- Dans la boite de recherche saisir "french-menu" et cliquer sur le bouton "Packages".

- En résultat on doit trouver french-menu x.x.x. Cliquer sur le bouton "Install".

## Installer les plugins additionnels pour Golang

- Lancer Atom.io et aller dans le menu File -> Préferences -> Settings
  Cliquer sur "Install"
  Dans la boite de recherche saisir "go-plus" et cliquer sur le bouton
  "Packages".

  En résultat on doit trouver go-plus 5.8.3. Cliquer sur le bouton "Install".

- Faire la même chose pour le package "autocomplete-go".

- Faire la même chose pour platformio-ide-terminal

- Paramétrer platformio-ide-terminal:
  Lancer Atom.io et aller dans le menu Edition -> Settings
  Cliquer sur "Packages"

  Bizarrement, le PATH défini au niveau du shell par le fichioer .bashrc
  n'est pa pris en compte par platformio-ide-terminal. Il faut donc ajouter
  les variables d'environnement GOROOT et GOPATH dans les paramètres du
  plugin:

  Trouver platformio-ide-terminal et cliquer sur le bouton "Settings"
  Dans la zone "Shell environment variables", ajouter les variables:
  GOROOT=/usr/local/go GOPATH=/usr/christophe.benard/Documents/code/go PATH=$PATH:$GOROOT/bin:$GOPATH/bin

  Bizarement (bis), le PATH défini dans les paramètres de platformio-ide-terminal
  n'est pas non plus pris en compte. Il faut donc redéfinir dans la
  fenêtre de terminal de platformio-ide-terminal la variable PATH en
  ajoutant $GOROOT/bin et $GOPATH/BIN:

  export $PATH=$PATH:$GOROOT/bin:$GOPATH/bin

  Maintenant la commande "go run" fontionne sans retourner de message
  "bash: go : commande introuvable"

- Installer manuellement les outils complémentaires:
   go get -u golang.org/x/tools/cmd/goimports
   go get -u golang.org/x/tools/cmd/gorename
   go get -u github.com/sqs/goreturns
   go get -u github.com/nsf/gocode
   go get -u github.com/alecthomas/gometalinter
   go get -u github.com/zmb3/gogetdoc
   go get -u github.com/zmb3/goaddimport
   go get -u github.com/rogpeppe/godef
   go get -u golang.org/x/tools/cmd/guru
   go get -u github.com/fatih/gomodifytags
   go get -u github.com/tpng/gopkgs

- Mettre à jour les packages Go:
  Aller dans Packages->Go et choisir "Update Tools"
