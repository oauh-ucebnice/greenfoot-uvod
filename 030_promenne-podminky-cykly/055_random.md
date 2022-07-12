# Náhodná čísla

Při vytváření her se ti občas stane, že chceš, aby se aktér choval náhodně.

K&nbsp;tomu slouží generování náhodných čísel metodou `Greenfoot.getRandomNumber(max)`.

## Použití:
```java
    int nahodnaPoziceX = Greenfoot.getRandomNumber(600);
       // Nastaví do proměnné nahodnaPoziceX náhodné číslo od 0 do 599.
```

## Příklad: Náhodné rozmístění 5 panáčků
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

/**
 * Demo náhodných čísel
 * 
 * @author Martin Šimůnek 
 * @version 2022-07-12
 */
public class MyWorld extends World
{
    public MyWorld()
    {    
        // Create a new world with 600x400 cells with a cell size of 1x1 pixels.
        super(600, 400, 1); 
        for (int i = 0; i < 5; i++) {
            int nahodnaPoziceX = Greenfoot.getRandomNumber(getWidth());
            int nahodnaPoziceY = Greenfoot.getRandomNumber(getHeight());
            addObject(new Panacek(), nahodnaPoziceX, nahodnaPoziceY);
        }
    }
}

> Nezapomeň si do projektu přidat aktéra `Panacek`!

```

## Úkol: Náhodné otočení

1. Doplň řešení předchozího úkolu tak, aby byli panáčci otočení náhodným směrem.
2. Doplň kód panáčka tak, aby se pohyboval vpřed.
