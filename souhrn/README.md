# Stručný přehled učiva

## Třída

Popis vlastností objektů dané třídy – jaké mají atributy a&nbsp;jaké mají metody

Syntaxe - příklad:
```java
public class NazevTridy
{
    atributy
    konstruktory
    metody
}
```

## Atributy a pomocné proměnné
Atribut – vlastnost objektů dané třídy. Popisuje, jaký datový typ vlastnost má a&nbsp;jaký má název. Používáme ve třídách.

## Proměnná – používáme pro uložení hodnoty během výpočtu. 

Používáme v metodách.
Syntaxe:
```java
datovyTyp nazevAtributu;
Trida nazevAtributu;
datovyTyp nazevAtributu = hodnota;
Trida nazevAtributu = new Trida();
Příklady:
int rychlost;
Panacek panacek = new Panacek();
String jmeno = "Jana";
```

## Konstruktor třídy
Speciální „metoda“, která se volá při vytvoření objektu.

Syntaxe:
```java
public NazevTridy(parametry-nebo-nic)
{
    co-se-má-dělat
}
```
Příklady:
```java
public Panacek(int rychlost, String jmeno)
{
    this.rychlost = rychlost;
    this.jmeno = jmeno;
}
```

## Metoda

Funkce objektu – zpráva, na kterou umí objekt reagovat. Popisuje, co má objekt v&nbsp;reakci na zprávu udělat.

Syntaxe:
```java
public void nazev(parametry-nebo-nic)
{
    co-se-má-dělat
}
public navratovyTyp nazev(parametry-nebo-nic)
{
    co-se-má-dělat
    return vracenaHodnota;
}
```

## Volání metody/poslání zprávy objektu
Pošleme objektu zprávu – spustí se metoda (provede se kód metody).

Syntaxe:
```java
objekt.nazevMetody(parametry-nebo-nic);
this.nazevMetody(parametry-nebo-nic);
Příklady:
p.move(20);
this.pridejRybu();
this.nastavJmeno("Karel");
```

## Pravidla zápis názvů (Java)
1. Název třídy začíná velkým písmenem.
2. Názvy metod a atributů začínají malým písmenem.
3. Každé další slovo začínám velkým písmenem.
4. Názvy NEobsahují: 
    - mezery, 
    - diakritiku, 
    - další speciální znaky.

## Podmíněný příkaz
Akce se povede pouze pokud je splněná podmínka.

Syntaxe:
```java
if (podmínka)
{
    co-se-má-dělat
}
else
{
    co-se-má-dělat-v-opačném-případě
} 
```

## Cyklus
Provedeme stejnou akci vícekrát za sebou.

Syntaxe:
```java
for (int i = 0; i < počet; i++)
{
    co-se-má-dělat
}

while (podmínka)
{
    co-se-má-dělat
}
```

## Zápis podmínek
a > 5
limit != 10 … hodnota není rovna 10
hodnota <= 20
jmeno.equals("Adéla")
aktivni … logická proměnná
Příklad:
```java
if (aktivni) { … }
if (limit != 4) { … }
if (jmeno.equals("Adéla")) { … }
```


## Datové typy
`int` … celé číslo
`String` … text
`double` … desetinné číslo
`boolean` … logická hodnota
`NazevTridy` … objekt dané třídy

## Greenfoot – náhodná čísla
Generování náhodných čísel `<0, limit>` resp. `<min, max>`.

Kód:
```java
int nahoda =
	Greenfoot.getRandomNumber(limit);
int nahoda =
	min + 	Greenfoot.getRandomNumber(max+1);
```

## Greenfoot – třída Actor

Metody třídy Actor – řídí pohyb aktéra.

Kód:


`move(oKolikKroku)`
`turn(oKolikStupnu)`
`setLocation(x,y)`
`setRotation(otoceni)`
`getX()`
`getY()`
`isAtEdge()` … vrací „pravda“, pokud se aktér dotýká okraje
`getWorld()` … vrací svět, ve kterém je aktér umístěn
```

## Greenfoot – třída World

Metody třídy World.

Kód:
```java
Trida akter = new Trida(parametry);
addObject(akter, x, y);
removeObject(akter);

getWidth();
getHeight();
```

## Greenfoot – pohyb za myší
Pohybuje aktérem směrem ke kurzoru myši resp. zároveň s&nbsp;myší.

Kód:
```java
MouseInfo mi = Greenfoot.getMouseInfo();
if (mi != null) {
	turnTowards(mi.getX(), mi.getY();
	move(rychlost);
}

if (mi != null) {
	setLocation(mi.getX(), mi.getY());
}
```

## Greenfoot – ovládání klávesnicí

Pohybuje aktérem podle toho, jak mačkáme klávesy. Může být zmáčknuto více kláves naráz.

Kód:
```java
if (Greenfoot.isKeyDown("left")) {
	co se má stát...
}
```

## Greenfoot – spuštění akce stisknutím klávesy

Provede akci na základě stisknutí klávesy (zde mezerníku a&nbsp;klávesy „x“). Akce se spustí jen jednou.

Kód:
```java
String klavesa = Greenfoot.getKey();
if ("space".equals (klavesa)) {
	co se má stát...
}
if ("x".equals (klavesa)) {
	co se má stát...
}
```

## Greenfoot – kódy kláves na klávesnici
Šipky: `left`, `right`, `up`, `down`
Mezerník: `space`
Enter: `enter`

## Souhrn jako PDF a ODT

- [Souhrn učiva ve formátu PDF](uvod-pro1-souhrn.pdf)
- [Souhrn učiva ve formátu ODT (Libre Office)](uvod-pro1-souhrn.odt)