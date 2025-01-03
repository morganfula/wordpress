# Session 5 : Introduction à la création de thèmes WordPress

## Objectifs de la session
- Comprendre la structure d’un thème WordPress.
- Apprendre le rôle des fichiers principaux d’un thème (template files).
- Découvrir les hooks, les templates, et le fichier `functions.php`.
- Créer et activer un thème enfant pour personnaliser un thème existant.

---

## 1. Qu’est-ce qu’un thème WordPress ?
Un thème WordPress contrôle l’apparence et la structure visuelle d’un site. Les thèmes se composent de fichiers PHP, CSS, JavaScript, et parfois HTML. Ils utilisent la hiérarchie des templates pour afficher différents types de contenu.

### Structure de base d’un thème
Un thème WordPress contient généralement les fichiers suivants :

- **index.php** : Fichier principal utilisé par défaut si aucun autre fichier n’est trouvé.
- **style.css** : Fichier de styles pour le design du thème.
- **functions.php** : Ajoute des fonctionnalités au thème.
- **header.php** : Contient l’en-tête du site.
- **footer.php** : Contient le pied de page.
- **sidebar.php** : Contient les barres latérales.
- **single.php** : Gère l’affichage d’un article.
- **page.php** : Gère l’affichage d’une page.

---

## 2. Créer un thème enfant

### Pourquoi créer un thème enfant ?
Un thème enfant permet de personnaliser un thème existant sans perdre vos modifications lors des mises à jour du thème parent.

### Étapes pour créer un thème enfant

#### Créer un dossier pour le thème enfant
1. Accédez au répertoire WordPress : `wp-content/themes/`.
2. Créez un nouveau dossier (exemple : `mon-theme-enfant`).

#### Ajouter un fichier `style.css`
1. Dans le dossier du thème enfant, créez un fichier `style.css`.
2. Ajoutez les informations suivantes au début du fichier :

```css
/*
Theme Name: Mon Thème Enfant
Template: nom-du-theme-parent
*/
```

> Remplacez `nom-du-theme-parent` par le nom exact du dossier du thème parent.

#### Créer un fichier `functions.php`
1. Dans le même dossier, créez un fichier `functions.php`.
2. Ajoutez le code suivant pour inclure les styles du thème parent :

```php
<?php
function mon_theme_enfant_enqueue_styles() {
    wp_enqueue_style('parent-style', get_template_directory_uri() . '/style.css');
}
add_action('wp_enqueue_scripts', 'mon_theme_enfant_enqueue_styles');
?>
```

#### Activer le thème enfant
1. Accédez à **Apparence > Thèmes**.
2. Activez le thème enfant.

---

## 3. Découvrir les Hooks et les Templates

### Les Hooks
Les hooks permettent d'ajouter ou de modifier des fonctionnalités sans toucher directement aux fichiers du thème parent.

#### Types de hooks
- **Action hooks** : Ajoutent du contenu ou exécutent du code à un endroit spécifique.
- **Filter hooks** : Modifient les données avant qu’elles soient affichées.

#### Exemple d’un action hook
Ajouter un texte personnalisé dans le pied de page :

```php
function ajouter_texte_pied_de_page() {
    echo '<p>Site personnalisé avec WordPress</p>';
}
add_action('wp_footer', 'ajouter_texte_pied_de_page');
```

---

### Les Templates

Les fichiers templates suivent une hiérarchie pour afficher différents types de contenu.

#### Exemple de fichiers de templates
- **single.php** : Affiche un article.
- **page.php** : Affiche une page.
- **category.php** : Affiche une catégorie.
- **404.php** : Affiche une page d’erreur 404.

#### Modifier un template
1. Copiez le fichier `single.php` du thème parent dans le dossier du thème enfant.
2. Modifiez le contenu pour ajouter un texte ou une image spécifique.

---

## Exercices pratiques

### Exercice 1 : Créer un thème enfant
1. Créez un dossier pour le thème enfant dans `wp-content/themes/`.
2. Ajoutez un fichier `style.css` avec les informations du thème parent.
3. Ajoutez un fichier `functions.php` pour inclure les styles du thème parent.
4. Activez le thème enfant et vérifiez son fonctionnement.

### Exercice 2 : Ajouter un hook au thème enfant
1. Modifiez le fichier `functions.php` du thème enfant.
2. Ajoutez un texte personnalisé dans le pied de page en utilisant un **action hook**.

### Exercice 3 : Modifier un template
1. Copiez le fichier `single.php` du thème parent dans le thème enfant.
2. Ajoutez un message ou un style spécifique pour personnaliser l’affichage des articles.

---

## Ressources supplémentaires
- [Documentation officielle WordPress - Thèmes](https://developer.wordpress.org/themes/)
- [Hiérarchie des templates](https://developer.wordpress.org/themes/basics/template-hierarchy/)
- [Hooks WordPress](https://developer.wordpress.org/plugins/hooks/)
- [Guide pour les thèmes enfants](https://developer.wordpress.org/themes/advanced-topics/child-themes/)

---

## Quiz de révision
1. Quels sont les fichiers principaux d’un thème WordPress ?
2. Pourquoi utiliser un thème enfant ?
3. Quelle est la différence entre un **action hook** et un **filter hook** ?
4. Comment activer un thème enfant dans WordPress ?
