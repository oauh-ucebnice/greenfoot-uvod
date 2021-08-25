# Proměnné a datové typy

Proměnnou si můžeme představit jako „krabičku“, do které ukládáme nějakou hodnotu či objekt.

Pokud je proměnná součástí popisu třídy, říkáme jí „atribut“.

## Datový typ

Stejně jako do krabice od bot nemůžeme dát automobil a propisku uložíme raději do pouzdra než do turistického batohu, je i proměnná vhodná jen pro uložení určitých objektů. Při vytváření proměnné tedy musíme říci, jaké objekty chceme do proměnné ukládat. Tomu se říká datový typ proměnné. Nejběžnější datové typy si uvedeme za chvíli.

Samozřejmě musíme do proměnné opravdu ukládat jen data správných datových typů. Pokud bychom do proměnné chtěli uložit nesprávná data, počítač by akci neprovedl a vypsal by chybu.

## Běžné datové typy 

V začátcích se potkáme s následujícími datovými typy:
 - Celé číslo (záporná i kladná čísla, ale ne desetinná čísla či zlomky):
`int`
 - Text
`String`
 - Desetinné číslo
`double`
 - Logická hodnota (ano/ne – `true`/`false`)
    - `boolean`

Zatím jsme si uvedli jen několik základních datových typů. Ve skutečnosti jich je v programovacích jazycích obvykle víc. 

## Vytvoření proměnné

Při vytváření proměnné píšeme vždy nejprve datový typ a poté název proměnné. Název si můžeme vymyslet. Měl by ale začínat malým písmenem, nesmí obsahovat mezery a jiné speciální znaky kromě písmen, číslic a podtržítek. Každé nové slovo názvu by mělo začínat velkým písmenem. (Aspoň v programovacím jazyce Java je to tak zvykem. Jiné jazyky mohou mít jiné pravidla.)
```java
TypPromenne nazevPromenne;
```
Příklady:
```java
int pocetOpakovani;
String jmeno;
boolean stisknuto;
```

## Nastavení hodnoty proměnné
Pokud chceme do proměnné uložit hodnotu, použijeme příkaz přiřazení:
```java
nazevPromenne = novaHodnota;
```

Příklady:
```java
pocetOpakovani = 10;
jmeno = "Karel";
stisknuto = true;
```

Můžeme také přiřadit hodnotu proměnné přímo při vytvoření proměnné:
```java
TypPromenne nazevPromenne = hodnota;
```

Příklady:
```java
int pocetOpakovani = 10;
String jmeno = "Karel";
boolean stisknuto = true;
```

## Použití hodnoty proměnné
Když někde v kódu použijeme název proměnné, dosadí se za něj hodnota proměnné:

Příklady:
```java
for (int i = 0; i < pocetOpakovani; i++) { ... }
System.out.println(jmeno);
if (stisknuto) { ... }
```