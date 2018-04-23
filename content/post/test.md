---
title: "Test"
date: 2017-10-03T16:40:27+02:00
draft: true
---

## Test de highlight html

Début du test

{{< highlight html >}}
<section id="main">
  <div>
   <h1 id="title">{{ .Title }}</h1>
    {{ range .Data.Pages }}
        {{ .Render "summary"}}
    {{ end }}
  </div>
</section>
{{< /highlight >}}

Fin du test

## Test de figure

{{< figure src="../../img/sublime-text/sublime-text_logo.png" title="Sublime-text" >}}

## Test d'un shortcode

Voici le texte du shortcode : {{< myshortcode color="green">}}


```
apt-get install go
```
