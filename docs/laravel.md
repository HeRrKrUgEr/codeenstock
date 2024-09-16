# Laravel Artisan & Eloquent Query Cheatsheet

## Commandes Artisan

### **Lancer votre application**

```bash
php artisan serve
```

Démarre un serveur de développement local à l'adresse <http://127.0.0.1:8000>.

### **Vider les caches**

```bash
php artisan cache:clear
```

Vide tous les caches de l'application.

### **Vider la vue compilée**

```bash
php artisan view:clear
```

Efface le cache des vues Blade compilées.

### **Exécuter les migrations**

```bash
php artisan migrate
```

Exécute les migrations de la base de données pour créer ou mettre à jour les tables.

### **Annuler la dernière migration**

```bash
php artisan migrate:rollback
```

Annule la dernière migration exécutée.

### **Créer un modèle avec migration, factory et contrôleur**

```bash
php artisan make:model Post -mfcr
```

Crée un modèle `Post` avec une migration, une factory, un contrôleur et une ressource.

### **Lister toutes les routes enregistrées**

```bash
php artisan route:list
```

Affiche la liste de toutes les routes définies dans l'application.

### **Créer un contrôleur de ressources**

```bash
php artisan make:controller UserController --resource
```

Crée un contrôleur avec des méthodes de ressources (index, create, store, show, edit, update, destroy).

### **Générer une clé d'application**

```bash
php artisan key:generate
```

Génère une nouvelle clé d'application et la définit dans le fichier `.env`.

### **Créer une nouvelle migration**

```bash
php artisan make:migration create_posts_table
```

Crée une nouvelle migration pour une table `posts`.

### **Créer une nouvelle commande personnalisée**

```bash
php artisan make:command MyCustomCommand
```

Crée une nouvelle commande artisan personnalisée.

### **Exécuter Tinker (console interactive pour tester des commandes Eloquent)**

```bash
php artisan tinker
```

Démarre Tinker pour interagir avec l'application via une interface CLI.

### **Lancer une commande planifiée manuellement**

```bash
php artisan schedule:run
```

Exécute les commandes planifiées qui devaient être déclenchées à cette heure.

---

## Exemples d'utilisation d'Eloquent Query

### **Récupérer tous les enregistrements**

```php
$users = User::all();
```

### **Récupérer un enregistrement par son ID**

```php
$user = User::find(1);
```

### **Récupérer plusieurs enregistrements par ID**

```php
$users = User::find([1, 2, 3]);
```

### **Récupérer le premier enregistrement correspondant à une condition**

```php
$user = User::where('email', 'example@example.com')->first();
```

### **Récupérer ou créer un enregistrement si non existant**

```php
$user = User::firstOrCreate(
    ['email' => 'example@example.com'],
    ['name' => 'John Doe', 'password' => bcrypt('password')]
);
```

### **Ajouter un nouvel enregistrement**

```php
$user = new User;
$user->name = 'John Doe';
$user->email = 'john@example.com';
$user->password = bcrypt('password');
$user->save();
```

### **Créer un nouvel enregistrement en utilisant `create`**

```php
User::create([
    'name' => 'Jane Doe',
    'email' => 'jane@example.com',
    'password' => bcrypt('password')
]);
```

### **Mettre à jour un enregistrement**

```php
$user = User::find(1);
$user->name = 'Jane Doe';
$user->save();
```

### **Mettre à jour plusieurs enregistrements**

```php
User::where('status', 'inactive')->update(['status' => 'active']);
```

### **Supprimer un enregistrement**

```php
$user = User::find(1);
$user->delete();
```

### **Supprimer plusieurs enregistrements**

```php
User::where('status', 'inactive')->delete();
```

### **Utiliser une requête avec plusieurs conditions**

```php
$users = User::where('status', 'active')
    ->where('age', '>', 18)
    ->get();
```

### **Récupérer des enregistrements triés**

```php
$users = User::orderBy('name', 'asc')->get();
```

### **Pagination des résultats**

```php
$users = User::paginate(10);
```

### **Relations Eloquent**

#### **Récupérer les posts d'un utilisateur (relation `hasMany`)**

```php
$user = User::find(1);
$posts = $user->posts;
```

#### **Récupérer l'utilisateur d'un post (relation `belongsTo`)**

```php
$post = Post::find(1);
$user = $post->user;
```

#### **Récupérer les rôles d'un utilisateur (relation `belongsToMany`)**

```php
$user = User::find(1);
$roles = $user->roles;
```

#### **Récupérer les commentaires d'un post avec les utilisateurs associés (relation imbriquée)**

```php
$post = Post::with('comments.user')->find(1);
$comments = $post->comments;
```

---

### **Comptes et Statistiques**

#### **Compter le nombre d'enregistrements**

```php
$userCount = User::count();
```

#### **Compter les enregistrements avec une condition**

```php
$activeUsers = User::where('status', 'active')->count();
```

### **Requêtes complexes avec Eloquent**

#### **Requête avec des jointures**

```php
$posts = Post::join('users', 'posts.user_id', '=', 'users.id')
    ->select('posts.*', 'users.name')
    ->get();
```

#### **Groupage des résultats**

```php
$users = User::selectRaw('count(*) as user_count, status')
    ->groupBy('status')
    ->get();
```

#### **Utiliser des sous-requêtes**

```php
$latestPosts = Post::select('user_id', Post::raw('MAX(created_at) as latest_post'))
    ->groupBy('user_id');

$usersWithLatestPosts = User::joinSub($latestPosts, 'latest_posts', function ($join) {
    $join->on('users.id', '=', 'latest_posts.user_id');
})->get();
```

#### **Requêtes en lot (chunking)**

```php
User::chunk(100, function ($users) {
    foreach ($users as $user) {
        // Traiter chaque utilisateur
    }
});
```

### **Utiliser des transactions**

```php
DB::transaction(function () {
    $user = User::create([
        'name' => 'Jane Doe',
        'email' => 'jane@example.com',
        'password' => bcrypt('password')
    ]);

    $user->posts()->create([
        'title' => 'Mon premier post',
        'body' => 'Le contenu du post...'
    ]);
});
```

---

## Autres commandes Artisan utiles

### **Effacer la file d'attente**

```bash
php artisan queue:flush
```

### **Vérifier l'état des tâches planifiées**

```bash
php artisan schedule:list
```

### **Optimiser les fichiers de l'application**

```bash
php artisan optimize
```

### **Créer une middleware**

```bash
php artisan make:middleware CheckAge
```

### **Créer une nouvelle factory**

```bash
php artisan make:factory PostFactory
```

---

## Conclusion

Cette cheatsheet couvre les principales commandes Artisan et propose une variété d'exemples de requêtes Eloquent, des plus basiques aux plus complexes. Utilisez cette référence pour améliorer votre productivité dans vos projets Laravel.
