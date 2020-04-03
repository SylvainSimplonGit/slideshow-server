# Configuration et Utilisation de Slideshow

- [Récupération de la présentation](#récupération-de-la-présentation)
- [Installation des dépendances](#installation-des-dépendances)
- [Modifier votre présentation](#modifier-votre-présentation)
- [Lancement de votre présentation](#lancement-de-votre-présentation)
- [Problèmes connus](#problèmes-connus)

Ce repository contient une présentation vierge basée sur Reveal.js et son utilisation en mode serveur.

Cette présentation a été réalisée avec Reveal.js v3.9.2 et testée sous Firefox 74.

>Dans les sections suivantes le répertoire racine de cette présentation sera nommé `SLIDESHOW-ROOT`.

## Récupération de la présentation

Dans le répertoire `SLIDESHOW-ROOT`, excécuter la commande suivante :

```shell
git clone https://github.com/SylvainSimplonGit/slideshow-server.git
```

## Installation des dépendances

Dans le répertoire `SLIDESHOW-ROOT`, exécuter la commande suivante :

```shell
./install.sh
```

## Modifier votre présentation

- [Modifier le titre](#modifier-le-titre)
- [Modifier l'icône](#modifier-l'icône)
- [Modifier le thème](#modifier-le-thème)
- [Ajouter un style personnalisé](#ajouter-un-style-personnalisé)
- [Modifier un style de surlignage](#modifier-un-style-de-surlignage)
- [Ajouter un chapitre](#ajouter-un-chapitre)
- [Ajouter un slide](#ajouter-un-slide)

### Modifier le titre

Pour changer le titre de votre présentation, ajoutez le entre les balises `title` à la ligne 9 du fichier `index.html` du répertoire `SLIDESHOW-ROOT` :

```html
  <!-- Change slideshow Title -->
  <title>Nouveau Titre</title>
```

### Modifier l'icône

Pour changer l'icône de votre présentation, ajoutez ou remplacer le fichier `icon.png` situé dans le répertoire `SLIDESHOW-ROOT/slideshow/resources/icons/` puis modifiez en conséquence la ligne 11 du fichier `index.html` du répertoire `SLIDESHOW-ROOT` :

```html
  <!-- Change slideshow Icon  -->
  <link rel="icon" href="./slideshow/resources/icons/<file_icon.png>" />
```

### Modifier le thème

Pour modifier le thème de la présentation, vous pouvez soit :

- utiliser un thème déjà livré avec Reveal.js qui se trouvent dans le répertoire `SLIDESHOW-ROOT/reveal.js/css/theme/`
- créer votre propre thème en copiant un thème déjà livré et le modifier en mettant ce fichier modifié dans le répertoire `SLIDESHOW-ROOT/slideshow/css/theme/`

Pour utiliser le thème choisi, modifiez en conséquence la ligne 17 du fichier `index.html` du répertoire `SLIDESHOW-ROOT` :

```html
  <!-- Modify the href link to change theme -->
  <link rel="stylesheet" href="./slideshow/css/theme/default.css" id="theme">
```

Ici le theme default est utilisé.

### Ajouter un style personnalisé

Pour ajouter un style sur une image ou autre balise, vous pouvez l'ajouter dans le fichier `style.css` situé dans le répertoire `SLIDESHOW-ROOT/slideshow/css/`

### Modifier un style de surlignage

Ce thème n'est utilisé que pour le surlignage (ou highlighting) des balises `<code>`.

Pour changer thème du surlignage de votre présentation, modifier la ligne 23 du fichier `index.html` du répertoire `SLIDESHOW-ROOT` :

```html
  <!-- Change CSS theme to the highlighting -->
  <link rel="stylesheet" href="../reveal.js/lib/css/monokai.css">
```

Ici le thème de surlignage monokai est utilisé. 

Vous pouvez choisir parmi les thèmes suivants :

- agate
- androidstudio
- arta
- atom-one-dark
- dark
- github
- github-gist
- ir-black
- kimbie.dark
- kimbie.light
- monokai
- monokai-sublime
- schoolbook
- zenburn

Pour voir une démo de ces thèmes, vous pouvez tester sur le site [highlight.js demo](https://highlightjs.org/static/demo/).

### Ajouter un chapitre

Dans le fichier `_slideshow.html` situé dans le répertoire `SLIDESHOW-ROOT/slideshow/`, ajoutez une nouvelle section dans l'ordre d'apparition du chapitre comme suit :

```html
<section data-external="./1-debut.html"> </section>

...

<section data-external="./99-fin.html"> </section>
```

Ici le fichier `1-debut.html` sera afficher en premier et le fichier `99-fin.html` sera afficher en dernier.

Il est nécessaire bien sûr d'ajouter le fichier correspondant dans le répertoire `SLIDESHOW-ROOT/slideshow/`.

Par exemple, si vous souhaitez ajouter le chapitre 2 entre le chapitre 1 et 3 dans l'exemple suivant :

```html
<section data-external="./1-chapter1.html"> </section>

<section data-external="./3-chapter3.html"> </section>
```

Il faudra insérer la section faisant référence au chapitre n°2 :

```html
<section data-external="./1-chapter1.html"> </section>

<section data-external="./2-chapter2.html"> </section>

<section data-external="./3-chapter3.html"> </section>
```

et créez le fichier `2-chapter2.html` dans le répertoire `SLIDESHOW-ROOT/slideshow/`.

### Ajouter un slide

Pour ajouter un slide dans un chapitre, éditez le fichier qui correspond au chapitre dans lequel vous voulez ajouter le nouveau slide et ajouter une nouvelle section où vous souhaitez voir afficher votre nouveau slide.

Par exemple, pour afficher une slide entre la slide 1 et 3 : 

```html

<section data-timing="">
  <h1>Slide 1</h1>

  <aside class="notes">
  </aside>
</section>

<section data-timing="">
  <h1>Slide 3</h1>

  <aside class="notes">
  </aside>
</section>

```

Insérer comme ceci le nouveau slide :

```html
<section data-timing="">
  <h1>Slide 1</h1>

  <aside class="notes">
  </aside>
</section>

<section data-timing="">
  <h1>Slide 2</h1>

  <aside class="notes">
  </aside>
</section>

<section data-timing="">
  <h1>Slide 3</h1>

  <aside class="notes">
  </aside>
</section>
```

### Ajouter le symbole de clic

Si vous souhaitez afficher l'icône symbolisant un clic <img src="reveal.js/resources/images/click-notes.png" width="30px">, il vous faudra ajouter ce texte "(O)" à l'endroit où vous souhaitez le voir apparaitre dans les notes du présentateur.

Exemple :

```html
<aside class="notes">
  ...
  cliquez => (O)
</aside>
```

## Lancement de votre présentation

Dans le répertoire `SLIDESHOW-ROOT`, exécuter la commande suivante :

```shell
./launch.sh
```

Vous devriez avoir un nouvel onglet dans votre navigateur par défaut avec la présentation.

Pour l'utilisation de Reveal.js, les raccourcis claviers sont les suivants :

- <kbd>N</kbd>, <kbd>SPACE</kbd>: Next slide
- <kbd>P</kbd>: Previous slide
- <kbd>←</kbd>, <kbd>H</kbd>: Navigate left
- <kbd>→</kbd>, <kbd>L</kbd>: Navigate right
- <kbd>↑</kbd>, <kbd>K</kbd>: Navigate up
- <kbd>↓</kbd>, <kbd>J</kbd>: Navigate down
- <kbd>Home</kbd>: First slide
- <kbd>End</kbd>: Last slide
- <kbd>B</kbd>, <kbd>.</kbd>: Pause (Blackout)
- <kbd>F</kbd>: Fullscreen
- <kbd>ESC</kbd>, <kbd>O</kbd>: Slide overview / Escape from full-screen
- <kbd>S</kbd>: Speaker notes view
- <kbd>?</kbd>: Show keyboard shortcuts
- <kbd>alt</kbd> + click: Zoom in. Repeat to zoom back out.

Si vous souhaitez plus d'informations sur ce que peut faire **Reveal.js**, vous pouvez visiter le [site officiel](https://revealjs.com/#/)

## Problèmes connus

Les vidéos ne sont pas lancés sous Chrome, apparemment Chrome bloquerait l'exécution des vidéos. Pour contourner le problème, utilisez Firefox.
