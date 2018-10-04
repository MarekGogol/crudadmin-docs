# Konfigurácia
Po úspešnej inštalácii sa vytvorí konfiguračný súbor `/config/admin.php` v ktorom sú definované globálne nastavenia administrácie.

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
    'settings' => 'Nastavenia',
    'school' => 'Škola'
],
```

## Jazykové mutácie

##### 1. Aktivácia jazykových mutácii
```php
'localization' => true,
```

##### 2. Deaktívacia núteného presmerovania pri predvolenom jazyku
```php
'localization_remove_default' => true,
```

##### 3. Podpora PHP rozšírenia Gettext
```php
'gettext' => true,
```

!> Kompletné nastavenia s vysvetlením jazykových mutácii nájdete v [tejto dokumentácii](languages#Jazykové-mutácie)