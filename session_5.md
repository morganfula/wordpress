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
    - 1.3. Créer les fichiers `header.php` et `footer.php`  
    - 1.4. Créer le fichier `front-page.php`  
    - 1.5. Activer le thème et vérifier l’affichage  
3. [Étape 2 : Ajouter une page About](#étape-2--ajouter-une-page-about)  
    - 2.1. Créer la page About depuis le back-office  
    - 2.2. Créer un template dédié : `page-about.php` (optionnel)  
4. [Étape 3 : Créer un menu principal](#étape-3--créer-un-menu-principal)  
    - 3.1. Enregistrer le menu dans `functions.php`  
    - 3.2. Gérer le menu dans l’admin  
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

## Étape 5 : Créer la page Post (article individuel)

### 5.1. Créer le fichier `single.php`

Ce fichier est utilisé pour afficher un article en détail. Créez un fichier `single.php` et ajoutez-y le code suivant :

```php
<?php
get_header();
?>

<div class="container">
    <?php
    if (have_posts()) :
        while (have_posts()) : the_post(); ?>
            <article>
                <h1><?php the_title(); ?></h1>
                <div>
                    <?php the_content(); ?>
                </div>
                <p><strong>Publié le :</strong> <?php echo get_the_date(); ?></p>
                <a href="<?php echo get_permalink(get_option('page_for_posts')); ?>">&larr; Retour au Blog</a>
            </article>
        <?php endwhile;
    else :
        echo '<p>Aucun contenu trouvé.</p>';
    endif;
    ?>
</div>

<?php
get_footer();
```

### Explications du code

1. **`the_title()`** : Affiche le titre de l’article.
2. **`the_content()`** : Affiche le contenu complet de l’article.
3. **`get_the_date()`** : Récupère et affiche la date de publication de l’article.
4. **Lien retour** : Permet de revenir à la page Blog en utilisant l’option `page_for_posts` configurée dans WordPress.

---

### 5.2. Tester l’affichage des articles

1. Dans le tableau de bord WordPress, allez dans **Articles > Ajouter**.
2. Créez un ou deux articles avec un titre, du contenu, et une image mise en avant (optionnelle).
3. Visitez votre page **Blog** et cliquez sur un article pour vérifier son affichage.

Vous devriez voir le contenu de `single.php` s’afficher avec le titre, le texte complet, et la date de publication de l’article.

---

## Conclusion

À ce stade, vous avez un site WordPress fonctionnel avec :

- Une **Home Page** (gérée par `front-page.php`).
- Une **page About** avec un template dédié ou non (`page-about.php`).
- Un **menu principal** géré via l’admin et enregistré dans `functions.php`.
- Une **page Blog** listant les articles (gérée par `home.php`).
- Des **articles individuels** avec leur page (gérée par `single.php`).

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
