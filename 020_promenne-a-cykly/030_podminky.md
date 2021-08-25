# Jak psát podmínky

Zpočátku se nejčastěji setkáme s podmíněnými příkazy, které pracují s čísly nebo logickými hodnotami.

Uvedeme si zde nejjednodušší příklady podmínek. Podrobnější výklad najdete v mnoha pokročilejších zdrojích, například: http://mis.e-mis.cz/index.php/

## Porovnání čísel
K porovnání čísel používáme operátory:
 	Podmínka...	… je splněna když:
 	 a == b	 a je rovno b
 	 a < b; a <= b	 a je menší než b; a je menší nebo rovno b
 	 a > b, a >= b	 a je větší než b; a je větši nebo rovno b
 	 a != b	 a není rovno b

Důležité je nezapomenout, že při porovnávání je třeba psát dvě rovnítka za sebou („==“)!!! Jeden znak „=“ znamená přiřazení – uloží hodnotu vpravo do proměnné vlevo (viz kapitola Nastavení hodnoty proměnné).
```java
int zivoty = 10;
// ...
if (zivoty <= 0) this.gameOver();
```

##  Logické proměnné
Logickou proměnnou můžeme použít přímo místo podmínky. Logická proměnná totiž sama obsahuje výsledek nějaké podmínky.

Pokud chceme testovat, zda podmínka NENÍ splněna, napíšeme před ni vykřičník.
```java
int x = 5;
boolean a = true;
boolean b = false;
boolean c = x > 10;
boolean d = overKod();
public boolean overKod() { return true; }
if (a) { … }
if (b) { … }
if (! c) { … } // Provede se, když proměnná c obsahuje logickou hodnotu „nepravda“.
if (d) { … }
if (overKod()) { … }  // Provede se, když metoda overKod() vrací hodnotu „pravda“.
```

## Porovnání textů

Pokud chceme zjistit, zda jsou dva texty stejné, použijeme metodu `equals()`:
```java
String klavesa = Greenfoot.getKey();
if ("space".equals(klavesa)) 
{
	System.out.println("Zmáčkl jsi mezerník!");
}
```

## Skládání více podmínek

Podmínky můžeme také kombinovat. Uděláme to tak, že mezi dvě podmínky vložíme značky logických funkcí AND, OR, nebo NOT:
 	Podmínky...	… je splněna když:
 	podm1 && podm2	 musí být splněny obě podmínky (logické AND)
 	podm1 || podm2	 stačí splnění jedné z podmínek (logické OR)
 	! podm1	 není splněna podmínka podm1 (logické NOT)

Například tedy:
```java
if (Greenfoot.isKeyDown("space") && pocetZivotu > 3) 
{
	System.out.println(
 		"Uživatel drží mezerník a zároveň je počet
 		 životů větší než 3!"
 	);
}
```

Nebo jiný příklad:
```java
if (! Greenfoot.isKeyDown("space")) 
{
	System.out.println("Není stisknutý mezerník!");
}
```