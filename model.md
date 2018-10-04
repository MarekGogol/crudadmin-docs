# Prvé kroky
V tejto sekcii je vysvetlené z čoho **Admin Model** pozostáva a ako s ním môžme ďalej pracovať.

- [Čo je to Admin Model](#Čo-je-to-Admin-Model)
- [Výhody Admin Modela](#Výhody-Admin-Modela)
- [Vytvorenie Admin Modela](#Vytvorenie-prvého-admin-modela)


---

## Čo je to Admin Model
Admin Model je klasický Laravel [Eloquent Model](https://laravel.com/docs/master/eloquent) z architektúry MVC. Rozdiel medzi klasickým modelom je ten, že
Admin Model obsahuje parametre a základné nastavenia, pomocou ktorých systém CrudAdmin dokáže vygenerovať celú
databázu, formuláre, validáciu a urychliť proces vývoja aplikácie.

!> Podrobne fungovanie Admin Modela ste si mohli prečítať v sekcii [Ako to funguje](how-it-works.md)

---

## Výhody Admin Modela
> 1. Automaticky vypĺnia `$fillable` a `$casts` podľa zadefinovaných vstupných hodnôt
> 2. Automaticky mapuje všetky relácie medzi modelmi. Čiže zaniká potreba písania metód v modeloch, ktoré definuju vzťahy medzi modelmi.
     Od teraz stačí zavolať metódu s názvom modela, a relácia bude automatický nabindovaná. Napríklad `$article->gallery()` alebo `$article->gallery`.
> 3. Celá databáza a používateľske rozhranie pre administrátora bude vygenerované podľa nastavení Admin Modela.

---

## Vytvorenie prvého Admin Modela
Admin model je možné vytvoriť podobne ako klasický model v laraveli a to pomocou príkazu **php artisan**.

```bash
php artisan admin:model Article
```

Po spustení príkazu sa v priečinku `app` vytvorí súbor s názvom `Article.php`