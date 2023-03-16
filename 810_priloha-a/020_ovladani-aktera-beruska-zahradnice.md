# Příklad: Ovládání aktéra – Beruška zahradnice

> POZOR! Tento úkol předpokládá, že již znáte čtení vstupů a&nbsp;práci s&nbsp;objekty!
>
> Návod je záměrně psán tak, abyste si museli vybavit a&nbsp;tím si procvičili správný postup při zjištění vstupů v&nbsp;Greenfootu.
>
> Nepouštějte se do tohoto úkolu, dokud tyto věci nemáte zvládnuté z&nbsp;předchozích kapitol!

## Motto:
Vyrobte hru, kde se bude beruška pohybovat vždy směrem ke kurzoru myši. Při stisku klávesy beruška zasadí květinu na pozici, na které právě je. Kytičky budou mít náhodnou velikost &mdash; některé budou větší a některé menší.

![Příklad Beruška zahradnice](../img/hra_beruska-zahradnice.png)

## Co se máte naučit:
V tomto úkolu si máte procvičit ovládání her v&nbsp;Greenfootu:
 - Čtení vstupu z&nbsp;klávesnice
 - Zjištění pozice myši
 - Zjištění rozměru hrací plochy

 Navíc se naučíte:
 - Nastavení velikosti obrázku

Zároveň si procvičíte pojmy z&nbsp;oblasti objektového programování a&nbsp;jejich zápis v&nbsp;Javě:
 - Zápis tříd
 - Zápis konstruktoru
 - Zápis metod

## Postup – první část: Květina
 1. Vytvořte v&nbsp;Greenfootu nový projekt (scenario) s&nbsp;názvem _Beruška_.
 2. Vytvořte třídu s&nbsp;názvem _Květina_ – bude potomkem (subclass) třídy `Actor`. Nastavte jí vhodný obrázek.
 3. Květina nebude využívat metodu `act`.
 4. Květina bude mít metodu _nastav velikost_. Ta dostane jeden číselný parametr a&nbsp;nastaví velikost obrázku na hodnotu parametru (velikost na souřadnicích X i Y bude stejná).  
   Pro změnu velikosti obrázku použij kód:

      ```java
      GreenfootImage image = this.getImage();
      image.scale(novaVelikostX, novaVelikostY)
      this.setImage(image);
      ```
 
 5. Květina bude mít konstruktor s&nbsp;jedním parametrem _velikost_ (bude to celé číslo).
    V&nbsp;kódu konstruktoru zavolej metodu _nastav velikost_ a&nbsp;jako parametr jí dej náhodné číslo od 20&nbsp;do 120.

## Postup – druhá část: Beruška a&nbsp;její pohyb

 5. Vytvořte třídu s&nbsp;názvem `Beruška` – bude potomkem (subclass) třídy Actor.

 6. Vytvořte metodu s&nbsp;názvem `Pohyb` k&nbsp;myši. Metoda nemá parametr a&nbsp;nevrací žádnou hodnotu. Metoda:

    1. Vytvoří celočíselné proměnné Myš X&nbsp;a Myš Y&nbsp;a uloží do nich aktuální souřadnice myši – viz kapitola [Čtení informací z&nbsp;myši](https://github.com/oauh-ucebnice/greenfoot-uvod/blob/main/040_greenfoot/030_mys.md)
 
    2. Zavolá metodu Set location s&nbsp;parametry _Myš X_&nbsp;a _Myš&nbsp;Y_, čímž posune aktéra na aktuální souřadnice myši.

 7. Vytvořte metodu s&nbsp;názvem Mám sázet. Metoda nemá parametr a&nbsp;nevrací žádnou hodnotu. Metoda:

    Zjistí, zda byl zmáčknut mezerník. Pokud byl zmáčknut mezerník, pak:

    1. Vytvoří novou instanci třídy Květina.
    2. Nově vytvořenou instanci umístíme do světa na souřadnice, na kterých je právě teď beruška:

        ```java 
        this.getWorld().addObject(kvetina, this.getX(), this.getY())
        ```

 8. Metoda `act` třídy _Beruška_ bude provádět následující akce:
    1. Zavolá metodu _pohyb k&nbsp;myši_.
    2. Zavolá metodu _mám sázet_.

## Postup – třetí část: svět hry

 9. Vytvořte třídu s&nbsp;názvem _Beruška World_ – bude potomkem (subclass) třídy World. Jako pozadí nastavte vhodný obrázek.

 10. V&nbsp;konstruktoru třídy _Beruška World_ proveďte:
    Vytvořte instanci třídy Beruška a&nbsp;umístěte ji doprostřed hrací plochy. 
    
        Zjištění poloviny hrací plochy:
        ```java 
        int x = this.getWidth()/2;
        int y = this.getHeight()/2;
        ```
