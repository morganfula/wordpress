# Session 6 : Développement d’un thème personnalisé WordPress

## Objectifs de la session
- Comprendre les étapes pour créer un thème WordPress à partir de zéro.
- Apprendre à structurer les fichiers d’un thème personnalisé.
- Intégrer du contenu dynamique avec les fonctions WordPress.
- Tester et activer un thème personnalisé.

---

## 1. Introduction au développement de thèmes WordPress
Un thème personnalisé vous permet de contrôler complètement l’apparence et les fonctionnalités de votre site.

### Pré-requis
- Connaissance de base en HTML, CSS, et PHP.
- Installation locale de WordPress avec accès au répertoire `wp-content/themes/`.

---

## 2. Étapes pour créer un thème personnalisé

### Étape 1 : Créer un dossier pour le thème
- Accédez au répertoire `wp-content/themes/`.
- Créez un nouveau dossier pour votre thème (exemple : `mon-theme-personnalise`).

### Étape 2 : Ajouter le fichier `style.css`
```css
/*
Theme Name: Mon Thème Personnalisé
author: Votre Nom
Description: Un thème WordPress développé de zéro.
Version: 1.0
*/
```

### Étape 3 : Ajouter le fichier `index.php`
```html
<!DOCTYPE html>
<html>
<head>
    <title>Mon Thème Personnalisé</title>
    <?php wp_head(); ?>
</head>
<body>
    <h1>Bienvenue sur mon thème personnalisé</h1>
    <?php wp_footer(); ?>
</body>
</html>
```

### Étape 4 : Ajouter le fichier `functions.php`
```php
<?php
function mon_theme_enqueue_styles() {
    wp_enqueue_style('style', get_stylesheet_uri());
}
add_action('wp_enqueue_scripts', 'mon_theme_enqueue_styles');
?>
```

### Étape 5 : Ajouter des fichiers supplémentaires
- `header.php` : Contient l’en-tête du site.
- `footer.php` : Contient le pied de page.
- `single.php` : Gère l’affichage des articles.
- `page.php` : Gère l’affichage des pages.

#### Exemple : Contenu du fichier `header.php`
```php
<!DOCTYPE html>
<html>
<head>
    <title><?php bloginfo('name'); ?></title>
    <?php wp_head(); ?>
</head>
<body>
```

#### Exemple : Contenu du fichier `footer.php`
```php
<?php wp_footer(); ?>
</body>
</html>
```

#### Exemple : Contenu du fichier `single.php` (Gère l’affichage d’un article unique)
```php
<?php get_header(); ?>

<?php
if ( have_posts() ) :
    while ( have_posts() ) :
        the_post(); 
        the_title('<h1>', '</h1>');
        the_content();
    endwhile; 
endif;
?>

<?php get_footer(); ?>
```

#### Exemple : Contenu du fichier `page.php` (Gère l’affichage d’une page)
```php
<?php get_header(); ?>

<?php
if ( have_posts() ) :
    while ( have_posts() ) :
        the_post(); 
        the_title('<h1>', '</h1>');
        the_content();
    endwhile; 
endif;
?>

<?php get_footer(); ?>
```

---

## 3. Tester le thème personnalisé
1. Accédez à **Apparence > Thèmes** dans le tableau de bord WordPress.
2. Activez votre thème personnalisé.
3. Accédez à la page d’accueil pour vérifier que votre thème fonctionne.

---

## 4. Ajouter du contenu dynamique

### 4.1. Titre et description du site
Dans `header.php`, utilisez les fonctions suivantes pour afficher dynamiquement le titre et la description du site :
```php
<h1><?php bloginfo('name'); ?></h1>
<p><?php bloginfo('description'); ?></p>
```

### 4.2. Boucle WordPress
La boucle WordPress est utilisée pour afficher les articles :
```php
<?php if (have_posts()) : ?>
    <?php while (have_posts()) : the_post(); ?>
        <h2><?php the_title(); ?></h2>
        <p><?php the_excerpt(); ?></p>
        <a href="<?php the_permalink(); ?>">Lire la suite</a>
    <?php endwhile; ?>
<?php else : ?>
    <p>Aucun article trouvé.</p>
<?php endif; ?>
```

---

## Exercices pratiques

### Exercice 1 : Créer un thème personnalisé de base
1. Créez un dossier pour le thème.
2. Ajoutez les fichiers `style.css`, `index.php`, et `functions.php`.
3. Activez le thème dans WordPress.

### Exercice 2 : Ajouter un en-tête et un pied de page
1. Créez les fichiers `header.php` et `footer.php`.
2. Modifiez `index.php` pour inclure ces fichiers :
    ```php
    <?php get_header(); ?>
    <h1>Contenu principal</h1>
    <?php get_footer(); ?>
    ```

### Exercice 3 : Utiliser la boucle WordPress
1. Ajoutez la boucle WordPress dans `index.php` pour afficher les articles.
2. Testez le fonctionnement sur votre site.

---

## Ressources supplémentaires
- [Documentation officielle WordPress - Thèmes](https://developer.wordpress.org/themes/)
- [Fonctions WordPress](https://developer.wordpress.org/reference/)
- [Hiérarchie des templates WordPress](https://developer.wordpress.org/themes/basics/template-hierarchy/)

---

## Quiz de révision
1. Quels sont les fichiers essentiels pour un thème WordPress personnalisé ?
2. À quoi sert la fonction `get_header()` ?
3. Qu’est-ce que la boucle WordPress ?
4. Comment inclure le fichier CSS principal dans un thème WordPress ?
