# Documentation

## Convention BEM

B --> Block
E --> Element
M --> Modifier

```html
<!-- mainList = Block -->
<ul class="mainList mainList--xmas">
  <!-- _item = Element -->
  <li class="mainList_item">
    <!-- _itemLink = Element  -->
    <a class="mainList_itemLink mainList_itemLink--isActive"href="/home">Home</a>
  </li>
  <li class="mainList_item">
    <!-- _itemLink = Element  -->
    <a class="mainList_itemLink"href="/about">About</a>
  </li>
  <li class="mainList_item">
    <!-- _itemLink = Element  -->
    <a class="mainList_itemLink"href="/works">Works</a>
  </li>
</ul>

```
```css
.mainList {
  display: flex;
  justify-content: space-between;
  &--xmas {
    background: green;
  }
  &_item {
    list-style: none;

  }
  &_itemLink{
    color: red;
    &--isActive {
      color: white;
    }
  }
}
```

Exemple en CSS du rendu :

```css

.mainList {

}
.mainList--xmas {

}
.mainList_item{

}
.mainList_itemLink{

}
.mainList_itemLink--isActive{

}
```

## Pseudo attributs

Les pseudo attributs `before` et `after` permettent de créer des noeuds HTML en CSS.
Ils sont essentiellement utilisés pour ajouter des ornements, des décorations ... On
peut bien entendu faire des animations avec, les positionner par rapport à leur
parent (relative / absolute). **Ils doivent obligatoirement avoir un `content`: ''`**
afin de s'afficher.

```HTML
<section class="cover">
  <h1 class="cover_mainTitle">Présentation des pseudo-attributs</h1>
</section>
```
```CSS
.cover {
  background: #FDFDFD;
  padding: 20px;
  &main_Title {
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;
    &::before,
    &::after {
      content:'';
      width: 50px;
      height: 50px;
      background: green;
      top:0;
    }
    &::before {
      left : 0;
    }
    &::after {
      right : 0;
    }

    }
  }
}
```

## REM, EM, %, VW Sizing

### %



### EM
* Relatie à la taille de son parent direct.

```css
.cover{
  font-size: 100%;  /* 100% = 16px */
  &_mainTitle {
    /* 1em = 16px / .8em ≠ 16px  */
    font-size: .8em;

  }
}
```
### REM

* Le REM est basé sur la taille de la racine (soit la balise <html>) qui, par défaut
a une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser
en donnant une base de 10px soit 62,5%.

* Le REM est intéressant à utiliser si les media-queries employées sont en rem
également. Cela vous permettra de garder des proportios égales lorsqu'on va
redimensionner la page.

* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.

```css

html{
  font-size: 62,5%;
}

.mainTitle {
  /* 1.6rem = 16px */
  font-size: 1.6em;
  /* 32rem = 320px */
  width : 32rem
}

```

### VW(idth) / VH(eight)
* Unités relatives à la taille de votre écran (peu importe le device)
* Attention au VH et à son contenu. 100 vh = 100vh quoi qu'il arrive.
* VW : très utile pour les interface fluides.

## Travailler avec Github

### Cloner le projet 

```
git clone git@lien-ssh
```

### Créer une branche 
```
git checkout -b nom_branche
````

### Résoudre les issues 
```
git add .
git commit -m "nom_issue"
```

### Ajouter les issues traitées sur github
```
git push origin nom_branche
```

## Utiliser une font-face 

### C'est quoi ?
Ne pas être limité par les polices prédéfinies. 

### Exemple d'utilisation 

```
@font-face {
  font-family : "Raleway";
  src : ('/fonts/raleway.eot');
  }
```
### Quelles sont les limites ?

Le chargement de la page peut être plus long car le fichier de la police et la page sont chargés en même temps. 

Les navigateurs n'arrivent parfois pas à interpréter le code correctement. Pour résoudre ces problèmes d'incompatibilité, il faut ajouter certains critères pour que le code s'affiche correctement. Exemple : télécharger la police dans tous les formats tels que .woff, .svg, .eot

## Positionnement des éléments

### Absolute
Permet de positionner un élément par rapport à son élément parent.

### Relative
Permet de placer un élément par rapport à sa position initiale.

### Sticky 
Permet de maintenir la postion d'un objet à une endroit précis dès que celui-ci devient hors de portée (quand on scroll dans la page). 

### Fixe
Permet de placer l'élément où on le souhaite dans la page. Celui-ci restera visible peut importe où l'on se trouve sur la page. 

## CSS Grid 

Il s'agit d'une grille à 2 dimensions (colonnes et lignes). 
La grille est entièrement paramétrable : nombre de lignes, taille des goutières. 
Exemple : 
```
 grid-template-columns: 250px 400px;
  grid-template-rows: 100px 300px;
  ```  
Le comportement de chaque élément est personnalisable en css  : l'ordre, le nombre de colonne que prendra l'élément, ... 
Exemple : 
```
nav {
  grid-column: 1; grid-row: 1;
}
section {
  grid-column: 2; grid-row: 1;
}
article {
  grid-column: 1; grid-row: 2;
}
```

### Une autre unité de mesure

Le fr. Celui-ci définit une fraction de l'espace disponible.

Exemple : 
```
grid-template-columns: repeat(3, 1fr);
```
Ici, nous aurons une grille comportant 3 colonnes occupant 1/3 de l'espace disponible restant (en fonction des margin et padding renseignés).  

### Astuce : 

Utiliser l'édition développeur de Firefox qui propose une visualisation de la grille. Cela permet de comprendre le comportement de chaque élément par rapport à la grille. 




## Liens utiles :
* [Caniuse]https://caniuse.com/#feat=viewport-units
