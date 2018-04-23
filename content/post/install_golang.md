---
title: "Install Golang"
date: 2018-04-13T16:19:31+02:00
draft: false
---
- Télécharger Golang

- Créer le répertoire qui va contenir GO et les GOtools:
  mkdir ~/golang

- Décompresser golang:
  tar -C /usr/local -xzf go1.10.1.linux-amd64.tar.gz

- Renseigner les variables d'environnement:

{{< highlight html >}}
  vi ~/.bashrc
  # golang
  #export GOROOT=/usr/local/go                # rep pour go et ses outils
  #pas nécessaire car /usr/local/go = emplacement par défaut
  #requis sinon le plugin go-plus de atom.io ne fonctionnera pas
  export GOPATH=$HOME/Documents/code/go       # rep pourles projets
  export PATH=$PATH:$GOPATH/bin:$GOROOT/bin   # variable PATH nécessaire pour compiler
- Créer les sous-répertoires nécessaires :
  mkdir $GOPATH/bin
  mkdir $GOPATH/pkg
  mkdir $GOPATH/src
{{< /highlight >}}

Inspiré de:
------------------------------------------------------------------------
Here is a my simple setup:

directory for go related things: ~/programming/go
directory for go compiler/tools: ~/programming/go/go-1.4
directory for go software      : ~/programming/go/packages

GOROOT, GOPATH, PATH are set as following:

export GOROOT=/home/user/programming/go/go-1.4
export GOPATH=/home/user/programming/go/packages
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin

So, in short:

GOROOT is for compiler/tools that comes from go installation.
GOPATH is for your own go projects / 3rd party libraries (downloaded with "go get").
------------------------------------------------------------------------

- Tester l'installation de golang:
  Créer le projet "hello"
  mkdir $GOPATH/src/hello
  vi $GOPATH/src/hello/hello.go

  insérer les lignes suivantes:

	package main

	import "fmt"

	func main() {
		fmt.Printf("Salut le monde !\n")
	}

- Compiler le projet
  go build

  A ce stade, l'exécutable est construit dans le répertoire dans lequel
  on a créé le source, à savoir : $GOPATH/src/hello

  Pour rendre l'exécutable accessible depuis tout le système, il faut le
  placer dans le répertoire $GOPATH/bin qui est référencé dans la
  variable d'environnement $PATH

  Pour cela, il faut installer "hello":
  lancer: "go install" depuis le répertoire $GOPATH/src/hello

  Pour supprimer le programme: go clean depuis le répertoire $GOPATH/src/hello
