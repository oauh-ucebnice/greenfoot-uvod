# Souhrnný úkol – hra Útěk ze ZOO

> POZOR! Toto NENÍ návod pro úplné začátečníky!
>
> Návod na tvorbu hry předpokládá, že jste již zvládli základní pojmy objektového programování! 
> Návod je záměrně psán tak, abyste si museli vybavit a&nbsp;tím si procvičili správný zápis tříd, metod, vytváření proměnných, vytváření instancí atd.
>
> Nepouštějte se do tohoto úkolu, dokud tyto pojmy nemáte zvládnuté z&nbsp;předchozích kapitol!

## Motiv hry: Ze ZOO utíkají klokani...

Na ploše se budou náhodně objevovat figurky klokana (či jiné zvíře). Kliknutím myši figurku „ulovíme“ a&nbsp;získáme za ni body. Pokud na figurku neklikneme po stanovenou dobu, figurka zmizí a&nbsp;my naopak body ztrácíme (klokan definitivně utekl).

## Co se máte naučit:

U tohoto úkolu už uvádíme jen rámcový popis na úrovni toho, jak bývají zadané programátorské projekty. Vaším úkolem je vzpomenout si nebo dohledat konkrétní postup řešení a řešení naprogramovat.

## Postup – rámcový:

 1. Vytvořte v&nbsp;Greenfootu aktéra (figurku) – bude to ten, který se ve hře bude objevovat a&nbsp;na kterého budeme klikat. Zvolte vhodný obrázek.

 2. Figurce nastav v&nbsp;metodě `act()` reakci na kliknutí. Využij metody `Greenfoot.mouseClicked(this)`. V&nbsp;reakci na kliknutí figurku odstraňte ze světa.

 3. Vytvořte prostředí hry – svět.

    Ve světě vytvořte metodu „Přidej figurku“, která na náhodné místo přidá figurku.
    V&nbsp;konstruktoru světa zavolejte několikrát metodu „přidej figurku“.

    V&nbsp;metodě `act()` světa s&nbsp;malou pravděpodobností zavolej metodu _Přidej figurku_. Vygenerujte náhodné číslo od `0` do `99` a&nbsp;pokud je číslo menší než například `5`, volej metodu.

 4. Vytvořte aktéra, který se bude pohybovat zároveň s&nbsp;myší (využijte jeho metodu `act()` k&nbsp;tomu, aby se neustále přesunoval na aktuální pozici myši. Jako obrázek můžete nastavit třeba obrázek sítě či lasa.

## Možná rozšíření:
 
 1. Přidejte do hry počítadlo bodů – při každém mizení figurky zvyšte počitadlo o&nbsp;jedničku.

    Návod na počitadlo bodů najdete třeba na [e-MiS.cz  Greenfoot: řešení častých úloh](http://mis.e-mis.cz/index.php/Greenfoot:_%C5%98e%C5%A1en%C3%AD_%C4%8Dast%C3%BDch_%C3%BAloh).

 2. Figurky se mohou z&nbsp;místa, kde se objeví, dále pohybovat. Mohou zmizet třeba když dojedou na okraj obrazovky.