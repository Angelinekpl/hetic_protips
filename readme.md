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

## Liens utiles :
* [Caniuse]https://caniuse.com/#feat=viewport-units