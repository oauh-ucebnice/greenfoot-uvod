# Atributy tříd

Pokud proměnnou přiřadíme nějaké třídě, mluvíme o ní jako o atributu třídy. Například všechny ryby budou mít rychlost (každá bude mít svou rychlost).

## Zápis atributu

Postupujeme úplně stejně jako při vytváření proměnných, jen proměnnou píšeme přímo pod hlavičku třídy:
```java
public class NazevTridy
{
    DatovyTypAtributu nazevAtributu;
}
```

Příklady:
```java
public class Mys extends Actor
{
    int rychlost;
    
    public void act()
    {
        // …
    }
}
```