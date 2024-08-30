# Cheat Sheet Razor .NET Core

## Introduction

Razor est un moteur de template de syntaxe qui permet de combiner du code C# avec du HTML de manière propre et lisible. Il est largement utilisé dans les applications ASP.NET Core pour la création de vues dynamiques.

## Syntaxe de Base

### Code C# dans Razor

```html
@{ var message = "Bonjour, Monde!"; }
<p>@message</p>
```

### Expressions C# Inline

```html
<p>Le résultat est: @("Hello, " + "World!")</p>
```

### Commentaires Razor

```html
@* Ceci est un commentaire Razor *@
```

### Directives Importantes

```html
@using MonProjet.Models // Importer un espace de nom @model
MonProjet.Models.MonModele // Spécifier le modèle de vue @inject MonService
myService // Injection de service @inherits MaClasseDeBase // Inhérer d'une
classe de base @functions { // Ajouter des fonctions C# custom }
```

## Boucles et Conditions

### Conditionnelle `if`

```html
@if (Model.IsLoggedIn) {
<p>Bienvenue, @Model.UserName!</p>
} else {
<p>Veuillez vous connecter.</p>
}
```

### Boucle `for`

```html
@for (int i = 0; i < 10; i++) {
<p>Numéro: @i</p>
}
```

### Boucle `foreach`

```html
@foreach (var item in Model.Items) {
<p>@item.Name</p>
}
```

## Liens et Actions

### Générer un lien d'action

```html
<a asp-controller="Home" asp-action="Index">Accueil</a>
```

### Lien avec paramètres

```html
<a asp-controller="Produit" asp-action="Détails" asp-route-id="@item.Id"
  >Voir Détails</a
>
```

## Affichage Conditionnel et Boucles

### Boucle `while`

```html
@{ int i = 0; while (i < 5) {
<p>Compteur: @i</p>
i++; } }
```

### Condition `switch`

```html
@switch (Model.TypeUtilisateur) { case "Admin":
<p>Vous avez les privilèges d'administrateur.</p>
break; case "Utilisateur":
<p>Bienvenue, utilisateur.</p>
break; default:
<p>Type utilisateur inconnu.</p>
break; }
```

## Helpers HTML

### Label et Input

```html
@Html.LabelFor(model => model.Nom) @Html.TextBoxFor(model => model.Nom)
```

### Checkbox et Radio Button

```html
@Html.CheckBoxFor(model => model.EstActif) @Html.RadioButtonFor(model =>
model.Genre, "Homme") @Html.RadioButtonFor(model => model.Genre, "Femme")
```

### DropdownList

```html
@Html.DropDownListFor(model => model.CatégorieId, new
SelectList(Model.Catégories, "Id", "Nom"))
```

## Validation et Messages d'Erreur

### Afficher les erreurs de validation

```html
@Html.ValidationSummary(true) @Html.ValidationMessageFor(model => model.Nom)
```

## Partials et Layouts

### Utiliser un Layout

```html
@{ Layout = "_Layout.cshtml"; }
```

### Rendu d'une vue partielle

```html
@Html.Partial("_PartialView", Model.PartieDeLaVue)
```

### Sections et Rendu

```html
@section Scripts {
<script src="monScript.js"></script>
}
```

### Inclusion de fichiers JS et CSS

```html
@section Styles {
<link rel="stylesheet" href="~/css/site.css" />
}
```
