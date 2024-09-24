# Laravel Blade Cheatsheet

## 1. Introduction à Blade

Blade est le moteur de template de Laravel qui permet d'utiliser du code PHP dans les fichiers `.blade.php` tout en restant propre et lisible. Blade ne ralentit pas l'application car il est compilé en PHP natif.

## 2. Directives de base

### `{{ $variable }}`

Affiche une variable, avec échappement des caractères HTML pour éviter les failles XSS.

```blade
{{ $name }}
```

Si `$name` contient `"Vincent"`, le résultat affichera simplement:

```
Vincent
```

### `{!! $variable !!}`

Affiche une variable sans échappement HTML, utile si la variable contient du code HTML.

```blade
{!! $html !!}
```

Si `$html` contient `"<strong>Salut</strong>"`, le résultat sera:

```
<strong>Salut</strong>
```

### `@if`, `@elseif`, `@else`

Utilisé pour les conditions.

```blade
@if($age > 18)
    <p>Tu es un adulte.</p>
@elseif($age == 18)
    <p>Tu viens juste d'avoir 18 ans!</p>
@else
    <p>Tu es mineur.</p>
@endif
```

Selon la valeur de `$age`, une des conditions sera évaluée et la phrase correspondante sera affichée.

### `@unless`

Inverse de `@if`. Exécute le bloc si la condition est fausse.

```blade
@unless($logged_in)
    <p>Veuillez vous connecter.</p>
@endunless
```

Cela affiche "Veuillez vous connecter" uniquement si `$logged_in` est `false`.

### `@isset` et `@empty`

Vérifie si une variable est définie ou vide.

```blade
@isset($user)
    <p>L'utilisateur existe.</p>
@endisset

@empty($user)
    <p>Aucun utilisateur trouvé.</p>
@endempty
```

Si `$user` est défini, la première condition s'affichera. Si `$user` est vide ou indéfini, la deuxième condition s'affichera.

## 3. Boucles

### `@for` / `@endfor`

Boucle `for`.

```blade
@for ($i = 0; $i < 5; $i++)
    <p>Itération numéro {{ $i }}</p>
@endfor
```

Cela affichera:

```
Itération numéro 0
Itération numéro 1
Itération numéro 2
Itération numéro 3
Itération numéro 4
```

### `@foreach` / `@endforeach`

Boucle `foreach`.

```blade
@foreach ($users as $user)
    <p>{{ $user->name }}</p>
@endforeach
```

Si `$users` contient une liste d'utilisateurs, chaque nom sera affiché.

### `@forelse` / `@empty`

Boucle `foreach` avec une condition pour gérer le cas où la collection est vide.

```blade
@forelse ($posts as $post)
    <p>{{ $post->title }}</p>
@empty
    <p>Aucun post trouvé.</p>
@endforelse
```

Si `$posts` contient des articles, ils seront listés. Sinon, "Aucun post trouvé" sera affiché.

### `@while` / `@endwhile`

Boucle `while`.

```blade
@while($count < 5)
    <p>Nombre actuel: {{ $count }}</p>
    @php $count++; @endphp
@endwhile
```

Tant que `$count` est inférieur à 5, la boucle continue.

## 4. Affichage conditionnel

### `@auth` / `@guest`

Vérifie si l'utilisateur est authentifié ou invité.

```blade
@auth
    <p>Bienvenue, {{ auth()->user()->name }} !</p>
@endauth

@guest
    <p>Veuillez vous connecter.</p>
@endguest
```

Le premier bloc s'affichera pour les utilisateurs connectés, et le second pour les invités.

### `@switch` / `@case` / `@default`

Structure de contrôle `switch`.

```blade
@switch($role)
    @case('admin')
        <p>Bienvenue, administrateur !</p>
        @break
    @case('user')
        <p>Bienvenue, utilisateur !</p>
        @break
    @default
        <p>Bienvenue, invité !</p>
@endswitch
```

Selon la valeur de `$role`, un message différent sera affiché.

## 5. Sections et Layouts

### `@extends`

Hérite d'un layout parent.

```blade
@extends('layouts.app')
```

Cela signifie que la vue actuelle utilise le layout `layouts.app`.

### `@section` / `@endsection`

Définit une section à remplir dans un layout.

```blade
@section('title', 'Accueil')

@section('content')
    <p>Ceci est la page d'accueil.</p>
@endsection
```

### `@yield`

Place un contenu provenant d'une section dans le layout.

```blade
<title>@yield('title')</title>
```

### `@include`

Inclut une vue partielle.

```blade
@include('partials.header')
```

Cela inclut le contenu de `partials.header`.

## 6. Boucles et Variables spéciales

### `$loop->index`

Donne l'index actuel de la boucle (commence à 0).

```blade
@foreach($items as $item)
    <p>Index: {{ $loop->index }}</p>
@endforeach
```

Cela affiche l'index de chaque itération dans la boucle.

### `$loop->count`

Le nombre total d'éléments dans la boucle.

```blade
@foreach($items as $item)
    <p>Total d'éléments: {{ $loop->count }}</p>
@endforeach
```

Affiche le nombre total d'éléments dans la boucle.

## 7. Composants et Slots

### `@component` / `@endcomponent`

Crée des composants personnalisés.

```blade
@component('components.alert')
    <strong>Attention!</strong> Il y a un problème.
@endcomponent
```

### `@slot` / `@endslot`

Définit des zones personnalisées dans les composants.

```blade
@component('components.alert')
    @slot('title')
        Erreur 404
    @endslot
    La page demandée n'existe pas.
@endcomponent
```

## 8. Commentaire Blade

### `{{-- Comment --}}`

Crée un commentaire qui ne sera pas affiché dans le HTML rendu.

```blade
{{-- Ceci est un commentaire Blade --}}
```

## 9. Traitement des erreurs

### `@error`

Affiche un message d'erreur pour un champ donné.

```blade
@error('email')
    <p class="error">{{ $message }}</p>
@enderror
```

Si le champ `email` contient une erreur, le message sera affiché.

## 10. Autres Directives Utiles

### `@csrf`

Insère un champ CSRF dans les formulaires pour éviter les attaques CSRF.

```blade
<form method="POST">
    @csrf
</form>
```

### `@method`

Spécifie une méthode HTTP différente (comme PUT ou DELETE).

```blade
<form method="POST">
    @method('PUT')
</form>
```

Cela dit au serveur que la méthode HTTP est `PUT`, même si le formulaire utilise `POST`.

### `@php` / `@endphp`

Exécute du code PHP pur à l'intérieur d'une vue.

```blade
@php
    $variable = 'valeur';
@endphp
```

## 11. Directives de boucle personnalisée

### `@break`

Interrompt une boucle.

```blade
@foreach($items as $item)
    @if($item->id == 5)
        @break
    @endif
    <p>{{ $item->name }}</p>
@endforeach
```

### `@continue`

Passe à l'itération suivante dans une boucle.

```blade
@foreach($items as $item)
    @if($item->id == 1)
        @continue
    @endif
    <p>{{ $item->name }}</p>
@endforeach
```

## 12. Helpers

### `@includeIf`

Inclut une vue seulement si elle existe.

```blade
@includeIf('view.name')
```

### `@includeWhen`

Inclut une vue seulement si une condition est vraie.

```blade
@includeWhen($boolean, 'view.name')
```

### `@includeUnless`

Inclut une vue si une condition est fausse.

```blade
@includeUnless($boolean, 'view.name')
```
