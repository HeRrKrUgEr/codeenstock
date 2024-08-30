# Cheatsheet Alpine.js

## Introduction

Alpine.js est un framework JavaScript léger pour ajouter des fonctionnalités interactives à vos pages web de manière déclarative.

## Installation

```html
<script src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js" defer></script>
```

## Directives de base

### x-data

Définit un objet de données pour un composant.

```html
<div x-data="{ open: false }">
  <!-- Contenu du composant -->
</div>
```

### x-bind

Lie un attribut à une expression.

```html
<button x-bind:disabled="!form.valid">Envoyer</button>
```

Raccourci : `:disabled="!form.valid"`

### x-on

Attache un écouteur d'événement à un élément.

```html
<button x-on:click="open = true">Ouvrir</button>
```

Raccourci : `@click="open = true"`

### x-text

Met à jour le contenu texte d'un élément.

```html
<span x-text="message"></span>
```

### x-html

Met à jour le contenu HTML d'un élément.

```html
<div x-html="htmlContent"></div>
```

### x-model

Crée une liaison bidirectionnelle sur un élément de formulaire.

```html
<input type="text" x-model="name" />
```

### x-show

Bascule la visibilité d'un élément.

```html
<div x-show="isVisible">Contenu visible</div>
```

### x-if

Ajoute ou supprime un élément du DOM.

```html
<template x-if="isLoggedIn">
  <nav><!-- Menu pour utilisateurs connectés --></nav>
</template>
```

### x-for

Itère sur un tableau pour créer des éléments du DOM.

```html
<template x-for="item in items">
  <li x-text="item"></li>
</template>
```

## Méthodes magiques

### $refs

Accède aux éléments DOM référencés.

```html
<div x-ref="content"></div>
<button @click="$refs.content.innerHTML = 'Nouveau contenu'">Modifier</button>
```

### $el

Fait référence à l'élément DOM actuel.

```html
<button @click="$el.textContent = 'Cliqué'">Cliquez-moi</button>
```

### $watch

Observe les changements d'une propriété.

```html
<div x-init="$watch('count', value => console.log(value))"></div>
```

### $dispatch

Déclenche un événement personnalisé.

```html
<button @click="$dispatch('custom-event', { data: 'example' })">Envoyer</button>
```

## Modificateurs d'événements

- `.prevent` : équivalent à `event.preventDefault()`
- `.stop` : équivalent à `event.stopPropagation()`
- `.outside` : déclenche le gestionnaire si l'événement se produit en dehors de l'élément
- `.window` : écoute l'événement sur l'objet window
- `.debounce` : retarde l'exécution du gestionnaire

## Cycle de vie

### x-init

Exécute des expressions lors de l'initialisation d'un composant.

```html
<div x-init="fetchData()">
  <!-- Contenu du composant -->
</div>
```

## Plugins

Alpine.js peut être étendu avec des plugins pour ajouter des fonctionnalités supplémentaires.

```javascript
Alpine.plugin(myPlugin);
```

## Conclusion

Cette cheatsheet couvre les fonctionnalités principales d'Alpine.js. Pour une documentation plus détaillée et des exemples avancés, consultez la [documentation officielle d'Alpine.js](https://alpinejs.dev/).
