# Souhrn: Ovládání aktéra a světa

## Ovládání aktéra

Shrňme si nyní, co můžeme dělat s&nbsp;aktérem Greenfootu (jaké metody můžeme volat):

 - `getX()`, `getY()` &hellip; zjištění aktuální pozice aktéra ve světě

 - `move(pocetKroku)` &hellip; posun o&nbsp;zadaný počet kroků vpřed
 - `turn(uhel)` &hellip; otočení o&nbsp;zadaný úhel vpravo
 - `turnTowards(x, y)` &hellip; otočení směrek k&nbsp;zadané pozici
 - `isAtEdge()` &hellip; vrací „pravda“, pokud je aktér na okraji obrazovky
 - `setLocation(x, y)` &hellip; přesun aktéra na zadanou pozici
 - `setRotation(uhelOtoceni)` &hellip; nastaví otočení aktéra oproti základní pozici
 - `getWorld()` &hellip; vrací svět, ve kterém aktér právě je umístěný (použití viz dále)

## Ovládání světa

Metody, které můžeme využít u&nbsp;světa:
 - `getWidth()`, `getHeight()` &hellip; zjištění rozměrů světa
 - `addObject(akter, x, y)` &hellip; přidání aktéra do světa
 - `removeObject(akter)` &hellip; vyjmutí aktéra ze světa


## Další funkce

Další užitečné funkce v&nbsp;Greenfootu:
 - `Greenfoot.getRandomNumber(limit)` &hellip; Generování náhodných čísel.
 - `Greenfoot.getRandomNumber((max-min+1))+min` &hellip; Generování náhodných čísel z&nbsp;rozsahu `min`...`max`

## Jak z&nbsp;aktéra ovládat svět?

U&nbsp;některých her potřebujeme v&nbsp;metodách aktéra ovlivnit zbytek světa. Příkladem takové situace může být zasazení kytičky či výstřel, kdy aktér vkládá do světa jiného aktéra.

Jak už jsme uvedli výše, používáme k&nbsp;tomu metodu `getWorld()`. Například takto:
```java
    // Do proměnné svět uložíme svět, ve kterém je náš objekt vložen:
    World svet = getWorld();                
    // Můžeme se světem pracovat:    
    svet.addObject(new Kvetina(), 300, 100);
```

> Upozornění!
>
> Abychom mohli použít metodu `getWorld()`, musí být náš objekt již vložen ve světě a&nbsp;nesmíme ho ze světa vyjmout!
>
> Častou chybou je, že začátečníci při srážce dvou předmětů odstraní předmět ze světa, ale v&nbsp;kódu metody `act` poté volají `getWorld()` ve snaze upravit dále svět. Tento postup vede k&nbsp;havárii aplikace.

<details><summary>Příklad použití `getWorld()`: zasazení květiny</summary>

```java
public class Zahradnik extends Actor 
{
    /**
     * Vytvoří nového aktéra třídy Kvetina a umístí ho do světa 
     * na stejnou pozici, kde je nyní zahradník.
     */
    public void zasadKvetinu()
    {
        World svet = getWorld();
        svet.addObject(new Kvetina(), getX(), getY());
    }

    public void act()
    {
        if (/*... podmínka pro zasazení květiny ...*/)
        {
            zasadKvetinu();
        }

    }
}
```

</details>


## Volání specifických metod světa

O&nbsp;něco složitější je situace, kdy chceme z&nbsp;aktéra volat metody světa, které jsme si sami naprogramovali. V&nbsp;takovém případě nám metoda `getWorld()` sama nestačí a&nbsp;musíme použít přetypování:
```java
    // Do proměnné svět uložíme svět, ve kterém je náš objekt vložen: 
    NazevSvetaWorld svet = (NazevSvetaWorld) getWorld();
    // Nyní můžeme volat i vlastní metody:
    svet.nazevVlastniMetody();
```

<details><summary>Příklad použití `getWorld()` s&nbsp;přetypováním: metoda `resetWorld()`</summary>

```java
public class SpawnWorld extends World
{
    /**
     * Metoda přidá do středu světa příšeru, která bude otočená 
     * směrem k zadaným souřadnicím.
     * Předpokládáme, že třída Monster už existuje -> pokud ji 
     * zatím nemáš, vytvoř si ji!
     * @param x Souřadnice X, ke které má být příšera otočena
     * @param y Souřadnice Y, ke které má být příšera otočena
     */
    public void spawnMonsterTurnedTowards(int x, int y)
    {
        Monster monster = new Monster();
        int stredX = getWidth()/2;
        int stredY = getHeight()/2;
        addObject(monster, stredX, stredY);
        monster.turnTowards(x, y);
    }

    public SpawnWorld()
    {
        super(600, 400);
        addObject(new Spawner, 10, 200);
    }
}

public class Monster extends Actor
{
    public void act() 
    {
        move(1);
    }
}

public class Spawner extends Actor
{
    int pocitadlo = 0;

    public void act()
    {
        // Po deseti krocích hry spusť vytvoření příšery 
        //  metodou spawnMonsterTurnedTowards():
        pocitadlo++;
        if (pocitadlo >= 10)
        {
            pocitadlo = 0;
            SpawnWorld svet = (SpawnWorld) getWorld();
            svet.spawnMonsterTurnedTowards(getX(), getY());
        }

        // Posuň se...
        move(2);
    }
}
```

</details>

## Vyzkoušej si: Ohňostroj

Vytvoř svět s&nbsp;aktérem „světlice“ (jako obrázek můžeš použít kuličku nebo jiný obrázek).
1. Na začátku vlož do světa jeden objekt „světlice“.
2. Světlice poletí vpřed. Po dvaceti krocích hry se světlice rozdělí na dvě stejně velké světlice &mdash; jedna poletí mírně vpravo (otoč ji o 30°), druhá mírně vlevo (otoč ji o&nbsp;-30°). Původní světlice pokračuje původním směrem.
3. Pokud světlice narazí na okraj obrazovky, zmizí.