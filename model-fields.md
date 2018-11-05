# Zoznam vstupných hodnôt
Základna konfigurácia Admin Modelu pozostáva zo vstupných hodnôt, ktoré reprezentujú informácie o všetkých stĺpcoch v databáze,
pravidla validácie formulárov, reláciach a nastavení gerenovania administračného rozhrania od formulárov, až po tabuľky výpisu.

- [Zoznam dostupných vstupov](#Zoznam-dostupných-vstupov)
- [Syntax vstupných hodnôt](#Syntax-vstupných-hodnôt)

!> Databáza je automatický synchronizovaná pri každej úprave vstupných hodnôt pomocou automatických migrácii

## Zoznam dostupných vstupov

<!-- -->
> #### (fa-font) TEXTOVÝ INPUT
> Textové pole reprezentované klasickým input vstupom.

<!-- -->
> #### (fa-text-width) Dlhší text
> Textové pole reprezentované textarea vstupom.

<!-- -->
> #### (fa-file-word-o) Textový editor
> Vstup vo formáte [CKEditoru]() pre jednoduché formátovanie textu.

<!-- -->
> #### (fa-sort-numeric-desc) Celé číslo
> Vstup vo formáte celého čísla.

<!-- -->
> #### (fa-sort-numeric-desc) Desatinné číslo
> Vstup vo formáte desatinného čísla.

<!-- -->
> #### (fa-circle-o) Radio
> Vstup vo formáte viacerých možnosti na výber typu radio input.

<!-- -->
> #### (fa-check-square-o) Checkbox
> Vstup vo formáte aktívnej alebo neaktívnej hodnoty.

<!-- -->
> #### (fa-key) Password
> Vstup vo formáte skytej hodnoty typu hesla.

<!-- -->
> #### (fa-list-ol) Select
> Výber jednej hodnoty zo zoznamu viacerých možností.

<!-- -->
> #### (fa-database) DB Select
> Podpora načítania hodnôt do selectu alebo multiselectu z existujúcich záznamov v ľubovoľenj tabuľke v databáze.

<!-- -->
> #### (fa-upload) Upload súborov
> Možnost pridania vstupu vo forme nahrávania súboru, či obrazkú s automatických orezávaním.

<!-- -->
> #### (fa-calendar) Dátum
> Podpora formátovaného vstupu vo forme dátumu, prípadne aj času zároveň.

<!-- -->
> #### (fa-clock-o) Čas
> Formatovaný vyber času.

## Syntax vstupných hodnôt
Skladá sa z viac rozmerného poľa v ktorom jeho kľúče označujú názov stĺpca v databáze a hodnota reprezentuje
konfiguráciu vstupného parametru v spojení s pravidlami [Laravel validácie](https://laravel.com/docs/5.5/validation#rule-unique). Konfigurácia môže mať 2 podoby. Jedná z ních je vo formáte poľa,
druhá vo forme reťazcu parametrov oddelených znakom |. Nižšie sú znázornene tieto 2 príklady.
Prve 2 položky name a content označujú vstupné hodnoty pre
názov a obsah. Tretí parameter image je vstup pre nahranie obrázku.

##### Zápis v podobe stringu
```php
protected $fields = [
    'name' => 'name:Názov|placeholder:Zadajte názov článku|type:string|required|max:90',
    'content' => 'name:Obsah článku|type:editor|required',
    'image' => 'name:Obrázok|type:file|image|required',
];
```

##### Rovnaký zápis v podobe poľa
```php
protected $fields = [
    'name' => [
        'name' => 'Názov',
        'placeholder' => 'Zadajte názov článku',
        'type' => 'string',
        'required' => 'true',
        'max' => 90,
    ],
    'content' => [
        'name' => 'Obsah článku',
        'type' => 'editor',
        'required' => 'true',
    ],
    'image' => [
        'name' => 'Obrazok',
        'type' => 'file',
        'required' => true,
        'image' => true,
    ]
];
```

##### Komplexný zápis vstupných hodnôt vo forme metódy

V niektorých prípadoch je potrebné validáciu rozlíšiť pri vytvárani nového záznamu a úprave už existujúceho,
v tomto prípade parameter `$row` bude pri editácii obsahovať editovaný záznam z databázy.

```php
use Illuminate\Validation\Rule;

public function fields($row)
{
    return [
        'username' => 'name:Meno a priezvisko|required|max:30',
        'email' => 'name:Email|email|required|unique:users,email,'.( isset($row) ? $row->getKey() : 'NULL' ),
        'password' => 'name:Heslo|type:password|confirmed|min:4|'.( ! isset($row) ? 'required' : '' ),

        'other_field' => [
            'name' => 'Vstupná hodnota X Y',
            'required' => isset($row) ? false : true,
            Rule::unique('users')->ignore( isset($row) ? $row->id : null ),
        ],
    ]
}
```

#### Vstupné hodnoty pre select
Pre manuálne definovanie kľúčov a ich hodnôt pre vstup z poľa typu [select]() je možné použiť parameter `$options`

**Pre statické vstupné hodnoty:**
```php
protected $options = [
     'countries' => [
          'sk' => 'Slovakia',
          'cs' => 'Czech republic',
          ...
     ]
];

**Pre dynamický generované vstupné hodnoty:**
```php
public function options()
{
     return [
         'countries' => App\Country::pluck('country', 'code')->toArray()
     ];
}
```

---