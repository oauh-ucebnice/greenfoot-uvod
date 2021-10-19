# Metody &mdash; základní zápis

_Metoda_ popisuje posloupnost akcí, které má objekt nějaké třídy vykonat, když ho o to požádáme (když „zavoláme metodu“). Při psaní metody používáme metody, které už počítač umí: například ty, které jsou součástí frameworku Greenfoot, nebo ty, které jsme si vytvořili sami.

## Základní zápis (syntaxe) metody

Nejběžnější metody se zapisují takto:
```java
public void nazevMetody()
{
	// Posloupnost příkazů: Co má metoda dělat...
}
```

Chceme-li později takto připravenou metodu spustit, zapíšeme její název, následovaný závorkami:

```java
komuToRikam.nazevMetody();
```

Na začátku ovládáme většinou ten objekt, se kterým pracujeme. Budeme tedy obvykle psát:

```java
this.nazevMetody();
```

My už jsme jednu metodu viděli – byla to metoda `act()` v aktérovi `Ryba`. Připomeňme si, jak metoda vypadala:
```java
public void act() 
{
        this.move(2);
}  
```  

Metoda se jmenovala `act` a obsahovala jediný příkaz – posuň se vpřed o dva pixely. Tuto metodu nemusíme sami _spouštět_ („volat“), protože ji volá Greenfoot sám. 

Později si ukážeme, že zápis metody může být i složitější. Podrobnější vysvětlení najdete v kapitole Chyba: zdroj odkazu nenalezen.

## Zápis vlastní metody

Zkusme si nyní vytvořit novou metodu a zavolat ji. Vytvoříme metodu s názvem „otoč se“, která způsobí, že se ryba otočí čelem vzad.
Dejte si pozor, ať novou metodu zapíšete mezi složené závorky, které ohraničují třídu, ale zároveň ji nepište do složených závorek ohraničujících metodu act().
```java
    public void otocSe() 
    {
          this.turn(180);
    }  
```  

Abychom nově vytvořenou metodu využili, zkusíme ji zavolat v metodě `act()`. Metodu `act()` tedy upravíme:
```java
    public void act() 
    {
          this.move(2);
          this.otocSe();
    }
```

Problém je, že po této úpravě se ryba bude neustále točit. Lepší by tedy bylo upravit metodu `act()` ještě dále:
```java
    public void act() 
    {
          move(2);
          String klavesa = Greenfoot.getKey();
          if ("space".equals(klavesa)) 
          {
              otocSe();
          }
    }
```

Nyní se bude ryba otáčet vždycky, když zmáčkneme mezerník (space). Museli jsme tu použít podmíněný příkaz. Ten si vysvětlíme za chvíli v kapitole Podmíněný příkaz.

Všimněte si, že názvy metod v Javě na rozdíl od názvů tříd začínají malým písmenem. Ostatní pravidla platí stejně jako u názvů tříd: každé další slovo začíná velkým písmenem, v názvu nesmí být mezery ani pomlčky a neměli bychom používat diakritická znaménka (háčky, čárky a kroužky nad písmeny).
