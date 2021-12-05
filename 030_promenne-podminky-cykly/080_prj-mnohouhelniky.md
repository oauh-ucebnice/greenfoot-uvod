# Vyzkoušej si – projekt Mnohoúhelníky

## Co si procvičíš?
 - podmíněné příkazy
 - cykly
 - práci s&nbsp;proměnnými

## Zadání
 - Vytvoř projekt, kde bude na obrazovce rozmístěn stanovený počet aktérů. Počet aktérů bude uložen v&nbsp;atributu světa. Na začátek použij jako počet aktérů hodnotu 8.
 - Aktéři budou rozmístěni vodorovně uprostřed obrazovky a&nbsp;budou mezi nimi rovnoměrné rozestupy.
- Každý aktér se vždy posunuje 10 kol hry vpřed o 20&nbsp;pixelů. Na konci 10 kola hry se otočí o&nbsp;120&nbsp;° vlevo. Aktéři tedy budou obíhat rovnoramenný trojúhelník.
- Úhel otočení ulož do atributu aktéra a&nbsp;vytvoř přístupovou metodu &nbsp;_set otočení_ tak, aby bylo možné měnit úhel otočení.

> ## Poznámka:
>
> Veškeré názvy záměrně píšeme malými písmeny s&nbsp;mezerami a&nbsp;diakritikou. Do kódu je piš v&nbsp;souladu s&nbsp;konvencemi Javy!

 
<details><summary>První nápověda: Postup rozmisťování aktérů</summary>

 - Vytvoř si proměnnou _x_, do které uložíš souřadnici X dalšího aktéra (na začátku bude její hodnota `50`).
 - Vytvoři si druhou proměnnou _odstup_, která bude udávat rozestup mezi jednotlivými aktéry. Hodnotu spočítáš tak, že od šířky obrazovky odečteš 2× 50 pixelů na okraje a&nbsp;výsledek vydělíš počtem aktérů mínus 1. Například pro 4&nbsp;aktéry to bude na obrazovce vypadat takto (znak `*` představuje aktéra):<br />
  _okraj obrazovky_| 50 px `*` odstup `*` odstup `*` odstup `*` 50 px |_okraj obrazovky_
 - Po vytvoření nového aktéra zvyš hodnotu proměnné _x_ o&nbsp;hodnotu proměnné _odstup_ a&nbsp;můžeš vytvářet dalšího aktéra.

</details>
 
<details><summary>Druhá nápověda: Pohyb aktéra</summary>

 - V&nbsp;aktérovi si vytvoř proměnnou _počet kroků_ a nastav ji na `0`.
 - Při každém volání metody `act` posuň aktéra a&nbsp;zvyš hodnotu _počet kroků_ o&nbsp;`1`.
 - Jakmile bude hodnota _počet kroků_ větší nebo rovna 10, proveď otočení aktéra a&nbsp;nastave _počet kroků_ opět na `0`.

</details>

---

## Rozšíření 1: Rozmísti aktéry na úhlopříčku obrazovky

Aktéři tedy nebudou vodorovně uprostřed obrazovky, ale první bude v&nbsp;levém horním rohu a poslední v&nbsp;pravém dolním rohu obrazovky.

<details><summary>Nápověda k rozšíření 1: Postup</summary>

 - Podle počtu aktérů spočti jejich rozestup na ose X a&nbsp;na ose Y. 
 - Vytvoř si proměnné `x` a&nbsp;`y` pro uložení polohy dalšího aktéra &mdash; na začátku budou mít souřadnice `0`, `0`.
 - Po umístění každého aktéra na obrazovku zvyš hodnotu proměnných `x` a `y` o&nbsp;spočtený rozestup.

</details>

---

## Výzva: Aktéři opisující různé mnohoúhelníky

První tři aktéři budou obíhat rovnostranný trojúhelník. Další tři budou obíhat čtverec. Další tři budou obíhat rovnostranný pětiúhelník. Pokud budou další, budou následovat šestiúhelníky, sedmiúhelníky atd.
