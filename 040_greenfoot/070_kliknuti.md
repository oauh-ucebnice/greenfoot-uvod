# Detekce kliknutí na aktéra

Hodí se také umět zareagovat, když uživatel klikne myší na některého aktéra. K&nbsp;tomu použijeme metodu mouseClicked třídy Greenfoot, které předáváme aktéra, u&nbsp;kterého chceme ověřit, zda se na něj kliknulo. (Jedná se o „třídní metodu“, voláme ji tedy Greenfoot.mouseClicked(this). Třídní metody ale zatím neznáme, takže se tím nezatěžujte.)

## Příklad:
```java
public class Ryba
{
	public void act()
	{
		// Pokud hráč klikl na tohoto aktéra, odstraň aktéra:
		if (Greenfoot.mouseClicked(this))
		{
			... // Co se má stát po kliknutí?
			// Například:
			this.getWorld().removeObject(this);
		}
	}
}
```

## Úkol: Chytej!
Vytvoř hru, ve které se budou náhodně na ploše objevovat ryby. Ryba vždy po chvíli zmizí. Pokud na rybu klikneme, zmizí okamžitě a&nbsp;hráč získává bod. Pokud ryba zmizí sama, má hráč naopak trestný bod.

Přidej do hry počítadlo bodů:
Návod najdeš na webu: [Řešení obvyklých situací v&nbsp;Greenfootu (→ e-MiŠ.cz)](http://mis.e-mis.cz/index.php/Greenfoot:_Řešení_častých_úloh)

1. V&nbsp;konstruktoru světa (MyWorld) umísti počítadlo na plochu.

Vytvoř aktéra „ryba“:

2. „Ryba“ bude mít celočíselné atributy: „odpočet“ (nastavte na 0), „body za zásah“ (nastavte na 1) a „body za zmizení“ (nastavte na -1).
3. V&nbsp;metodě „act“ přidejte pomocnou proměnnou „má zmizet“ a&nbsp;nastavte ji na „nepravda“.
4. Při kliknutí na aktéra:
    1. nastav „má zmizet“ na „pravda“.
    2. uprav stav počítadla o&nbsp;tolik bodů, kolik je hodnota atributu „body za zásah“.
5. Poté zvyš hodnotu atributu „odpočet“ o&nbsp;jedničku.
6. Pokud je hodnota „odpočet“ větší než 60, potom:
    1. Nastav „má zmizet“ na „pravda“.
    2. uprav stav počítadla o&nbsp;tolik boků, kolik je hodnota atributu „body za zmizení“.
7. Pokud je „má zmizet“ „pravda“, tak odstraň aktéra ze světa: `this.getWorld().removeObject(this);`

V&nbsp;metodě `act` světa náhodně rozmisťuj ryby na hrací plochu:

8. Přidej metodu „přidej náhodně“, která:
   1. Vygeneruje náhodné číslo „x“ od 0 do šířky světa (`this.getWidth()`).
   2. Vygeneruje náhodné číslo „y“ od 0 do šířky světa (`this.getHeight()`).
   3. Umístí novou rybu na souřadnice „x“, „y“.

9. V&nbsp;metodě act světa zařiď, aby se vygenerovalo náhodné číslo od 0 do 99. Pokud je náhodné číslo menší než 2, zavolej metodu „přidej náhodně“.

## Výzva: Vylepšení hry Chytej!
Přidej do hry kaktusy. Kliknutí na kaktus znamená ztrátu 3&nbsp;bodů. Po dosažení 10&nbsp;bodů hra končí vítězstvím.

 1. V&nbsp;metodě act světa přidej kontrolu, jestli je hodnota počítadla větší než 10. Pokud je, zobraz hlášení _„Vyhrál jsi!“_ a&nbsp;ukonči hru. 
 
    Postup pro vytvoření vyskakovacího hlášení najdeš na: http://mis.e-mis.cz/index.php/Greenfoot:_Řešení_častých_úloh

 2. Klikni na aktéra „ryba“ pravým tlačítkem a&nbsp;zvol _New Subclass..._. Vytvoříš tak aktéra „Kaktus“, který bude _podtřídou_ třídy „ryba“. Smaž v&nbsp;této třídě metodu `act` (tu zdědí od „ryby“).
 3. Aktérovi „kaktus“ přidej konstruktor, ve kterém nastavíš atributy „body za zmizení“ na 0 a&nbsp;„body za zásah“ na -3. (Atributy nepiš, aktér je zdědí od „ryby“.)
 4. V&nbsp;kódu světa, kde přidáváš na obrazovku ryby, přidej s&nbsp;pravděpodobností 5/1000 nový kaktus na náhodné místo.

Uvádíme kód třídy „kaktus“, který je pro tebe nový:

<details><summary>Kód třídy „kaktus“</summary>

```java
public class Kaktus extends Ryba {
    public Kaktus() {
        bodyZaZmizeni = 0;
        bodyZaZasah = -3;
    }
}
```
</details>