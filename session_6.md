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
1. Accédez au répertoire `wp-content/themes/`.
2. Créez un nouveau dossier pour votre thème (exemple : `mon-theme-personnalise`).

---

### Étape 2 : Ajouter le fichier `style.css`
1. Créez un fichier `style.css` dans le dossier du thème.
2. Ajoutez les informations suivantes :
   ```css
   /*
   Theme Name: Mon Thème Personnalisé
   Author: Votre Nom
   Description: Un thème WordPress développé de zéro.
   Version: 1.0
   */

---

### Étape 3 : Ajouter le fichier index.php


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
