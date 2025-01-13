# Création d’un site WordPress minimal pas à pas

Ce tutoriel vous propose de créer un **thème WordPress** minimaliste, de manière **progressive**, en détaillant chaque étape.en ajoutant des **commentaires** dans le code.  

---

## Sommaire

1. [Pré-requis](#pré-requis)  
2. [Étape 1 : Mettre en place la Home Page](#étape-1--mettre-en-place-la-home-page)  
    - 1.1. Créer le dossier du thème  
    - 1.2. Créer le fichier `style.css`  
    - 1.3. Créer le fichier `front-page.php`  
    - 1.4. Activer le thème et vérifier l’affichage  
3. [Étape 2 : Ajouter une page About](#étape-2--ajouter-une-page-about)  
    - 2.1. Créer la page About depuis le back-office  
    - 2.2. Créer un template dédié : `page-about.php` (optionnel)  
4. [Étape 3 : Créer un menu et un footer](#étape-3--créer-un-menu-et-un-footer)  
    - 3.1. Enregistrer le menu dans `functions.php`  
    - 3.2. Créer les fichiers `header.php` et `footer.php`  
    - 3.3. Mettre à jour `front-page.php` et `page-about.php`  
    - 3.4. Gérer le menu dans l’admin  
5. [Étape 4 : Ajouter la page Blog](#étape-4--ajouter-la-page-blog)  
    - 4.1. Créer la page « Blog »  
    - 4.2. Configurer la page des articles (Lecture)  
    - 4.3. Créer le template `home.php`  
6. [Étape 5 : Créer la page Post (article individuel)](#étape-5--créer-la-page-post-article-individuel)  
    - 5.1. Créer le fichier `single.php`  
    - 5.2. Tester l’affichage des articles  
7. [Conclusion](#conclusion)  
8. [Ressources utiles](#ressources-utiles)  

---

## Pré-requis

- Une **installation WordPress** fonctionnelle (locale via Wamp, Mamp, Local by Flywheel, etc. ou en ligne sur un hébergeur).
- Un accès au dossier `wp-content/themes/` où nous allons créer et développer notre thème.

---

## Étape 1 : Mettre en place la Home Page

### 1.1. Créer le dossier du thème

1. Dans le répertoire `wp-content/themes/`, créez un dossier, par exemple :  
   `my-simple-theme`
2. Ce dossier contiendra tous les fichiers de votre thème.

---

### 1.2. Créer le fichier `style.css`

Dans votre nouveau dossier `my-simple-theme`, créez un fichier **`style.css`**.  
Ce fichier doit **impérativement** contenir les métadonnées suivantes pour que WordPress reconnaisse le thème :

```css
/*
Theme Name: My Simple Theme
Author: Votre Nom
Description: Un thème WordPress minimaliste, créé pas à pas.
Version: 1.0
*/

/* Exemples de styles globaux */
body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
}

h1, h2, h3 {
    font-weight: normal;
    margin: 0 0 10px 0;
}

.container {
    width: 80%;
    margin: 20px auto;
}
```

---

### 1.3. Créer le fichier `front-page.php`

Toujours dans `my-simple-theme`, créez `front-page.php`.  
Ce fichier est le template utilisé par WordPress pour afficher la page d’accueil si l’on choisit une page statique en tant que Home.

Pour l’instant, faisons quelque chose de très simple :

```php
<?php
/*
 * front-page.php
 * Template pour la page d'accueil
 */
?>
<!DOCTYPE html>
<html <?php language_attributes(); ?>>
<head>
    <meta charset="<?php bloginfo('charset'); ?>">
    <title><?php bloginfo('name'); ?> - <?php bloginfo('description'); ?></title>
    <?php wp_head(); ?>
</head>
<body <?php body_class(); ?>>

    <h1>Bienvenue sur la Home Page de mon thème</h1>

    <?php wp_footer(); ?>
</body>
</html>
```

---

### 1.4. Activer le thème et vérifier l’affichage

1. Dans le tableau de bord WordPress, allez dans : **Apparence > Thèmes**.
2. Vous devriez voir apparaître « My Simple Theme ». Activez-le.
3. Allez dans **Réglages > Lecture** et sélectionnez la page que vous souhaitez afficher en Page d’accueil statique. Si vous n’avez pas encore créé de page dans WordPress, créez-en une vide nommée « Home », puis définissez-la comme page d’accueil.
4. Accédez à l’URL de votre site : vous devriez voir le message de test « Bienvenue sur la Home Page de mon thème ».

---

## Étape 2 : Ajouter une page About

### 2.1. Créer la page About depuis le back-office

1. Dans le back-office de WordPress, allez dans **Pages > Ajouter**.
2. Créez une page nommée About (ou « À propos »).
3. Ajoutez quelques lignes de texte pour tester, et Publiez la page.

### 2.2. Créer un template dédié : `page-about.php` (optionnel)

Si vous souhaitez personnaliser la mise en page de votre page About, vous pouvez créer un fichier `page-about.php` dans le dossier du thème :

```php
<?php
/*
 * Template Name: About
 * Description: Modèle de page pour la page "About"
 */

get_header();
?>

<h1><?php the_title(); ?></h1>
<div>
    <?php
    if ( have_posts() ) :
        while ( have_posts() ) : the_post();
            the_content();
        endwhile;
    endif;
    ?>
</div>

<?php
get_footer();
```

Pour l’utiliser :

1. Dans l’admin, éditez la page About.
2. Dans la colonne de droite, cherchez l’option « Attributs de page » ou « Template », et choisissez « About ».

---

## Étape 3 : Créer un menu et un footer

### 3.1. Enregistrer le menu dans `functions.php`

Créez un fichier `functions.php` à la racine du thème :

```php
<?php
/**
 * Fonctions principales du thème
 */

// 1) Activer la gestion des menus
function my_theme_register_menus() {
    register_nav_menu('primary', __('Menu Principal', 'my-simple-theme'));
}
add_action('after_setup_theme', 'my_theme_register_menus');
```

---

### 3.2. Créer les fichiers `header.php` et `footer.php`

#### `header.php`

```php
<!DOCTYPE html>
<html <?php language_attributes(); ?>>
<head>
    <meta charset="<?php bloginfo('charset'); ?>">
    <title><?php bloginfo('name'); ?> - <?php is_front_page() ? bloginfo('description') : wp_title(''); ?></title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <?php wp_head(); ?>
</head>
<body <?php body_class(); ?>>

<header>
    <h1><?php bloginfo('name'); ?></h1>
    <p><?php bloginfo('description'); ?></p>
    <nav>
        <?php
        wp_nav_menu(array(
            'theme_location' => 'primary',
            'container'      => false
        ));
        ?>
    </nav>
</header>

<div class="container">
```

#### `footer.php`

```php
</div> <!-- Fin .container -->

<footer>
    <p>&copy; <?php echo date('Y'); ?> - <?php bloginfo('name'); ?></p>
    <?php wp_footer(); ?>
</footer>
</body>
</html>
```

---

### 3.3. Mettre à jour `front-page.php` et `page-about.php`

Exemple : `front-page.php` :

```php
<?php
get_header();
?>

<h1><?php the_title(); ?></h1>

<?php
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_content();
    endwhile;
endif;
?>

<?php
get_footer();
```

---

### 3.4. Gérer le menu dans l’admin

1. Dans le back-office WordPress, allez dans **Apparence > Menus**.
2. Créez un Nouveau menu (par exemple « Menu Principal »).
3. Ajoutez vos pages « Home », « About », etc.
4. Assignez ce menu à l’emplacement « Menu Principal » (défini dans `functions.php`).

---

## Étape 4 : Ajouter la page Blog

### 4.1. Créer la page « Blog »

1. Dans l’admin, allez dans **Pages > Ajouter**.
2. Créez une page nommée « Blog » (laissez-la vide ou non).

### 4.2. Configurer la page des articles (Lecture)

1. Dans **Réglages > Lecture** :
    - Page d’accueil : choisissez « Home ».
    - Page des articles : choisissez « Blog ».

### 4.3. Créer le template `home.php`

Créez un fichier `home.php` dans le dossier du thème :

```php
<?php
get_header();
?>

<h1>Notre Blog</h1>

<?php
if ( have_posts() ) :
    while ( have_posts() ) : the_post(); ?>
        <article>
            <h2>
                <a href="<?php the_permalink(); ?>">
                    <?php the_title(); ?>
                </a>
            </h2>
            <p><?php the_excerpt(); ?></p>
        </article>
    <?php endwhile;
    the_posts_pagination();
else :
    echo '<p>Aucun article trouvé.</p>';
endif;
?>

<?php
get_footer();
```

---

## Étape 5 : Créer la page Post (article individuel)

### 5.1. Créer le fichier `single.php`

```php
<?php
get_header();
?>

<?php
if ( have_posts() ) :
    while ( have_posts() ) : the_post(); ?>
        <article>
            <h1><?php the_title(); ?></h1>
            <div>
                <?php the_content(); ?>
            </div>
        </article>
        <a href="<?php echo get_permalink( get_option( 'page_for_posts' ) ); ?>">
            ← Retour au Blog
        </a>
    <?php endwhile;
endif;
?>

<?php
get_footer();
```

---

### 5.2. Tester l’affichage des articles

1. Dans l’admin, allez dans **Articles > Ajouter**.
2. Créez un ou deux articles avec un titre et du contenu.
3. Visitez la page « Blog » : vous devriez voir la liste de vos articles.
4. En cliquant sur un article, vous accédez à la page `single.php` affichant l’article complet.

---

## Conclusion

À ce stade, vous avez un site WordPress fonctionnel avec :

- Une Home Page (gérée par `front-page.php`)
- Une page About avec un template dédié ou non (`page-about.php`)
- Un menu principal (géré via l’admin et enregistré dans `functions.php`)
- Une page Blog listant les articles (gérée par `home.php`)
- Des articles individuels avec leur page (`single.php`)

Bien sûr, il reste des optimisations possibles :

- **Personnaliser le CSS** : Ajoutez vos styles dans `style.css` ou utilisez un préprocesseur (Sass).
- **Images de mise en avant** : Activez-les avec `add_theme_support('post-thumbnails')` dans `functions.php`.
- **Responsivité** : Assurez-vous que votre mise en page s’adapte bien aux mobiles et tablettes.
- **SEO** : Installez des plugins comme Yoast SEO pour améliorer la visibilité.

Ce tutoriel vous donne les bases pour comprendre la structure d’un thème WordPress. Libre à vous d’enrichir ce thème (widgets, sidebar, custom post types, etc.) au fur et à mesure de vos besoins.

---

## Ressources utiles

- [Documentation officielle WordPress (FR)](https://fr.wordpress.org/support/)
- [Documentation officielle WordPress (EN)](https://developer.wordpress.org/)
- [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/)
- [Navigation Menus](https://developer.wordpress.org/themes/functionality/navigation-menus/)

