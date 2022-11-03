# Proměnné a datové typy

Proměnnou si můžeme představit jako „krabičku“, do které ukládáme nějakou hodnotu či objekt. Tuto hodnotu si potom můžeme kdykoli vyzvednout.

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

Do existující proměnné můžeme také přiřadit novou hodnotu. V&nbsp;takovém případě _nesmíme_ znovu uvádět datový typ. Datový typ se nemůže měnit:

Příklady:
```java
// příklad navazuje na předchozí příklady...
pocetOpakovani = 4;
jmeno = "Ivana";
stiskuto = true; // Můžeme znovu přiřadit stejnou hodnotu, to nevadí.
```


## Poznámka: Proměnné a atributy tříd

Pokud je nějaká „proměnná“ součástí popisu třídy, říkáme jí _atribut_ třídy. Potom se tato proměnná alokuje („vytvoří“) v&nbsp;paměti v&nbsp;okamžiku vytvoření objektu dané třídy (když voláme <code>new NazevTridy()</code>) a uvolní se po uvolnění objektu z&nbsp;paměti.

Více viz: [Atributy tříd](../020_tridy/03_atributy.md)

## K čemu se hodí proměnné?

<details><summary>Příklad použití 1: Uložení objektu</summary>

Proměnné už jsi nejspíš použil(a) mockrát. Pokaždé, když vytváříš objekt, musíš ho uložit do proměnné, abys s&nbsp;ním mohl(a) pracovat:

```java
public class MyWorld {
    public MyWorld() 
    {
        // ...

        Jablko jablko = new Jablko();  
         // Vytvořili jsme proměnnou s názvem "jablko" a datovým typem "Jablko"
        addObject(jablko, 300, 100);
    }
}
```

</details>


<details><summary>Příklad použití 2: Uložení hodnoty do proměnné</summary>

Například chceme uložit pozici našeho aktéra, abychom mohli testovat, jestli je aktér v&nbsp;pravé polovině obrazovky. Vytvoříme tedy proměnnou a uložíme do ní výsledek volání <code>getX()</code>:

```java
public class Jablko {
    public void act() 
    {
        int poziceX = getX();
        // Pozor: tento kód funguje pouze tehdy, kdy je objekt ve světě!
        // Způsobí chybu, když objekt ze světa vyjmeme metodou (removeObject()):
        int polovinaObrazovky = getWorld().getWidth()/2;
        if (poziceX > polovinaObrazovky) {
            // ... co se má stát...
        }
    }
}
```

</details>

<details><summary>Příklad použití 3: Opakované použití stejné hodnoty</summary>

Proměnné se hodí také tehdy, kdy chceme stejnou hodnotu použít vícekrát. Abychom hodnotu nemuseli opakovat, uložíme ji do proměnné:

```java
public class MyWorld {
    public MyWorld() 
    {
        // ...

        int polohaX = 10;
        Jablko jablko = new Jablko();
        addObject(jablko, polohaX, 100);
        jablko = new Jablko();  
            // do stejné proměnné jablko umisťujeme novou hodnotu
            // datový typ už neuvádíme, proměnná má stále stejný datový typ
        addObject(jablko, polohaX, 200);
    }
}
```

</details>

<details><summary>Příklad použití 4: Výpočty s hodnotami</summary>

Podobně jako v&nbsp;matematice můžeme s&nbsp;číselnými hodnotami počítat. Zatím to moc neumíme využít, ale například následující kód rozmístí na obrazovku 10 objektů, které budou rovnoměrně rozprostřené po obrazovce:

```java
public class MyWorld {
    public MyWorld() 
    {
        // ...

        int sirkaOkna = getWidth();
        int pocetJablek = 10;
        int rozestup = sirkaOkna/pocetJablek;
        int aktualniPozice = rozestup/2;
        int poziceY = getHeight()/2;
        Jablko jablko;
        for (int i = 0; i < 10; i++) 
        {
            jablko = new Jablko();
            addObject(jablko, aktualniPozice, poziceY);
            aktualniPozice = aktualniPozice + rozestup;
        }
    }
}
```

</details>
