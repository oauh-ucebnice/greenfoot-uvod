# Metody a konstruktory s parametry a návratovou hodnotou

## Metody z hlediska objektového programování

Pokud mluvíme obecně o&nbsp;objektech, říkáme, že objekty si „posílají zprávy“. V&nbsp;kódu je to zachyceno tak, že jeden objekt volá metodu jiného objektu. Metody pak upravují hodnoty atributů objektu. Když chceme změnit hodnotu atributů nějakého objektu, pošleme mu zprávu – zavoláme metodu. Tato metoda popisuje, jak se má na zprávu zareagovat. Obvykle tak, že upravíme hodnoty atributů objektu, nebo voláme další metody.

Pokud například chceme, aby se aktér medvěd ve světě Greenfootu posunul o&nbsp;5 kroků, zavoláme jeho metodu move() s&nbsp;parametrem&nbsp;`5`:
```java
medved.move(5);
```

Pokud chceme, aby se medvěd otočil o&nbsp;180°, zavoláme jeho metodu `turn()` s&nbsp;parametrem `180`:
```java
medved.turn(180);
```

Výše uvedené metody mají všichni aktéři Greenfootu, psát je tedy nemusíme. Můžeme si ale přidat svoje vlastní metody.
Zápis metod jsme probrali již na začátku učebnice. Naše metody ale zatím neměli žádné parametry ani nevraceli žádný výsledek (návratovou hodnotu). Přitom ale spousta metod Greenfootu parametry potřebuje. Například při volání metod: `move(5)` nebo `turn(180)` musíme zadat parametr – v&nbsp;tomto případě číselnou hodnotu. Stejně tak z&nbsp;Greenfootu známe metody, které vrací výsledek (návratovou hodnotu). Například když zavoláme metodu `getX()`, nebo `getMouseInfo()`, výsledkem bude pozice X&nbsp;daného objektu, resp. objekt, popisující polohu a&nbsp;události myši. Zbývá nám tedy vysvětlit si, jak zapsat metody s&nbsp;parametry a&nbsp;návratovými hodnotami. 

## Metoda – základní syntaxe

Na začátku jsme se seznámili se základním zápisem metody. Ostatně metody používáme už od úplného začátku.
Pokud se někde v&nbsp;kódu vyskytuje úkol, sestávající z&nbsp;více příkazů, můžeme si připravit metodu, která celý postup provede v jednom kroku.

```java
public void nazevMetody()
{
	// Posloupnost příkazů: Co má metoda dělat...
}
```

Podívejme se ale podrobněji, jaké možnost při zápisu metod máme.

## Metoda s parametry
Začneme situací, kdy potřebujeme metodě doplnit nějaké parametry. Například chceme napsat metodu „přesuň“ třídy „Panáček“, která přesune panáčka na zadanou pozici. Potřebujeme tedy, aby uživatel při volání metody zapsal cílové souřadnice.
Parametry metody:
 - Zapíšeme do závorek za název metody. 
 - Vždy uvádíme datový typ parametru a&nbsp;název parametru. 
 - Parametr může být jeden, nebo jich může být více.
 - Parametry mezi sebou oddělujeme je čárkou. 

```java
public void nazevMetody(Typ1 nazevParametru1, Typ2 nazev2,...)
{
	// Posloupnost příkazů: Co má metoda dělat...
	// Hodnoty parametrů můžeme používat – například:
	if ( nazevParametru1 == nějaká hodnota ) { ... }
}
```

Příklad: Přesun panáčka jen na levé polovině obrazovky
Zapišme metodu „přesuň se“ třídy „Panáček“. Metoda dostane číselné parametry – souřadnice _x_;a&nbsp;_y_. Metoda otestuje, jestli je hodnota x&nbsp;v levé polovině obrazovky. Pokud je, přesune panáčka. Pokud je nová souřadnice v&nbsp;pravé polovině obrazovky, zastaví se panáček v&nbsp;polovině obrazovky.

```java
public void presunSe(int cilX, int cilY)
{
	int polovina =  this.getWorld().getWidth/2;
	int novaX;
	if (cilX >= polovina) 
	{
		novaX = polovina;
	} else {
		novaX = cilX;
	}
	this.setLocation(novaX, cilY);
}
```

### Úkol 1: Cedule
Vytvořte aktéra, který bude zobrazovat zadané texty.
 - Třída aktéra se bude jmenovat „Cedule“.
 - Ve třídě „Cedule“ bude metoda „zobraz text“ s&nbsp;jedním textovým parametrem.
 - Při spuštění metody „zobraz text“ si aktér nastaví jako obrázek zadaný text.
 - Při vytvoření instance se (v konstruktoru) zavolá metoda „zobraz text“ s&nbsp;parametrem „Čekám na text...“.

<details><summary>Řešení úkolu</summary>

```java
import greenfoot.*;

/**
 * Kapitola Metoda s parametry – úkol 1 – Cedule.
 * 
 * @author Martin Šimůnek 
 * @version 2020-04-24
 */

public class Cedule extends Actor
{
    public Cedule()
    {
        this.zobrazText("Čekám na text...");
    }
    
    public void zobrazText(String coZobrazit) 
    {
        GreenfootImage obrazek;
        obrazek = new GreenfootImage(
                        coZobrazit, 20, Color.RED, Color.YELLOW);
        this.setImage(obrazek);
    }
}
```

</details>

### Úkol 2: Metoda pro umisťování aktérů

Vytvořte nový projekt Greenfootu. Ve třídě `MyWorld` připravte metodu „umísti a&nbsp;otoč“, která dostane dva číselné parametry – souřadnice _x_ a&nbsp;_y_ – a&nbsp;provede následující kroky:
    • Vytvoří nového aktéra třídy letadlo.
    • Otočí aktéra o&nbsp;90 °.
    • Umístí aktéra na zadané souřadnice.

## Konstruktor s parametry

Stejně jako mohou mít parametry metody, může mít parametr i&nbsp;konstruktor. Parametry konstruktoru zapisujeme úplně stejně jako u&nbsp;metod:
```java
public NázevTřídy(Typ1 nazevParametru1, Typ2 nazevParametru2,...)
{
	Posloupnost příkazů, které se provedou při vytvoření instance. 
}
```

### Příklad: Krmící se slon

Vytvořme aktéra, který bude reprezentovat krmícího se slona. Při vytvoření vždy zadáme rychlost, jakou se slon bude krmit. Krmení bude probíhat tak, že v&nbsp;pravidelných intervalech budeme měnit obrázek slona – jednou s&nbsp;chobotem nahoru, podruhé s&nbsp;chobotem dolů.
Rychlost změny obrázku zadáme při vytvoření instance jako parametr konstruktoru.

```java
public class KrmiciSeSlon extends Actor
{
    int delkaIntervalu;
    int stav = 0;
    boolean zvednutyChobot = true;
    
    public void KrmiciSeSlon(int delkaIntervalu) 
    {
        this.delkaIntervalu = delkaIntervalu;
    }    
    
    public void act()
    {
        this.stav++;
        if (this.stav >= this.delkaIntervalu)
        {
            this.stav = 0;
            this.zmenObrazek();
        }
    }
    
    public void zmenObrazek()
    {
        if (this.zvednutyChobot)
        {
            this.zvednutyChobot = false;
            this.setImage("elephant.png");
        }
        else
        {
            this.zvednutyChobot = true;
            this.setImage("elephant2.png");
        }
    }
}
```

## Pojmenování parametrů konstruktoru

V&nbsp;konstruktoru často nastává situace, kdy pomocí parametru nastavujeme hodnotu nějakého atributu. Celkem běžně se přitom stává, že název parametru se shoduje s&nbsp;názvem atributu. V&nbsp;takovém případě je potřeba použít identifikátor `this`, protože jinak bychom nerozlišili mezi parametrem a&nbsp;atributem:

```java
public class Hroch
{
    String jmeno;
    int vaha;
    public Hroch(String jmeno, int vaha)
    {
        this.jmeno = jmeno; 
        // Identifikátor this zde musí být uveden.
        this.vaha = vaha;
    }
}
```

Samozřejmě ti nic nebrání pojmenovat si parametry jinak. Pak se tomuto problému vyhneš. V&nbsp;praxi se ale běžně parametry konstruktoru pojmenovávají stejně jako odpovídající atributy:

```java
public class Hroch
{

    String jmeno;
    int vaha;

    public Hroch(String jmenoHrocha, int vahaHrocha)
    {
        this.jmeno = jmenoHrocha; 
        // Identifikátor this zde můžeme vynechat.
        this.vaha = vahaHrocha;
    }
}
```

## Metoda s návratovou hodnotou

Metoda může vracet výsledek. Opět tuto situaci velmi dobře známe ze standardních metod Greenfootu. Například když chceme zjistit souřadnici X&nbsp;aktuální polohy aktéra, zavoláme: `this.getX()`. Metoda nám pak vrací celé číslo – souřadnici&nbsp;X. Zatím jsme ale takové hodnoty neuměli zapsat. Nyní se to naučíme.

Pokud má metoda vracet nějaký výsledek, pak místo slovíčka `void` uvedeme datový typ výsledku, který bude metoda vracet:

```java
public NávratovýTyp NázevMetody()
{
	// Posloupnost příkazů: Co má metoda dělat...
	return hodnotaKterouVracime;
}
```

Slovíčko `void` v&nbsp;hlavičce metody vlastně znamená, že metoda žádný výsledek nevrací. V&nbsp;programovacím jazyce C, ze kterého syntaxe Javy vychází dokonce existoval datový typ `void` – nedefinovaná hodnota.

### Příklad: Hladový medvěd

Vytvořte aktéra Greenfootu – medvěda. Medvěd bude mít číselný atribut „hlad“, který bude mít hodnotu `1` – `10`. Na začátku bude hlad nastaven na&nbsp;`1`. Dále bude mít medvěd metodu „je hladový“, která vrátí „pravda“, pokud je hodnota atributu „hlad“ větší než `7`.

```java
public class Medved {
    int hlad = 1;
    public boolean jeHladovy()
    {
        return this.hlad > 7;
    }
}
```

### Úkol 1: Vlevo nebo vpravo

Vytvořte aktéra Greenfootu, který bude mít místo obrázku text „vlevo“ nebo „vpravo“ podle toho, na které straně obrazovky se bude nacházet. 

Aktér:
 - se bude pohybovat spolu s&nbsp;kurzorem myši.
 - V&nbsp;metodě act se zjistí, jestli aktuální souřadnice je menší než polovina obrazovky (`this.getWorld().getWidth()/2`).
 - Pokud je aktuální souřadnice X&nbsp;menší, nastaví se jako obrázek aktéra text „vlevo“, v&nbsp;opačném případě se nastaví text „vpravo“.

<details><summary>Řešení úkolu: Vlevo nebo vpravo</summary>

```java
import greenfoot.*;

/**
 * Kapitola Metoda s návratovou hodnotou – Úkol 1 Vlevo nebo vpravo.
 * 
 * @author Martin Šimůnek 
 * @version 2020-04-24
 */

public class VlevoVpravo extends Actor
{
    boolean minuleVlevo = true;
    // Tady si uložím, na které polovině obrazovky jsem byl dosud.
    
    public boolean jsemVlevo()
    {
        boolean vysledek = true;
        World svet = this.getWorld();
        if (svet != null)
        {
            // Pokud jsem ve světě, zjistím, zda vlevo od poloviny:
            vysledek = this.getX() < svet.getWidth()/2;
        }
        return vysledek;
    }
    


    public void act() 
    {
        MouseInfo mi = Greenfoot.getMouseInfo();
        if (mi != null)
        {

            this.setLocation(mi.getX(), mi.getY());

            boolean nyniVlevo = this.jsemVlevo();

            // Pokud jsem se přesunul na jinou polovinu, změň obrázek:
            if (this.minuleVlevo != nyniVlevo) {
                this.upravText(nyniVlevo);
                // Ulož si změněnou polohu do atributu minuleVlevo:
                this.minuleVlevo = nyniVlevo;
            }
        }
    }    
    
    public void upravText(boolean jsemVlevo) {
        String text;
        if (jsemVlevo) {
            text = "<<<< vlevo";
        } else {
            text = "vpravo >>>>";
        }
        this.setImage(new GreenfootImage(
                           text, 20, Color.RED, Color.YELLOW));
    }
```

</details>

## Metoda s parametry a návratovou hodnotou

Parametry a&nbsp;návratová hodnota jdou samozřejmě libovolně kombinovat. Metoda může mít zároveň libovolný počet parametrů a&nbsp;zároveň vracet návratovou hodnotu.

```java
public NávratovýTyp NázevMetody(Typ1 nazev1, Typ2 nazev2,...)
{
	Posloupnost příkazů: Co má metoda dělat...
	return hodnotaKterouVracime;
}
```

### Příklad: Vzdálenost k bodu

Vytvořte metodu „vzdálenost k&nbsp;bodu“, která bude vracet jako výsledek (návratovou hodnotu) vzdálenost aktéra od cílového bodu. Souřadnice cílového bodu metoda dostane jako parametry. Metoda bude vracet desetinné číslo.

Při výpočtu použijeme Pythagorovu větu pro délku přepony pravoúhlého trojúhelníku, kde jednotlivé odvěsny budou vzdálenost na ose X a&nbsp;vzdálenost na ose Y.

```java
/** Spočítá vzdálenost aktéra od bodu (cilX, cilY). */
public double vzdalenostKBodu(int cilX, int cilY)
{
    int deltaX = cilX – this.getX();
    int deltaY = cilY – this.getY();
    double vzdalenost = Math.sqrt(deltaX*deltaX + deltaY*deltaY);
    // Funkce Math.sqrt(číslo) počítá odmocninu ze zadaného čísla.
    return vzdalenost;
}
```

## Vyzkoušej si!

### Úkol – na papíře:
a) Vytvořte metodu „počítadlo“. 

    Bude mít parametry:
    1. _číslo_... do kolika má napočítat (od jedničky),
    2. _text_... vždy vypíše text + pořadí.

    Příklad výstupu: 
    Pokud dostane parametry:
    `3` a `Karel` 
    => vypíše: 
    `Karel 1` 
    `Karel 2`
    `Karel 3`

b) Zapište volání metody „počítadlo“ s&nbsp;parametry `3` a&nbsp;`Karel`.

