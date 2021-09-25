# Čtení pokynů z klávesnice – pohyb

Hru můžeme ovládat také pomocí klávesnice. Pokud chceš pomocí kláves pohybovat postavičkou aktéra, je vhodné, aby šlo zmáčknout více kláves zároveň. K&nbsp;tomu je vhodná funkce `isKeyDown`, které jako parametr předáváme _kód klávesy_ jako textový řetězec (v uvozovkách). Funkce nám vrátí informaci o&nbsp;tom, zda je právě stisknutá klávesa, kterou jsme zadali jako parametr.

Zkus například do metody `act` svého aktéra přidat následující kód:

```java
public void act()
{
   if (Greenfoot.isKeyDown("space"))
   {
       this.move(3);
   }
   if (Greenfoot.isKeyDown("f"))
   {
       this.turn(10);
   }
}
```

Aktér se bude při stisku mezerníku pohybovat vpřed a&nbsp;při stisku klávesy „F“ se bude otáčet ve směru hodinových ručiček.
Všimni si, že obě klávesy mohou být stisknuty zároveň a&nbsp;aktér se zároveň pohybuje vpřed i&nbsp;otáčí.

## Kódy kláves

U&nbsp;kláves s&nbsp;písmenky je jasné, jaký parametr máš zadat metodě `isKeyDown`. Jenže co když potřebuješ reagovat na jiné klávesy? 

Kódy běžně používaných kláves jsou:
 - `space`&hellip; mezerník
 - `left`, `right`, `up`, `down`&hellip; šipky
 - `a`, `b`, `c`,&hellip; písmena a čísla na klávesnici
 - `F1`, `F2`,&hellip; funkční klávesy F1, F2,&hellip;

## Příklad: Ovládání aktéra šipkami

Vytvoř projekt v&nbsp;Greenfootu, ve kterém bude na hrací ploše jediný aktér. Tento aktér se bude po ploše pohybovat šipkami vpravo, vlevo, nahoru a&nbsp;dolů.

<details><summary>Řešení</summary>

```java
import greenfoot.*;

/**
 * Řešení příkladu Ovládání klávesnicí - učebnice Úvod do programování
 *
 * Panáček se ovládá šipkami. Všimněte si, že lze stisknout více 
 *  šipek zároveň.
 * 
 * @author Martin Šimůnek
 * @version 2020-03-12
 */
public class Panacek extends Actor
{
    public void act() 
    {
        int posunX = 0, posunY = 0;
        // Při šipce vlevo sníží hodnotu posunX o 3.
        if (Greenfoot.isKeyDown("left"))  posunX -= 3; 
        // Při šipce vpravo zvýší hodnotu posunX o 3.
        if (Greenfoot.isKeyDown("right")) posunX += 3; 
        if (Greenfoot.isKeyDown("up"))    posunY -= 3;
        if (Greenfoot.isKeyDown("down"))  posunY += 3;
        // Posune panáčka o hodnotu posunX a posunY
        this.setLocation(this.getX()+posunX, this.getY()+posunY);
    }    
}
```
</details>


## Úkol: Autíčko s volantem

Zkuste kód předchozího příkladu upravit tak, aby se aktér (autíčko) pohyboval šipkou nahoru vpřed a&nbsp;šipkou dolů couval. Šipkami vpravo a&nbsp;vlevo se bude aktér na místě otáčet o&nbsp;10&nbsp;° doprava či doleva.


## Výzva: Zrychlování a brzdění aktéra
Zkus se zamyslet, jak upravit kód z&nbsp;předchozího úkolu tak, aby aktér zrychloval šipkou nahoru a&nbsp;brzdil šipkou dolů.

<details><summary>Nápověda:</summary>

Budeš si muset vytvořit atribut, ve kterém budeš ukládat aktuální rychlost aktéra. V&nbsp;metodě `act` se budeš vždy pohybovat o&nbsp;tolik dílků, jaká je aktuální hodnota rychlosti. (Pokud má být aktér na místě, musí být rychlost 0.)
</details>