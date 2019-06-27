# Snipety šablón

Snipety šablóny slúžia pre pridávanie vlastných komponentov do existujúceho rozhrania v administrácii.

- [Vytvorenie prvej šablóny](#Vytvorenie-prvej-šablóny)
- [Nastavenie konfigurácie šablóny](#Nastavenie-konfigurácie-šablóny)
- [Registrácia šablóny](#Registrácia-šablóny)

<hr>

## Vytvorenie prvej šablóny

Šablóna pozostáva z dvoch súborov, ako prvý je konfiguračny súbor PHP, a druhý je šablóna komponenty, ktorá je priradena ku konfiguračnému súboru. Tieto súbory je možné vytvoriť pomocou `artisan` príkazu.

```
php artisan admin:layout MyCustomLayout
```

!> Po spustení príkazu mame na výber z dvoch druhov komponent, prvá je **VueJS** a druhá je **Blade**.

!> V prípade výberu **VueJS** bude komponenta s názvom `MyCustomLayout.vue` vytvorená v priečinku `resources/views/admin/components/layouts`. Pri zvolení **Blade** komponenty, bude vytvorený súbor `testLayout.blade.php` v priečinku `resources/views/admin`.

<hr>

## Nastavenie konfigurácie šablóny

Ako prvý súbor, z ktorého sa sklada šablóna, je PHP trieda, v ktoréj su zadefinované nastavenia danej komponenty. Všetky nastavenia sú znázornene nižšie.

```php
class MyExampleLayout extends Layout
{
    public $position = 'form-top';

    /*
     * On build blade layour
     */
    public function build()
    {
        return view('admin.MyExampleLayout');
    }
}
```


#### Pozícia snippetu
Pozíciu nastavujeme podľa parametru `$position`.

```php
public $position = 'form-top';
```

Na výber mame z niekoľkých pozícii, kde chceme vygenerovanú komponentu umiestniť.

`top` - pred panel s rozšírením<br>
`bottom` - za panel s rozšírením<br>
`form-top` - horná časť formuláru<br>
`form-bottom` - spodná časť formuláru<br>
`form-header` - hlavička formuláru<br>
`form-footer` - pätička formuláru<br>
`table-header` - hlavička so záznamami<br>
`table-footer` - pätička so záznamami<br>

#### Dosadenie komponenty

##### V prípade blade
```php
public function build()
{
    $articles = Article::get();

    return view('admin.MyTestLayout', compact('articles'));
}
```

##### V prípade VueJS
```php
public function build()
{
    return $this->component('MyTestLayout.vue');
}
```

!> VueJs komponentu môžeme vytvoriť aj osobitne bez konfiguračného PHP súboru, pomocou príkazu `php artisan admin:component MyTestLayout`. Na otázku typu komponenty zvolíme odpoveď `layout`.

!> Všetky komponenty sa rekurzívne automatický načitávaju z priečinka `resources/views/admin/components`. Tento priečinok je možné nastaviť v [konfigurácii administrácie](config.md#_7-priečinok-načitávania-vuejs-komponent).

<hr>

## Registrácia šablóny

Po vytvorení šablóny, je potrebné priradiť konfiguračny PHP súbor k Admin Modelu pomocou parametru `$layouts`.

```php
class Article extends AdminModel
{
    ...

    protected $layouts = [
        \App\Admin\Layouts\MyExampleLayout::class,
    ];
}
```

V prípade VueJS komponenty nie je potrebné vytvárať konfiguračný PHP súbor. VueJS komponentu môžeme zaregistrovať napriamo, pričom kľuč v poli bude reprezentovaný pozíciou umiestnenia danej komponenty.

```php
class Article extends AdminModel
{
    ...

    protected $layouts = [
        'form-top' => 'MyTopLayout.vue'
        'form-bottom' => 'MyBottomLayout.vue'
    ];
}
```

!> V tomto prípade vytvorime samostatnú VueJS komponentu pomocou príkazu `php artisan admin:component MyTestLayout`. Na otázku typu komponenty zvolíme odpoveď `layout`.

## VueJS Komponenta

Pomocou `props` atribútu v komponente viete obdržať všetky potrebné informácie o upravovanom zázname, novo vytvorenóm zázname a ďalšie informácie s ktorými môžete ďalej dynamicky pracovať.

```html
<template>
    <div>
        <h2 v-if="!row.id">Please open any row.</h2>
        <h2 v-else>You are editing row number {{ row.id }}</h2>
    </div>
</template>

<script type="text/javascript">
export default {
    props : ['model', 'row', 'rows'],

    mounted(){
        console.log('Your own layout is mounted!!', this.key, this.row, this.field);
    },
}
</script>
```