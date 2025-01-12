# Session 5 : Développement d’un thème personnalisé WordPress

## Objectifs de la session
- Comprendre les étapes pour créer un thème WordPress à partir de zéro.
- Apprendre à structurer les fichiers d’un thème personnalisé.
- Intégrer du contenu dynamique avec les fonctions WordPress.
- Tester et activer un thème personnalisé.

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

   ```plaintext
   my-simple-theme
   ```

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
```

Vous pouvez également y ajouter des règles CSS globales :

```css
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

... (le reste du contenu suit cette structure) ...

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

Ce tutoriel vous donne les bases pour comprendre la structure d’un thème WordPress. Libre à vous d’enrichir ce thème (widget, sidebar, custom post types, etc.) au fur et à mesure de vos besoins.

---

## Ressources utiles

- [Documentation officielle WordPress (FR)](https://fr.wordpress.org/support/)
- [Documentation officielle WordPress (EN)](https://wordpress.org/support/)
- [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/)
- [Navigation Menus](https://developer.wordpress.org/themes/functionality/navigation-menus/)
- [The Loop (Boucle WordPress)](https://developer.wordpress.org/themes/basics/the-loop/)
