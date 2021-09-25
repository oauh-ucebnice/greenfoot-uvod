# Příklad: Proměnné, cykly, podmínky – Míčky

POZOR! Tento úkol předpokládá, že již znáte základní pojmy objektového programování a umíte používat cykly a podmínky!

> Návod je záměrně psán tak, aby sis musel(a) vybavit a&nbsp;tím si procvičili správný zápis cyklů, podmínek, tříd, metod, konstruktorů.
>
> Nepouštěj se do tohoto úkolu, dokud tyto pojmy nemáš zvládnuté z&nbsp;předchozích kapitol!

## Motto:
V tomto úkolu si vytvoříte hrací plochu, po které budou létat míčky a odrážet se od stěn. 

## Co se máš naučit:
V&nbsp;tomto úkolu si máš procvičit zápis cyklů a&nbsp;podmínek v&nbsp;Javě. 

<details><summary>Postup – první část: třída Míček</summary>

1. Vytvoř v&nbsp;Greenfootu nový projekt (scenario) s&nbsp;názvem _Míčky_.
2. Vytvoř třídu s&nbsp;názvem „Míček“ – bude potomkem (subclass) třídy `Actor`. Nastav jí vhodný obrázek.
3. Míček bude mít dva atributy s názvy Rychlost X a Rychlost Y. Oba atributy budou celá čísla.
4. V konstruktoru třídy Míček nastav oběma atributům jako hodnotu náhodné číslo od 0 do 10. Poté od hodnoty obou atributů odečti číslo 5. (Tím atributům nastavíš náhodnou hodnotu od -5 do 5.)

Konstruktor třídy Míček nemá žádné parametry.

5. Vytvoř metodu _Posun_. Metoda je bez parametrů, nevrací nic. Metoda spočítá nové souřadnice X a Y míčku tak, že ke stávajícím přičte hodnotu atributů Rychlost X a Rychlost Y. Nová souřadnice X tedy vznikne tak, že vezmeme stávající souřadnici X (získáme voláním metody getX) a přičteme hodnotu Rychlost X. Totéž pro Y.
Nové souřadnice nastav pomocí metody `setLocation` (již existuje).
6. Vytvoř metodu Odraz. Metoda je bez parametrů a vrací logickou hodnotu.
Pokud je míček na okraji obrazovky (metoda `isAtEdge` vrací logickou hodnotu „pravda“), potom se zavolá kód:

```java
int x = this.getX(); int y = this.getY();
if ((x >= this.getWorld().getWidth()) || (x <= 0)) {
    rychlostX = -1*rychlostX;
}
if ((y >= this.getWorld().getHeight()) || (y <= 0)) {
    rychlostY = -1*rychlostY;
}
```
7. V metodě `act` proveď:
    - Zavolej metodu Posun.
    - Vytvoř pomocnou proměnnou Obrat datového typu logická hodnota.
    - Do proměnné Obrat ulož výsledek volání funkce Odraz.
    - Pokud je v&nbsp;proměnné Obrat hodnota „pravda“, pak vypiš do textové konzole text: „Nastal odraz“.
</details>

Postup – první část: třída MíčekWorld
8. Vytvořte třídu s názvem MíčekWorld – bude potomkem (subclass) třídy World.
9. V konstruktoru třídy MíčekWorld vytvořte 20 objektů třídy Míček a umístěte je na plochu na náhodné souřadnice.
Rozšíření
10. Zkuste třídy doplnit tak, aby se míčky odráželi od sebe. 

<details><summary>Řešení příkladu</summary>

## Třída Míček

```java
public class Micek extends Actor
{
    int rychlostX;
    int rychlostY;
    public Micek()
    {
        this.rychlostX = Greenfoot.getRandomNumber(20)-10;
        this.rychlostY = Greenfoot.getRandomNumber(20)-10;
    }
    public void posun()
    {
        this.setLocation(
                this.getX()+this.rychlostX, 
                this.getY()+this.rychlostY
            );
    }
    public boolean odraz()
    {
        if (this.isAtEdge())
        {
            int x = this.getX(); int y = this.getY();
            if ((x >= this.getWorld().getWidth()-1) || (x <= 0)) 
            {
                rychlostX = -1*rychlostX;
            }
            if ((y >= this.getWorld().getHeight()-1) || (y <= 0)) 
            {
                rychlostY = -1*rychlostY;
            }
            return true;
        }
        else
        {
            return false;
        }
    }
    public void act() 
    {
        this.posun();
        boolean obrat = this.odraz();
        if (obrat) 
        {
            System.out.println("Nastal odraz");
        }
    }    
}
```

## Třída MíčekWorld

```java
public MicekWorld()
{
    super(600, 400, 1); 
    for (int i = 0; i < 10; i++)
    {
        Micek micek = new Micek();
        this.addObject(
                micek, 
                Greenfoot.getRandomNumber(this.getWidth()),
                Greenfoot.getRandomNumber(this.getHeight())
            );
    }
}
```
</details>