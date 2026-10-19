# PolyJob — Portail d'offres d'emploi

**PolyJob** est une application web de type job portal développée avec **Symfony 7** et **Twig**. Elle met en relation candidats et recruteurs à travers une interface moderne (Bootstrap 5), un carrousel d'accroche, une barre de recherche et des pages institutionnelles en français.

> Projet réalisé dans le cadre du TP *Application Twig avancée* — intégration d'un template HTML/CSS/JS avec **AssetMapper** (modes développement et production).

![Page À propos — PolyJob](docs/screenshots/about.png)

## Fonctionnalités

- **Page d'accueil** (`/accueil`) : carrousel Owl Carousel, recherche par mot-clé / catégorie / localisation, exploration par catégories métiers
- **À propos** (`/about`) : présentation de la plateforme, visuels et appels à l'action
- **Contact** (`/contact`) : coordonnées, carte Google Maps, formulaire de message
- **Template maître** : navigation active selon la route, titres d'onglet dynamiques, fil d'Ariane sur les pages secondaires
- **Composants Twig réutilisables** : `carousel`, `search`

## Stack technique

| Composant | Version / outil |
|-----------|-----------------|
| PHP | ≥ 8.2 |
| Symfony | 7.0 |
| Moteur de vues | Twig |
| Assets | Symfony AssetMapper (`asset()`) |
| Front | Bootstrap 5, jQuery, WOW.js, Owl Carousel |
| Base de données | Doctrine ORM (projet Symfony standard) |

## Prérequis

- PHP 8.2+
- [Composer](https://getcomposer.org/)
- Extensions PHP : `ctype`, `iconv`

## Installation

```bash
git clone https://github.com/karimgh2023/job-portal.git
cd job-portal
composer install
```

Copiez les images du thème dans `assets/images/` (ex. `carousel-1.jpg`, `carousel-2.jpg`, `about-1.jpg` … `about-4.jpg`).

## Lancer en développement

```bash
# Serveur PHP intégré Symfony
symfony server:start

# ou
php -S localhost:8000 -t public public/index.php
```

Ouvrir :

- http://localhost:8000/accueil
- http://localhost:8000/about
- http://localhost:8000/contact

## Commandes utiles

```bash
# Vérifier les routes
php bin/console debug:router

# Valider les templates Twig
php bin/console lint:twig templates

# Cartographie des assets
php bin/console debug:asset-map

# Compilation des assets (production)
php bin/console asset-map:compile
```

## Structure du projet

```
assets/
  images/          # Images du thème (carrousel, about, …)
  js/              # main.js + bibliothèques (owl, wow, …)
  styles/          # bootstrap.min.css, style.css
src/Controller/
  HomeController.php
templates/
  template_job.html.twig    # Gabarit maître (blocs title, titre_page, search, body, …)
  components/               # carousel.html.twig, search.html.twig
  home/                     # accueil, about, contact
public/
  index.php
```

## Routes

| URL | Nom de route | Vue |
|-----|--------------|-----|
| `/accueil` | `app_accueil` | `home/accueil.html.twig` |
| `/about` | `app_about` | `home/about.html.twig` |
| `/contact` | `app_contact` | `home/contact.html.twig` |

## Auteur

**Karim GH** — [@karimgh2023](https://github.com/karimgh2023)

## Licence

Projet académique — usage pédagogique.
