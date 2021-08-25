# První pohled do kódu

Dosud jsme s&nbsp;prostředím Greenfoot nakládali, jako by to byl spíš kreslicí program. Umisťovali jsme na plochu obrázky a&nbsp;pohybovali jimi posíláním zpráv. My ale chceme programovat hry. Chceme tedy, aby se některé objekty/obrázky pohybovaly samy, a&nbsp;jiné aby ovládal hráč myší či prostřednictvím klávesnice. Nyní se naučíme psát kód pro ovládání aktérů a&nbsp;v&nbsp;další části knihy se postupně budeme učit, jak popsat chování jednotlivých aktérů.

## Zobrazení kódu aktéra

Zkus provést dvojklik na název aktéra – třeba na aktéra `Ryba`. (Můžete také kliknout pravým tlačítkem a&nbsp;vybrat Open in editor - Otevřít v&nbsp;editoru.) Mělo by se aktivovat okno s&nbsp;kódem, který popisuje vlastnosti aktérů třídy Ryba.

```java
import greenfoot.*; // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

/**
 * Write a description of class Ryba here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
public class Ryba extends Actor
{
    /**
     * Act - do whatever the Ryba wants to do. This method is called whenever
     * the 'Act' or 'Run' button gets pressed in the environment.
     */
    public void act() 
    {
        // Add your action code here.
    }    
}
```

## Komentáře

Text, který jsme označili šedivě, je _komentář_. Můžeme ho klidně smazat, nebo si místo něj napsat vlastní poznámky. Java si tohoto textu nebude všímat.

Když se na řádku objeví dvě lomítka hned za sebou `//`, vše, co následuje za jimi se bere jako komentář – počítač si toho nevšímá. 

Stejně tak pokud nějaký text uvodíme kombinací `/*` a&nbsp;následně ukončíme kombinací znaků `*/`, vše mezi tím se považuje za komentář.
Více viz kapitola Chyba: zdroj odkazu nenalezen.

## Kód aktéra – import knihovny

Podívejme se tedy, co v&nbsp;kódu najdeme kromě komentářů. Na prvním řádku najdeme import knihovny s&nbsp;třídami Greenfootu:

```java
import greenfoot.*;
```

Import knihoven pro nás teď není důležitý, musíme si ale dávat pozor, abychom tento řádek nepoškodili. Kdyby tento řádek chyběl, nebo byl poškozený, naše hra by nefungovala. Naštěstí je import hned na prvním řádku, kam běžně nepotřebujeme nic psát. Je tedy málo pravděpodobné, že bychom kód poškodili.

## Kód aktéra – třída

Dále už to bude o&nbsp;něco zajímavější. Dalším kouskem kódu je začátek třídy Ryba (nebo jiné, pokud si otevřete kód jiné třídy):

```java
public class Ryba extends Actor
{
    // … tady je popis třídy, ten si vysvětlíme za chvíli… 
}
```

Ani do tohoto kódu bychom neměli zasahovat. Pokud bychom si ale rozmysleli, že se třída má jmenovat jinak, můžeme zde opravit název třídy a&nbsp;Greenfoot změnu správně promítne. Ale pozor! Pokud někde v&nbsp;dalším kódu název třídy používáme, tento kód by přestal fungovat!

## Kód aktéra – metoda act()
V popisu třídy můžeme mít „metody“ a „atributy“. Zatím si vystačíme jen s&nbsp;jedinou metodou, která už je v&nbsp;kódu připravená. Jmenuje se act() a&nbsp;Greenfoot tuto metodu spouští pravidelně stále dokola postupně pro všechny aktéry. 

Pokud máme ve světě tři objekty – dvě ryby a&nbsp;letadlo, Greenfoot bude stále dokola spouštět:
- `act()` první ryby,
- `act()` druhé ryby,
- `act()` letadla,
- a&nbsp;znovu a&nbsp;znovu...

Zkuste nyní přidat do kódu řádek, který posune aktéra o&nbsp;pár pixelů dopředu:

```java
    public void act() 
    {
        // Add your action code here.
        this.move(2);
    }    
```

Pokud kód napíšeš správně a&nbsp;umístíš aktéra do světa, bude se nyní aktér pohybovat vpřed tak dlouho, až narazí na okraj obrazovky, kde se zastaví.
Tímto způsobem popisujeme, jak se budou chovat jednotliví aktéři.

## Vytvoření prostředí hry – konstruktor světa

Pojďme se nyní podívat, jak vypadá kód, který vznikl, když jsme vytvořili nové prostředí hry (nový svět):

Kód zobrazíme dvojklikem na položku světa v&nbsp;pravém menu. Měli bychom vidět následující kód:

```java
import greenfoot.*;  //(World, Actor, GreenfootImage, Greenfoot and MouseInfo)

/**
 * Write a description of class MyWorld here.
 * 
 * @author (your name) 
 * @version (a version number or a date)
 */
public class MyWorld extends World
{
    /**
     * Constructor for objects of class MyWorld.
     * 
     */
    public MyWorld()
    {    
        // Create a new world with 600x400 cells with a cell size of 1x1 pixels.
        super(600, 400, 1); 
    }
}
```

Co zde vidíme?
1. Import knihovny Greenfootu na prvním řádku – to už známe.
2. Třídu MyWorld – zápis tříd už také známe.
3. Speciální metodu, která nemá v&nbsp;hlavičce slovíčko void a&nbsp;jmenuje se stejně jako třída. Tato metoda se jmenuje konstruktor a&nbsp;spustí se jen jednou při vytvoření objektu třídy `MyWorld`.

Konstruktor je tedy popsán tímto kódem:
```java
    public MyWorld()
    {    
        // Create a new world with 600x400 cells with a cell size of 1x1 pixels.
        super(600, 400, 1); 
    }
```

Do konstruktoru světa budeme umisťovat kód, který chceme, aby se provedl jednou na začátku hry – kód, který hru připraví.

Zkusme nyní do kódu něco přidat, ať si vyzkoušíme, že to bude opravdu fungovat:

```java
    public MyWorld()
    {    
        // Create a new world with 600x400 cells with a cell size of 1x1 pixels.
        super(600, 400, 1);

        Ryba ryba = new Ryba();        
        this.addObject(ryba, 300, 200);
    }
```

Jak asi správně tušíš, když si kód přečteš, tento kód vytvoří a&nbsp;umístí novou rybu. Když nyní klikneš na tlačítko „Compile“, na hrací ploše by se měla objevit ryba uprostřed obrazovky a&nbsp;měla by začít vykonávat to, co je popsáno v&nbsp;její metodě `act()`. 

Kdykoli nyní restartujete hru tlačítkem „Restart“, ryba se vždy vrátí zpět doprostřed obrazovky.

> Dávej si pozor, kam kód píšeš. Je důležité, aby byl mezi složenými závorkami a&nbsp;abys žádné složené závorky neumazal(a). Postupně si vysvětlíme, jaká pravidla musíš dodržovat, co můžeš a&nbsp;co nemůžeš.

## Může mít svět metodu `act()`?

Ve skutečnosti mohou mít i&nbsp;aktéři konstruktor a&nbsp;i&nbsp;ve světě může být metoda `act()`. Tato metoda se bude podobně jako metody `act()` v&nbsp;aktérech spouštět pravidelně stále dokola. Protože ale zatím vlastní metody psát neumíme, nebudeme se tím zatím zatěžovat.

## Nefunguje mi to!

Pokud ti kód nefunguje, oslov svého učitele nebo kamaráda a&nbsp;najděte chybu. Opravováním chyb se učíš najvíc! Pamatuj, programování je řešení problémů a&nbsp;to se potřebuješ naučit!