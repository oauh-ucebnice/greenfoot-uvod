# Detekce kolize s aktérem

## Detekce kolize

Pokud potřebuješ zjistit, jestli se aktér (předmět ve hře) srazil s&nbsp;jiným aktérem, můžeš použít metodu `isTouching` třídy `Actor`. 

> Protože je to metoda našeho aktéra, voláme ji pomocí klíčového slova `this`: `this.isTouching(...)`.

Jako parametr musíš metodě předat buď:
 - `null` &hellip; detekujete srážku s&nbsp;jakýmkoli aktérem/objektem.
 - `NazevTridy.class` … detekuje srážky jen s&nbsp;objekty třídy s&nbsp;daným názvem.

## Příklad: Sbírání balónků
Jako příklad uvedeme hru, se míček otočí o&nbsp;180&nbsp;°, kdykoli narazí na zeď:

```java
public class Micek
{
	public void act()
	{
		// Pokud se dotýkáme objektu třídy Zed,
		//  otoč se o 180 ° a posune se o 5 px:
		if (this.isTouching(Zed.class))
		{
			turn(180);
			move(5);
		}
	}
}
```

## Další metody pro detekci kolize

 - `removeTouching(NazevTridy.class)` &hellip; Můžeš také použít metodu `removeTouching(NazevTridy.class)`, která odstraní ze světa všechny objekty třídy `NazevTridy`, které se dotýkají našeho objektu.
	
	Jako příklad uveďme kód, kde balónky budou mizet, jakmile se jich dotkne kaktus:

	```java
	public class Kaktus
	{
		public void act()
		{
			// Odstraň ze světa všechny objekty
			//  třídy Balonek, které se dotýkají
			//  kaktusu:
			this.removeTouching(Balonek.class));
		}
	}
	```

 - `getIntersectingObjects(NazevTridy.class)` &hellip; vrací seznam objektů, které kolidují s&nbsp;naším aktérem.

	Můžeme tedy například všem objektům připočíst trestný bod.

 - `getOneIntersectingObject(NazevTridy.class)` &hellip; vrací jeden kolidující objekt. Pokud žádný objekt nekoliduje, vrací `null`.

	Pokud objektů koliduje více, dostaneme jeden z&nbsp;nich, nevíme ale který.

> Všimni si, že detekci kolize můžeme provést v&nbsp;libovolném z&nbsp;kolidujících objektů. Záleží jen na naší volbě a&nbsp;na tom, co se nám více hodí. 
>
> Pokud například chceme ve třídě `Hrac` počítat body za ulovené klokany, je lepší detekci kolize provést ve třídě `Hrac`, protože tam máme k&nbsp;dispozici atribut `pocetBodu`.


## Úkol: Air Race!

### Motivace:
Vytvořte hru, ve které se letadlo vyhýbá překážkám. Necháme se inspirovat závody Red Bull Air Race, ale úlohu si zjednodušíme – poletíme stále vpřed a&nbsp;budeme se pouze vyhýbat překážkám v&nbsp;podobě majáků.

### Cíl:
Letadlo bude po celou dobu na levém okraji obrazovky. Pomocí šipek nahoru a&nbsp;dolů se bude letadlo posunovat vzhůru a&nbsp;dolů. 

Překážky (majáky) se budou objevovat na pravém okraji obrazovky a&nbsp;budou se pohybovat směrem vlevo. Úkolem hráče je pohybovat letadlem tak, aby se majákům vyhnul. 

Když se letadlo majáku nevyhne a&nbsp;srazí se(nebo se dostane příliš blízko), hra končí.
 
 ![Hra Air race!](../img/hra_airrace.png)

<details><summary>Nápověda: Postup</summary>

Letadlo:
 
 1. Vytvořte aktéra pro letadlo (obrázek letadlo).
 2. V&nbsp;konstruktoru světa (`MyWorld`) umístěte jedno letadlo na levý okraj obrazovky doprostřed.
 3. Když hráč stiskne šipky nahoru a&nbsp;dolů, letadlo se pohybuje nahoru a&nbsp;dolů po levém okraji obrazovky (na šipky doprava a doleva nereaguje).
 
 Překážky:

 4. Vytvořte aktéra pro překážku (obrázek maják či třeba kámen).
 5. Chování překážky/majáku:
     1. Pohybuje se k&nbsp;levému okraji obrazovky (volejte metodu `move()` a&nbsp;jako parametr dejte záporné číslo).
     2. Pokud dojde ke srážce s&nbsp;letadlem, ukončí hru. Ukončení hry zařídíte voláním `Greenfoot.stop()`.
 6. V&nbsp;metodě `act` světa zařiďte, aby se vygenerovalo náhodné číslo z&nbsp;rozsahu od `0` do `99`. Pokud je náhodné číslo `0`, přidá se na pravý okraj obrazovky nová překážka.
</details>

## Výzva: Vylepšení Air Race!

 1. Zvětši svět pro letadlo tím, že upravíš v&nbsp;konstruktoru světa řádek:
    `super(600, 400, 1);`
    Nastav například:
    `super(1000, 1000, 1);`
    Tím získáš pro letadlo více prostoru.
 2. Jakmile hra skončí, zobraz hlášení „Game over“. Postup pro zobrazení vyskakovacího hlášení najdeš na stránce:  http://mis.e-mis.cz/index.php/Greenfoot:_Řešení_častých_úloh
 3. Do předchozí hry přidej počítadlo času, které se vždy po 50 kolech hry zvýší o&nbsp;jedničku. Hráči tak mohou soutěžit, kdo vydrží déle ve hře.

<details><summary>Nápověda: Postup pro počítadlo času</summary>

Zvyšování počítadla prováděj v&nbsp;metodě `act` světa: zaveď si číselný atribut „odpočet“, který budeš v&nbsp;každém kole zvyšovat. Jakmile bude větší než `50`, vynuluješ odpočet a&nbsp;zavoláš zvýšení počítadla o `1`.

Realizaci počítadla můžeš převzít ze stránek: http://mis.e-mis.cz/index.php/Greenfoot:_Řešení_častých_úloh

</details>