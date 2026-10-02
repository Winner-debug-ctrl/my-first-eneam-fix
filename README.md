# Rapport de Bug - Site ENEAM

**Site concerné:** https://eneam.uac.bj/club/alumni-%C3%A9tudiant
**Date:** 2 Octobre 2026 - 10h00
**Par:** Winner-debug-ctrl - Abomey-Calavi
**Lien GitHub:** https://github.com/Winner-debug-ctrl/my-first-eneam-fix

### 1. Le problème
Quand on clique sur "Alumni - Étudiant" dans le menu, le site affiche une page blanche avec erreur 500.

Message d'erreur:
> View [frontend.menu2.almni.index] not found

### 2. Pourquoi ça arrive ?
C'est une simple faute de frappe dans le code.

Dans le fichier `app/Http/Controllers/Front/AlumniController.php` à la ligne 11, il est écrit:
```php
return view('frontend.menu2.almni.index');
// Corriger la faute
return view('frontend.menu2.alumni.index');

->Version Anglaise du rapport de bug:
# my-first-eneam-fix

# ENEAM Bug Report - 500 View Not Found

**Date:** 02 Oct 2026 - 07:32 AM (Abomey-Calavi, Benin)
**URL:** https://eneam.uac.bj/club/alumni-%C3%A9tudiant
**Reporter:** Winner-debug-ctrl

## 1. Error Found

Root cause: Typo `almni` instead of `alumni`. The blade file does not exist in `resources/views/frontend/menu2/`.

## 2. Second Issue - Performance
80+ identical SQL queries on one page load:
```sql
select * from `classes` where `classes`.`deleted_at` is null order by `nom` asc
// AlumniController.php
public function index() {
    return view('frontend.menu2.alumni.index'); // fixed typo
}

# my-first-eneam-fix - ENEAM Bug Hunt

Real bug found on eneam.uac.bj on Oct 2 2026.

## Bug
- 500 Error on /club/alumni-étudiant
- View [frontend.menu2.almni.index] not found -> typo almni
- File: AlumniController.php:11

## What I learned
- Laravel MVC
- N+1 query problem
- APP_DEBUG should be false in production

By Winner-debug-ctrl - Future ENEAM IT student

