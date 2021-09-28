# Příklad: Ovládání aktéra – Beruška zahradnice

> POZOR! Tento úkol předpokládá, že již znáte čtení vstupů a práci s objekty!
>
> Návod je záměrně psán tak, abyste si museli vybavit a tím si procvičili správný postup při zjištění vstupů v Greenfootu.
>
> Nepouštějte se do tohoto úkolu, dokud tyto věci nemáte zvládnuté z předchozích kapitol!

## Motto:
Vyrobte hru, kde se bude beruška pohybovat vždy směrem ke kurzoru myši. Při stisku klávesy beruška zasadí květinu na pozici, na které právě je.

![Příklad Beruška zahradnice](../img/hra_beruska-zahradnice.png)

## Co se máte naučit:
V tomto úkolu si máte procvičit ovládání her v Greenfootu:
 - Čtení vstupu z klávesnice
 - Zjištění pozice myši
 - Zjištění rozměru hrací plochy

Zároveň si procvičíte pojmy z oblasti objektového programování a jejich zápis v Javě:
 - Zápis tříd
 - Zápis konstruktoru
 - Zápis metod

## Postup – první část: Květina
 1. Vytvořte v Greenfootu nový projekt (scenario) s názvem _Beruška_.
 2. Vytvořte třídu s názvem _Květina_ – bude potomkem (subclass) třídy `Actor`. Nastavte jí vhodný obrázek.
 3. Květina nebude využívat metodu `act`.
 4. Květina bude mít metodu _nastav velikost_. Ta dostane jeden číselný parametr a nastaví velikost obrázku na hodnotu parametru vynásobenou číslem 50.

       ```java
      this.setImage(this.getImage().scale(novaVelikostX, novaVelikostY));
      ```
 
 5. Květina bude mít konstruktor s jedním parametrem _velikost_ (bude to celé číslo).
    V kódu konstruktoru zavolej metodu _nastav velikost_ a jako parametr jí dej náhodné číslo od 1 do 10.

## Postup – druhá část: Beruška a její pohyb

 5. Vytvořte třídu s názvem Beruška – bude potomkem (subclass) třídy Actor.

 6. Vytvořte metodu s názvem Pohyb k myši. Metoda nemá parametr a nevrací žádnou hodnotu. Metoda:

    1. Vytvoří celočíselné proměnné Myš X a Myš Y a uloží do nich aktuální souřadnice myši – viz kapitola Chyba: zdroj odkazu nenalezen.
 
    2. Zavolá metodu Set location s parametry Myš X a Myš Y, čímž posune aktéra na aktuální souřadnice myši.

 7. Vytvořte metodu s názvem Mám sázet. Metoda nemá parametr a nevrací žádnou hodnotu. Metoda:

    Zjistí, zda byl zmáčknut mezerník. Pokud byl zmáčknut mezerník, pak:

    1. Vytvoří novou instanci třídy Květina.
    2. Nově vytvořenou instanci umístíme do světa na souřadnice, na kterých je právě teď beruška:

        ```java 
        this.getWorld().addObject(kvetina, this.getX(), this.getY())
        ```

 8. Metoda `act` třídy _Beruška_ bude provádět následující akce:
    1. Zavolá metodu _pohyb k myši_.
    2. Zavolá metodu _mám sázet_.

## Postup – třetí část: svět hry

 9. Vytvořte třídu s názvem _Beruška World_ – bude potomkem (subclass) třídy World. Jako pozadí nastavte vhodný obrázek.

 10. V konstruktoru třídy _Beruška World_ proveďte:
    Vytvořte instanci třídy Beruška a umístěte ji doprostřed hrací plochy. 
    
        Zjištění poloviny hrací plochy:
        ```java 
        int x = this.getWidth()/2;
        int y = this.getHeight()/2;
        ```
