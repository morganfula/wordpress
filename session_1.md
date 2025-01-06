# Session 1 : Installation de WordPress et introduction à l’écosystème

## Objectifs de la session
- Comprendre l’écosystème WordPress et son importance.
- Installer WordPress en local sur **Mac** ou **PC**.
- Explorer l’interface administrateur de WordPress.

---

## Partie 1 : Présentation et démonstration (30-45 minutes)

### 1. Introduction à WordPress
#### Qu’est-ce que WordPress ?
- **WordPress** est un CMS (Content Management System) qui permet de créer des sites web sans coder.
- Plus de **43% des sites web mondiaux** utilisent WordPress.
- Caractéristiques principales :
  - Open-source.
  - Flexible grâce aux **plugins** et **thèmes**.
  - Accessible aux débutants.

#### Pourquoi choisir WordPress ?
- Facile à utiliser et personnaliser.
- Adapté pour des projets variés : blogs, boutiques en ligne, portfolios.
- Large communauté et support abondant.

---

### 2. Préparer l’installation locale

#### Prérequis
- Un environnement de serveur local :
  - **PC** : [XAMPP](https://www.apachefriends.org/index.html)
  - **Mac** : [MAMP](https://www.mamp.info/)
- Télécharger WordPress depuis : [wordpress.org/download](https://wordpress.org/download).

---

#### Étapes d'installation

**Étape 1 : Installer un serveur local**

**Sur PC (XAMPP) :**
1. Téléchargez **XAMPP** sur [apachefriends.org](https://www.apachefriends.org/).
2. Installez XAMPP et ouvrez le panneau de contrôle.
3. Activez les services **Apache** et **MySQL**.

**Sur Mac (MAMP) :**
1. Téléchargez **MAMP** sur [mamp.info](https://www.mamp.info/).
2. Installez MAMP et ouvrez l’application.
3. Cliquez sur **Start Servers** pour activer **Apache** et **MySQL**.

---

**Étape 2 : Télécharger WordPress**
1. Rendez-vous sur [wordpress.org/download](https://wordpress.org/download).
2. Téléchargez et décompressez l’archive WordPress.
3. Déplacez le dossier WordPress dans :
   - **PC (XAMPP)** : `C:/xampp/htdocs`.
   - **Mac (MAMP)** : `/Applications/MAMP/htdocs`.

---

**Étape 3 : Créer une base de données**
1. Accédez à **phpMyAdmin** :
   - **PC (XAMPP)** : [http://localhost/phpmyadmin](http://localhost/phpmyadmin).
   - **Mac (MAMP)** : [http://localhost:8888/phpmyadmin](http://localhost:8888/phpmyadmin).
2. Cliquez sur **Nouvelle base de données**.
3. Nommez la base de données `wordpress` et cliquez sur **Créer**.

---

**Étape 4 : Configurer WordPress**
1. Accédez à votre site local :
   - **PC (XAMPP)** : [http://localhost/nom_du_dossier_wordpress](http://localhost/nom_du_dossier_wordpress).
   - **Mac (MAMP)** : [http://localhost:8888/nom_du_dossier_wordpress](http://localhost:8888/nom_du_dossier_wordpress).
2. Suivez l’assistant de configuration :
   - **Nom de la base de données** : `wordpress`.
   - **Nom d’utilisateur** :
     - `root` sur **PC (XAMPP)**.
     - `root` sur **Mac (MAMP)**.
   - **Mot de passe** :
     - *(vide)* sur **PC (XAMPP)**.
     - `root` sur **Mac (MAMP)**.
3. Complétez les informations du site : nom, identifiant admin, mot de passe, etc.

---

### 3. Exploration du tableau de bord WordPress
1. **Tableau de bord** : Vue d’ensemble du site.
2. **Articles** : Créez et gérez des blogs.
3. **Pages** : Créez des pages statiques (exemple : "À propos").
4. **Apparence** : Modifiez les thèmes et widgets.
5. **Extensions** : Ajoutez des fonctionnalités.

---

## Partie 2 : Pratique autonome (2h30)

### Exercices pratiques

#### Exercice 1 : Installer WordPress en local
- Suivez les étapes d’installation pour configurer votre propre site WordPress.
- Prenez une capture d’écran une fois l’installation terminée et le tableau de bord accessible.

#### Exercice 2 : Créer une page "Bienvenue"
1. Accédez à **Pages** > **Ajouter une nouvelle**.
2. Créez une page intitulée **Bienvenue** avec un message d’accueil.
3. Publiez la page et prévisualisez-la.
4. Prenez une capture d’écran de la page.

#### Exercice 3 : Explorer le tableau de bord
1. Identifiez les différents menus et fonctionnalités du tableau de bord.
2. Notez deux questions ou observations sur les menus ou options.

---

## Ressources supplémentaires
- **Documentation officielle WordPress** : [https://wordpress.org/support/](https://wordpress.org/support/)
- **Tutoriels vidéo** : [Installation locale WordPress (MAC)](https://www.youtube.com/watch?v=_oB9ltryMXI&t)
- **Tutoriels vidéo** : [Installation locale WordPress (PC)](https://www.youtube.com/watch?v=um8BtHFNJBA&t)
- **Guide XAMPP** : [https://www.apachefriends.org/index.html](https://www.apachefriends.org/index.html)
- **Guide MAMP** : [https://www.mamp.info/en/documentation/](https://www.mamp.info/en/documentation/)

---

## Bonus (Pour aller plus loin)
- Explorez les réglages disponibles dans **Réglages > Général**.
- Essayez de changer le thème par défaut dans **Apparence > Thèmes**.
- Testez la création d’un premier article dans **Articles > Ajouter**.

---

