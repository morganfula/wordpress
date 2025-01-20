# Session 6 : Hooks WordPress et Intégration de ACF

Dans cette session, nous allons explorer l'utilisation des **Hooks** (`add_action`, `add_filter`) dans WordPress et intégrer **Advanced Custom Fields (ACF)** pour enrichir notre thème avec des champs personnalisés.

## Sommaire

1. [Introduction aux Hooks WordPress](#introduction-aux-hooks-wordpress)
2. [Utilisation des Hooks `add_action` et `add_filter`](#utilisation-des-hooks-add_action-et-add_filter)
3. [Exemples concrets d'utilisation](#exemples-concrets-dutilisation)
4. [Intégration de Advanced Custom Fields (ACF)](#intégration-de-advanced-custom-fields-acf)
5. [Mise en pratique avec des champs personnalisés](#mise-en-pratique-avec-des-champs-personnalisés)
6. [Conclusion](#conclusion)

---

## Introduction aux Hooks WordPress

Les **Hooks** sont un des concepts les plus puissants de WordPress. Ils permettent de **modifier ou d’étendre** le comportement de WordPress sans modifier le cœur du CMS.

Il existe deux types principaux de Hooks :
- **`add_action`** : Permet d'ajouter du code à un moment spécifique dans l'exécution de WordPress.
- **`add_filter`** : Permet de modifier ou filtrer une valeur avant qu’elle ne soit affichée ou utilisée.

---

## Utilisation des Hooks `add_action` et `add_filter`

### `add_action` : Ajouter du contenu ou des fonctionnalités

Exemple : Ajouter du texte après le contenu de chaque article.

Ajoutez ce code dans `functions.php` :

```php
function ajouter_texte_apres_article($content) {
    if (is_single()) {
        $content .= '<p>Merci d’avoir lu cet article !</p>';
    }
    return $content;
}
add_filter('the_content', 'ajouter_texte_apres_article');
```

### `add_filter` : Modifier une valeur retournée par WordPress

Exemple : Modifier le titre de chaque article

Ajoutez ce code dans `functions.php` :

```php
function modifier_titre_article($title) {
    if (is_single()) {
        $title = '★ ' . $title;
    }
    return $title;
}
add_filter('the_title', 'modifier_titre_article');
```

Ces exemples montrent comment les Hooks permettent de **personnaliser facilement** un site WordPress sans modifier directement les fichiers de base.

---

## Exemples concrets d'utilisation

### 1. Ajouter un script JavaScript personnalisé
Ajoutez ce code dans `functions.php` pour charger un fichier `script.js` dans le thème :

```php
<?php
/**
 * Fonctions principales du thème
 */

// 1) Activer la gestion des menus
function my_theme_register_menus() {
    register_nav_menu('primary', __('Menu Principal', 'my-simple-theme'));
}

// 2) Charger les styles et scripts
function mytheme_styles_scripts() {
  // Charger la feuille de style principale du thème
  wp_enqueue_style('my-simple-theme-style', get_stylesheet_uri());
  
  // Charger le fichier JavaScript personnalisé situé dans le dossier js/
  wp_enqueue_script('script-name', get_template_directory_uri() . '/js/script.js', array(), false, true);
}

// Ajouter les actions WordPress pour charger les styles et scripts et enregistrer le menu
add_action('wp_enqueue_scripts', 'mytheme_styles_scripts');
add_action('after_setup_theme', 'my_theme_register_menus');
```

### 2. Personnaliser le footer avec un Hook
Ajoutez ce code dans `functions.php` :

```php
function personnaliser_footer() {
    echo '<p>© ' . date('Y') . ' - Tous droits réservés.</p>';
}
add_action('wp_footer', 'personnaliser_footer');
```

---

## Intégration de Advanced Custom Fields (ACF)

### Installation
1. Installez le plugin **Advanced Custom Fields** depuis le répertoire des plugins WordPress.
2. Activez-le.

### Création d'un champ personnalisé
1. Allez dans **ACF > Champs personnalisés**.
2. Ajoutez un nouveau groupe de champs.
3. Créez un champ nommé `sous_titre` de type **Texte**.

### Affichage du champ dans `single.php`
Ajoutez ce code dans `single.php` :

```php
<?php
get_header();
?>

<article>
    <h1><?php the_title(); ?></h1>
    <h2><?php the_field('sous_titre'); ?></h2>
    <div><?php the_content(); ?></div>
</article>

<?php
get_footer();
```

Cela permettra d’afficher un sous-titre personnalisé pour chaque article si le champ `sous_titre` est renseigné dans l’administration.

---

## Mise en pratique avec des champs personnalisés

### Ajouter un champ personnalisé dans `front-page.php`
Ajoutez ce code pour afficher un texte personnalisé depuis ACF sur la page d'accueil :

```php
<h1><?php the_title(); ?></h1>
<p><?php the_field('texte_accueil'); ?></p>
```

Assurez-vous d’avoir créé un champ personnalisé nommé `texte_accueil` dans l’admin.

---

## Conclusion

Dans cette session, nous avons exploré :
- Les **Hooks WordPress** (`add_action`, `add_filter`) et leur utilisation.
- Comment **ajouter des fonctionnalités** avec des Hooks.
- L’intégration du plugin **Advanced Custom Fields (ACF)** pour enrichir le contenu.
- Des **exemples concrets** pour appliquer ces concepts dans un projet WordPress.

Ces outils sont essentiels pour **développer des thèmes WordPress professionnels et personnalisés**.

### Ressources utiles :
- [Documentation officielle WordPress sur les Hooks](https://developer.wordpress.org/plugins/hooks/)
- [Advanced Custom Fields](https://www.advancedcustomfields.com/)

---

Ce guide vous permet d'exploiter pleinement les Hooks WordPress et d’intégrer ACF efficacement dans votre thème. N’hésitez pas à tester et expérimenter !
