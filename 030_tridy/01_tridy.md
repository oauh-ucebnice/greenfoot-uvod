# Třídy a objekty

Jak už jsme si ukázali dříve, objektové programování popisuje realitu jako skupinu objektů, které si posílají zprávy.

## Třída

Třída popisuje, jaké vlastnosti mají všechny objekty této třídy. Třeba jaký obrázek je přiřazen všem letadlům, nebo jaké metody mají všechny letadla (na jaké zprávy umí objekty třídy letadlo reagovat).

Základní zápis třídy (syntaxe):
```java
public class NazevTridy
{
   // Popis třídy – metody, atributy, konstruktory,...
}
```

## Pravidla pro názvy tříd:
1. Názvy tříd by vždy měly začínat velkými písmenem! 
2. Pokud se název třídy skládá z více slov, začíná vždy další slovo opět velkým písmenem.
3. Doporučujeme nepoužívat znaky s diakritickými znaménky (háčky, čárky, kroužky).
4. V názvu tříd nesmí být mezery, pomlčky, ani jiné znaky kromě písmen a číslic (může tam být i podtržítko, ale nedoporučujeme to)!

Příklady správně zapsaných názvů tříd jsou například: `Ryba`, `ZavodniAuto`, `Panacek`, `ExplozeVelka`, `ExplozeMala`, `Kyticka`, `RuzovyDort`,…

## Objekty – instance tříd
Třída je jen popis vlastností. Třeba třída Velbloud popisuje, jak má v naší hře vypadat velbloud. Sama třída ale nic nevykonává. Pokud má velbloud chodit zleva doprava, třída jen říká, „CO“ má velbloud dělat. Musíme ale do hry umístit objekty (skutečné velbloudy), kteří budou po obrazovce chodit.

<!-- begin:Akce-->
> Vyzkoušej si!
> Tohle už bys měl znát: 
> 1. Vytvoř nový projekt.
> 2. Připrav aktéra (třeba třídu Beruška) 
> 3. Vytvoř několik objektů třídy Beruška a rozmísti je na obrazovce.
> 4. Poté uprav popis třídy Beruška (metodu `act()`) tak, aby se všechny berušky stále pohybovaly vpřed. 
> 5. Znovu přidej na plochu několik berušek. (Předtím při úpravě předchozí berušky zmizely.)
<!-- end:Akce-->
