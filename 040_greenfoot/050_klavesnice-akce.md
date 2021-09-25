# Čtení pokynů z klávesnice – spuštění akce

Pokud chceš na základě stisku klávesy provádět nějakou akci (zasazení kytičky, střelbu,...), není vhodné používat metodu `isKeyDown`, protože by se akce často spustila opakovaně.

V&nbsp;takovém případě je lepší využít metodu `getKey`. Tato metoda čte klávesy, které jsme napsali. Pokud klávesu budeme držet, klávesnice zajistí opakované psaní písmene/znaku. Každé volání funkce `getKey` vybere z&nbsp;bufferu klávesnice jeden napsaný znak. 

> Při použití této funkce nelze číst více kláves naráz. Například když stiskneš a&nbsp;držíš klávesu „F“, klávesnice generuje opakovaně do bufferu písmenka „F“. Jakmile ale zmáčkneš klávesu „G“, klávesnice si již dále nevšímá toho, že máš stisknutou i&nbsp;klávesu „F“ a&nbsp;bude generovat písmenko „G“.

Kód pro detekci stisku klávesy opět umísti do metody `act`:

```java
String klavesa = Greenfoot.getKey();
if ("space".equals(klavesa))
{
    Kvetina kvetina = new Kvetina();
    this.getWorld().addObject(kvetina, this.getX(), this.getY());
}
```

Kód běžně používaných kláves jsou stejné jako u&nbsp;metody `isKeyDown` (viz předchozí kapitola).

## Příklad: Velikonoční klokan
Vytvoe projekt v&nbsp;Greenfootu, ve kterém bude na hrací ploše jediný aktér &mdash; klokan. Způsob pohybu aktéra si zvol libovolný. Při stisknutí mezerníku klokan položí na hrací plochu modré velikonoční vejce (modrou kuličku). Vajíčko bude na stejné pozici, na které je v&nbsp;okamžiku stisku klávesy klokan.

<details><summary>Řešení</summary>

```java
import greenfoot.*;
/**
 * Řešení příkladu Velikonoční klokan - učebnice Úvod do programování
 * 
 * 
 * Klokan se pohybuje s myší. Při stisku mezerníku vytvoří na svých
 * pozicích nový objekt - instanci třídy Vejce (modrá kulička).
 * 
 * @author Martin Šimůnek
 * @version 2020-03-12
 */
public class VelikonocniKlokan extends Actor
{
    private void resPohyb()
    {
        MouseInfo mi = Greenfoot.getMouseInfo();
        if (mi != null)
        {
            this.setLocation(mi.getX(), mi.getY());
        }
    }
    public void act() 
    {
        this.resPohyb();
        String klavesa = Greenfoot.getKey();
        if ("space".equals(klavesa))
        {
            World svet = this.getWorld();
            svet.addObject(new Vejce(), this.getX(), this.getY());
        }
    }    
}
```
</details>


## Úkol: Ostražitý tuleň
Vytvoř aktéra, který se bude pohybovat společně s&nbsp;myší. Při stisku klávesy „R“ se otočí o&nbsp;180&nbsp;° („rozhlédne se“).

## Výzva: Střílející raketa

Zkus doprostřed světa umístit vhodného aktéra, třeba raketu. Při pohybu myši otáčej raketou směrem ke kurzoru myši (raketa bude stále na jednom místě, pouze se bude otáčet). Při zmáčknutí  mezerníku raketa zvoleným směrem „vystřelí“ kuličku (nebo jiný objekt), která se bude pohybovat ve směru, kterým je raketa otočená.

<details><summary>Nápověda:</summary>

Pro otáčení rakety využiješ metodu třídy `Actor` s&nbsp;názvem `turnTowards(x, y)`, která raketu otočí směrem k&nbsp;zadanému bodu. 

Vytvoření kuličky už umíš. 

Před umístěním kuličky do světa pošli kuličce zprávu `setRotation` a&nbsp;jako parametr jí předejte výsledek metody `getRotation` rakety. Tím kuličku při umístění do světa otočíš stejným směrem, kterým je otočena raketa. 

Třída `Kulicka` bude mít v&nbsp;metodě `act` jediný příkaz – pohybovat se vpřed o&nbsp;tři dílky.
</details>