# Čo je to CrudAdmin

CrudAdmin je systém navrhnutý pre programátorov a firmy zamerané na vývoj
webových a mobilných databázových aplikácii. V jednoduchosti **niekoľko násobne
zvyšuje produktivitu** programátora tým, že **odbremeňuje** všetky zložité kroky ako
**návrh databázy, použivateľského rozhrania, validácie formulárov** a prácu s
dátmi v databáze.

---

## Čo všetko podporuje?

Kedže ide o systém postavený na frameworku **Laravel 5**, ponúka jednoduchú a
ucelenú štruktúru pri programovaní. Laravel model dostal nadstavbu a
nazývame ho **Admin model**. Po jednoduchom vytvorení admin modelu systém
automatický navrhné všetky tieto následne vypísane kroky.

<!-- -->
> #### (fa-window-maximize) NÁVRH UI / UX
> Automatický vytvorí prehľadné používateľské rozhranie pre jednoduchú správu systému koncovým používateľom

<!-- -->
> #### (fa-user-circle-o) Autentifikácia
> Automatický navrhne rozhranie pre prihlásovanie, správu používateľov, použivateľských ról

<!-- -->
> #### (fa-users) Právomoci
> Podporuje možnosť vytvorenia používateľských skupín pre správu právomoci administrátorov, každá rola môže mať presne zadefinované práva pre dane moduly.

<!-- -->
> #### (fa-database) Návrh databázy
> Automatický navrhne relačnú databázu bez akejkoľvek znalosti databázoveho jazyka. Taktiež sa postará o jej následnu úpravu pri vývoji projektu alebo migrovaní na novu verziu.

<!-- -->
> #### (fa-wpforms) Formuláre
> Automaticky navrhne všetky formuláre v administrácii, prepoji ich s databázou, postará sa o kompletnú validáciu položiek vo formulári a následne uloženie a prácu so záznamom v databáze.

<!-- -->
> #### (fa-exclamation) Validácia
> Postará sa o validáciu všetkych položiek vo formulári na strane backendu bez akých koľvek osobitných nastavovani zo strany programátora. Taktiež sa postará o validáciu na strane frontendu.

<!-- -->
> #### (fa-file-image-o) Upload súborov
> Automaticky uloží a postará sa o všetky súbory, obrazky ktoré sa nachádzaju vo formulári. Taktiež sa postará o ich následne zmenšenie na požadované veľkosti.

<!-- -->
> #### (fa-language) Jazykové mutácie
> Automatický vytvori jazykovú tabuľku, prepoji dane modeli s danými jazykmi a postará sa o automatické prepinanie jazykov ako na stránke administrácie, tak i na strane frontendu. V spolupráci s Gettext rozšírením, je možné spravovať preklady statických textov ako v zdrojových šablonách aplikácie, no taktiež aj v javascriptoch.

<!-- -->
> #### (fa-table) Výpis dát
> Automatický navrhne všetky tabuľky pre inteligentný a prehliadny výpis dát v administrácii. Postará sa o možnosť pridania záznamov, úpravy, mazania, skývania záznamov a zmeny ich poradia.

<!-- -->
> #### (fa-pencil-square-o) Vstupné polia
> Podporuje veľke množstvo vstupných hodnôt od obyčajného textu, textarei, čísla, des. čísla, textového editoru, dátumu, času, selectboxu, checkboxu až po automatické uploadovanie súborov. Pre tých zdatnejších, alebo pre projekty s veľkym dôrazom pre unikátnosť, system podporuje aj možnosť vytvorenia vlastných kustomizovateľných komponent.

<!-- -->
> #### (fa-key) Relácie
> Automatický sa postará o vygenerovanie všetkych relácii v databáze a prepojenie naviazaných formulárov. Taktiež odstránil nutnosť písania vzťahov medzi Eloquentmi. Tieto vzťahy medzi modelmi sú od teraz prepojené automaticky. Podporuje belongsTo, belongsToMany, hasMany, hasOne, manyToMany...

<!-- -->
> #### (fa-terminal) Jednoduchá inštalácia
> Systém ponuká jednoduchu inštaláciu a vytvaranie admin modelov pomocou príkazu `php artisan`

## História CrudAdminu

Rozšírenie uzrelo svetlo sveta začiatkom roku **2016**. Vzniklo pri tvorbe komplexného a zložitého projektu, za účelom urýchlenia developmentu tohto projektu.

Už v zárodku tvorby tohto projektu bol potencial systému natoľko vysoký, že sa jadro systému začalo vyvíjať ako oddelený projekt, ktorý  sa postupne začal používať vo viacerých projektoch.

## Kto používa CrudAdmin

Po niekoľkých rokoch vývoja systému, ho používa cez **stovky webových aplikácii, eshopov, informačných systémov, či mobilných aplikácii** pripajajúcich sa na API systému, ktorý obsluhuje dáta tychto aplikácii.

Nachádza sa taktiež v niekoľkých **Slovenských** a **Českých firmách**, jeho rast je do budúcnosti plánovaný pre globalný trh.

## CrudAdmin a testovanie

CrudAdmin plné obsahuje automatizované **unit** a **integračné testy**, ktoré sa starajú a kontroluju väčšinu funkcionalit v systéme.

Pred každým zverejnením novej verzie systému podliehaju jeho súčasti kontrole funkcionality na viacerých testovacích projektoch. Kontrola taktiež prebieha pomocou integračných testov, ktoré automatický spustia aplikáciu a otestuju jej správne chovanie v prehliadači.

!> Všetky nové verzie systému su spätne kompatibilné.