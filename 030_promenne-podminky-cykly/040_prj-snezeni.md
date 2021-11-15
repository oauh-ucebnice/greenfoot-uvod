# Vyzkoušej si – cvičení Sněžení

> Návod:
> - Zkus si přečíst zadání a zamysli se, co zvládneš naprogramovat hned.
> - Vyzkoušej naprogramovat co nejvíce sám/sama.
> - Až nebudeš vědět dál, použij první nápovědu.
> - Když si ani s&nbsp;první nápovědou nebudeš vědět rady, použij druhou nápovědu, kde už je hotový kód.
> 
> Snaž se co nejvíce zvládnout sám/sama. Pamatuj, že programování je řešení problémů, které neznáš, ne opisování kódu.

## Co se naučíš?
 - Budeme volat metody ve třídě světa.
 - Budeme generovat náhodná čísla.
 - Zopakujeme si podmínky.

## Zadání
 - Na začátku hry budou na horním okraji obrazovky dvě vločky (jako obrázek můžeš použít modrou kuličku). 
 - Po spuštění hry se vločky budou posunovat směrem k&nbsp;dolnímu okraji obrazovky.
 - Jakmile se vločky dotknou dolního okraje obrazovky, přesunou se na horní okraj obrazovky na náhodnou pozici X. Náhodné číslo z&nbsp;rozsahu _0..599_ vygeneruješ takto:
 
 ```java
    int poziceX = Greenfoot.getRandomNumber(600);
 ```
 
 > ## Poznámka:
 >
 > Veškeré názvy záměrně píšeme zde v&nbsp;zadání malými písmeny s&nbsp;mezerami a&nbsp;diakritikou. Do kódu je piš v&nbsp;souladu s&nbsp;konvencemi Javy!

<details><summary>První nápověda: Postup</summary>
Připrav si aktéra „vločka“:

 - Vločka bude mít konstruktor a&nbsp;v&nbsp;něm se otočí o&nbsp;90&nbsp;°C.
 - Vločka bude mít metodu `act()`, kde:
    - se posune o&nbsp;1&nbsp;px vpřed,
    - ověří, jestli se nedotýká okraje obrazovky (`isAtEdge()`).
    - pokud je na okraji obrazovky, přesune se na nové místo na horním okraji obrazovky (`setLocation()`).

Umísti do světa dvě vločky:
 - V&nbsp;konstruktoru světa vytvoř dvě instance třídy „vločka“.
 - Vločky umísti na horní okraj obrazovky na pozice na ose X: `200`, `400`.
</details>

<details><summary>Druhá nápověda: Kód</summary>

Třída `Vlocka`:
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

/**
 * Write a description of class Vlocka here.
 * 
 * @author Martin Šimůnek
 * @version 2021-11-15
 */
public class Vlocka extends Actor
{
   
    public Vlocka() {
        turn(90);
    }
    
    public void act()
    {
        move(1);
        if (isAtEdge()) {
            int poziceX = Greenfoot.getRandomNumber(600);
            setLocation(poziceX, 10);
        }
    }
}
```

Třída `SnezeniWorld`:
```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

/**
 * Write a description of class MyWorld here.
 * 
 * @author Martin Šimůnek 
 * @version 2021-11-15
 */
public class MyWorld extends World
{

    public MyWorld()
    {    
        super(600, 400, 1); 
        
        addObject(new Vlocka(), 200, 10);
        addObject(new Vlocka(), 400, 10);
    }
}
```

</details>

## Rozšíření 1: Různá rychlost vloček

Pokaždé, když se vločka přesune na horní okraj obrazovky, nastav jí náhodnou rychlost od 1 do 4&nbsp;px na jeden pohyb.

<details><summary>Nápověda: Postup<summary>
Využij kódu pro nastavení rychlosti z&nbsp;předchozích hodin. 
 - Přidej vločce číselný atribut `rychlost`.
 - Každá vločka si v&nbsp;konstruktoru nastaví náhodnou rychlost.
 - Připrav metodu `setRychlost(novaRychlost)`, která nastaví rychlost podle parametru.
 - Při každém přesunu vločky na horní okraj obrazovky zavolej `setRychlost()`.
</details>

<details><summary>Nápověda: Kód<summary>

Stačí upravit kód třídy „vločka“:

```java
import greenfoot.*;  // (World, Actor, GreenfootImage, Greenfoot and MouseInfo)

/**
 * Write a description of class Vlocka here.
 * 
 * @author Martin Šimůnek
 * @version 2021-11-15
 */
public class Vlocka extends Actor
{
    final int MAX_RYCHLOST = 4; // Konstanta
    
    int rychlost = 1;
    public Vlocka() {
        turn(90);
        rychlost = Greenfoot.getRandomNumber(MAX_RYCHLOST)+1;
    }
    
    public void act()
    {
        move(rychlost);
        if (isAtEdge()) {
            int poziceX = Greenfoot.getRandomNumber(600);
            setLocation(poziceX, 10);
            setRychlost(Greenfoot.getRandomNumber(MAX_RYCHLOST)+1);
        }
    }
    
    public void setRychlost(int novaRychlost) {
        rychlost = novaRychlost;
    }
}
```

</details>


<!--
Atributy vločky:
 - „Aktivní“… logická hodnota, na začátku „pravda“.
Chování vločky: 
Dokud má atribut „aktivní“ hodnotu „pravda“:
 - Vločka padá dolů.
 - Jakmile se vločka dotkne okraje obrazovky (`isAtEdge()`), zavolá metodu „umísti vločku“ světa a nastaví atribut „aktivní“ na „nepravda“.
Pro volání metody „umísti vločku“ je třeba nejprve získat aktuální svět:
    ```java
    MyWorld svet = (MyWorld) this.getWorld();
    ```

## Rozšíření 2:

Jakmile se vločky dotknou dolního okraje obrazovky, zůstanou na místě a&nbsp;dále se již nepohybují. Zároveň se na horním okraji obrazovky objeví další dvě vločky na náhodné souřadnici `x`.

<details><summary>Nápověda k&nbsp;rozšíření 1: Postup</summary>
</details>
K umisťování vloček si ve světě Greenfootu (world) připrav metodu „umísti vločku“: 
 - V&nbsp;metodě vytvoř dvě instance třídy „vločka“.
 - Obě vločky budou umístěny na horním okraji obrazovky a&nbsp;na náhodné pozici na ose X.
