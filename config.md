# Konfigurácia
Po úspešnej inštalácii sa vytvorí konfiguračný súbor [config/admin.php](https://github.com/MarekGogol/crudadmin/blob/master/src/Config/config.php) v ktorom sú definované základne globálne nastavenia administrácie. V tomto konfiguračnom súbore je možné doplniť dodatočné rozšírené nastavenia, čím je možné škálovať funkcionalitu rozšírenia.

---

## Základné nastavenia

##### 1. Názov administrácie
```php
'name' => 'My Admin'
```

##### 2. Skupina rozšírení
V administráci pri vytvárani modulov je niekedy potrebujete zoskúpiť viacero rozšíreni do jednej skupiny.
![menu_groups](images/menu_groups.png)

```php
'groups' => [
    'settings' => 'Nastavenia', #1 skupina bez ikony
    'school' => ['Škola', 'fa-car'], #2 skupina s ikonou
],
```
!> Ako nastaviť priradenie Admin modelu do skupiny je znázornené [v tejto dokumentácii](#)

## Jazykové mutácie

##### 1. Aktivácia jazykových mutácii
```php
'localization' => true,
```

##### 2. Deaktívacia núteného presmerovania pri predvolenom jazyku
Ak sa Vaša webová aplikácia delí podľa viac jazyčných mutácii, ktoré su definované v url adrese. Je možné vypnúť nútené presmerovanie na predvolený jazyk. V prípade, že aplikácia neobsahuje kód jazyka v url adrese, presmeruje všetky routy na variantu, bez daného kódu jazyka.
```php
'localization_remove_default' => true,
```

##### 3. Podpora PHP rozšírenia Gettext
Rozšírenie Gettext v spolupráci s rozšírením CrudAdmin automaticky skenuje všetky statické texty v aplikácii, a následne ponúka preklad textov priamo v administrácii, či k dispozícii pre prekladateľské spoločností v programe [PoEdit](https://poedit.net/)
```php
'gettext' => true,
```

!> Kompletné nastavenia s vysvetlením jazykových mutácii nájdete v sekcii [Jazykové mutácie](languages#Jazykové-mutácie)

!> CrudAdmin posunul gettext rozšírenie o krok ďalej s podporou čítania zdrojových textov aj z javascriptových súborov! Čítaj viac v sekcii o [využití gettext prekladov](languages#_2-zápis-prekladov-v-aplikácii).

## Rozšírené nastavenia
K základným nastaveniam administrácie, rozšírenie CrudAdmin poskytuje ďalšie množstvo volitelných parametrov, ktoré je možné v konfiguračnom súbore `config/admin.php` prepísať. Tieto nastavenia môžu služit pre lepšie škálovanie projektu.

> Doplnkový administračný súbor https://github.com/MarekGogol/crudadmin/blob/master/src/Config/config_additional.php

##### 1. Gettext mapovanie súborov
Rozšírenie Gettext dokáže čítať zo zdrojových súborov texty a následne ich prekládať. Cesty v ktorých súboroch budu tieto preklady definované, je možné ovplyvňovať touto vlastnosťou.
```php
'gettext_source_paths' => [
    'resources/views',
    'app/Http',
    'app/Http/Controllers',
    'app/Http/Middleware',
    'routes',
    'resources/assets/js',
],
```