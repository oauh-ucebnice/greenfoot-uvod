# Souhrnný úkol – hra Autíčko

> POZOR! Toto NENÍ návod pro úplné začátečníky!
>
> Návod na tvorbu hry předpokládá, že jste již zvládli základní pojmy objektového programování! Návod je záměrně psán tak, abyste si museli vybavit a tím si procvičili správný zápis tříd, metod, vytváření proměnných, vytváření instancí atd.

## Motiv hry:

Naše hra bude spočívat v tom, že hráč bude ovládat autíčko, které se bude vyhýbat balvanům a přitom nesmí vyjet mimo silnici. Pokud hráč vyjede mimo silnici nebo narazí do balvanu, dochází k poškození autíčka. Jakmile poškození autíčka přesáhne stanovenou mez, hra končí.

## Co se máš naučit:

Máš si důkladně zopakovat základní programátorské konstrukce (cykly, podmínky, metody,…) a jejich zápis v Javě. 

## Možná rozšíření:
 1. Přidej do hry bonus – opravu automobilu

    Zvolte vhodný pohyb, může například padat stejně jako kameny.

    Pokud se autíčko bonusu dotkne, bonus umizí a&nbsp;sníží se poškození autíčka. 
    
    Jako obrázek můžeš použít buď barevné kuličky, nebo například obrázek plochého klíče či šroubováku.

## Nápověda

details><summary>Nápověda s postupem</summary>

## Postup – první část: Projekt a pomocné třídy

 1. Vytvořte v Greenfootu nový projekt (scenario).

 2. Vytvořte třídu s názvem _Strom_ – bude potomkem (_subclass_) třídy `Actor`.

        Metoda `act` třídy _Strom_ bude provádět následující akce:
        1) Posune strom o jeden dílek dolů: setLocation(getX(), getY()+1)
        2) Pokud se dotýká okraje (this.isAtEdge()), nastaví souřadnici Y na 50:
        setLocation(getX(), 50)
        Stromy se budou stále posunovat dolů. Pokud narazí na okraj obrazovky, přesunou se zpět na horní okraj (na stejné souřadnici X).
  3. Vytvořte třídu s názvem Game Over – bude potomkem (subclass) třídy Actor.
        Konstruktor třídy bude bez parametrů a v jeho kódu:

        1) Vytvořte proměnnou s názvem Obrázek GameOver, datový typ bude `GreenfootImage`.

        2) Uložte do proměnné Obrázek GameOver novou instanci třídy `GreenfootImage`. Konstruktor třídy `GreenfootImage` má čtyři parametry: 

            ```java
            new GreenfootImage("Game Over", 30, Color.RED, Color.BLACK);
            ```
        
        3) Zavolejte metodu _set image_ a předejte jí jako parametr hodnotu proměnné _Obrázek GameOver_.

            (Nastaví jako obrázek aktéra text „Game Over“ velikosti 30 bodů. Text bude červený na černém pozadí.)

## Postup – druhá část: svět hry a stromy
 4. Vytvořte třídu s názvem AutíčkoWorld – bude potomkem (subclass) třídy Actor. Jako pozadí nastavte obrázek AutickoPozadi.png z balíčku Resources, který máte k této knize.
 5. V konstruktoru třídy AutíčkoWorld proveďte:
Vytvořte pomocí cyklu 5 instancí třídy Strom a umístěte je do světa na souřadnice:
X náhodné číslo od 0 do 100.
Y náhodné číslo od 0 do souřadnice dolního okraje obrazovky (this.getHeight()).
Postup – třetí část: Třída autíčko
    6. Vytvořte třídu s názvem Autíčko – bude potomkem (subclass) třídy Actor.
Při vytváření třídy zvolte vhodný obrázek.
    7. Třída Autíčko bude mít atribut s názvem Poškození – celé číslo, na začátku nastavte na 0.
    8. Ve třídě Autíčko vytvořte metodu s názvem Poškoď. Metoda bude mít jeden parametr typu celé číslo a bude vracet také celé číslo. Metoda zvýší hodnotu atributu Poškození o hodnotu parametru a jako návratovou hodnotu vrátí výslednou hodnotu parametru Poškození.
    9. Ve třídě Autíčko vytvořte metodu s názvem Posun. Metoda bude mít jeden parametr typu celé číslo. Metoda nevrací žádnou hodnotu.
Metoda posune autíčko v horizontální rovině (ve směru osy X) o počet dílků, který odpovídá hodnotě parametru délka. Pokud je délka větší než 0, posunujeme autíčko doprava, pokud je délka záporná, posunujeme autíčko doleva.
Kód metody bude následující:
this.setLocation(this.getX()+delka, this.getY());
 10. Ve třídě Autíčko vytvořte metodu s názvem Mimo silnici. Metoda nebude mít parametry a bude vracet logickou hodnotu (pravda/nepravda).
    V rámci metody:
    a) vytvořte logickou proměnnou s názvem Výsledek a uložte do ní hodnotu nepravda.
    b) pokud je pozice autíčka (získáte voláním metody getX) větší než 500, uložte do logické proměnné Výsledek hodnotu pravda a autíčko posuňte o 50 bodů doleva voláním metody Posun.
    c) Pokud je pozice autíčka (získáte voláním metody getX) menší než 100, uložte do logické proměnné Výsledek hodnotu pravda a autíčko posuňte o 50 bodů doprava voláním metody Posun.
    d) Vrátí hodnotu logické proměnné Výsledek.
    11. Vytvořte metodu Řízení. Bude bez parametrů, nebude vracet žádnou hodnotu. Kód metody bude následující:

    1) Pokud metoda isKeyDown s textovým parametrem "left" vrací logickou hodnotu pravda, zavolej metodu Posun s parametrem -5.
    2) Pokud metoda isKeyDown s textovým parametrem "right" vrací logickou hodnotu pravda, zavolej metodu Posun s parametrem +5.
        (Reagujeme tím na stisk šipek na klávesnici a posunujeme autíčko vpravo nebo vlevo.)

 12. Vytvořte metodu Test konec hry bez parametrů a bez návratové hodnoty s následujícím kódem:
    Pokud je atribut Poškození větší než 10, spusť:
    World svet = this.getWorld();
    svet.removeObject(this);
    svet.addObject(
            new GameOver(), svet.getWidth()/2, svet.getHeight()/2
        );
 13. V metodě Act autíčka zavolejte metody Řízení a Mimo silnici. Pokud metoda Mimo silnici vrátí logickou hodnotu pravda, pak zavolejte metodu Poškoď s parametrem 1.
    Pak zavolejte metodu Test konec hry.

## Postup – čtvrtá část: umístění autíčka do světa
 14. V konstruktoru třídy AutíčkoWorld proveďte:
    Vytvořte novou instanci třídy Autíčko.
    Spočtěte souřadnice autíčka: X bude polovina šířky světa (this.getWidth()/2), Y bude 50 bodů od dolního okraje obrazovky (this.getHeight()-50).
    Nově vytvořenou instanci autíčka umístěte do světa na pozici X, Y.
 15. V konstruktoru třídy AutíčkoWorld přidejte na hrací plochu 10 instancí třídy Strom. Souřadnice stromů určete takto:
    X: šířka světa minus 100 + náhodné číslo od 0 do 99 (šířku světa získáte voláním metody getWidth).
    Y: náhodné číslo od 0 do výšky světa (výšku světa získáte voláním metody getHeight()).

## Postup – padající balvany
 16. Vytvořte třídu s názvem Balvan – bude potomkem (subclass) třídy Actor.
Třída bude mít atributy Pozice X, Pozice Y, Počítadlo a Rychlost (jsou to celá čísla).
Konstruktor třídy bude mít parametr Šířka světa (celé číslo). Konstruktor nastaví Počítadlo a Pozici Y na 0 a Pozici X na náhodné číslo od 0 do Šířky světa. Atribut Rychlost nastaví na 1. Dále k atributu Rychlost přičte náhodné číslo od 0 do 10.
    17. Třída Balvan bude mít metodu s názvem Naraz do auta. Metoda je bez parametrů, vrací logickou hodnotu. Kód metody je následující:
Auticko kolize = 
    (Auticko) this.getOneIntersectingObject(Auticko.class);
if (kolize != null) 
{
    kolize.poskod(3);
    return true;
}
return false;
(Detekuje kolizi s autíčkem, pokud nastane, poškodí autíčko a vrací „pravda“, jinak vrací „nepravda“.)
    18. V metodě Act třídy Balvan:
1) Zvyšte hodnotu atributu Počítadlo o 1,
2) Pokud je hodnota Počítadlo větší než hodnota atributu Rychlost, nastavte Počítadlo na 0 a zvyšte Pozice Y o 3.
3) Zavolejte metodu Set Location a předejte jí parametry Pozice X a Pozice Y. (Metoda Set Location už existuje, získali jsme ji od třídy Actor).
4) Vytvořte logickou proměnnou s názvem Odstraň.
5) Zavolejte metodu Náraz do auta a výsledek metody uložte do proměnné Odstraň.
6) Pokud je Pozice Y větší nebo rovna výšce světa, do proměnné Odstraň uložte hodnotu „pravda“:
7) Pokud je v proměnné Odstraň logická hodnota „pravda“, odstraňte balvan ze světa:
this.getWorld().removeObject(this)
    19. V metodě Act světa (třídy AutíčkoWorld):
1) Vygenerujte náhodné číslo od 0 do 199.
2) Pokud je náhodné číslo menší než 2, vytvořte nový balvan a umístěte ho do světa na pozici (-100, -100).

</details>
