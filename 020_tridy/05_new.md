# Vytvoření objektu v kódu

## Vytvoření objektu

Třída popisuje, jaké vlastnosti (atributy) mají mít objekty této třídy a na jaké zprávy mají umět reagovat (jaké mají metody). Třída sama je ale pouze popis. Abychom mohli skutečně něco provádět, musíme vytvořit skutečný objekt (instanci) této třídy.

Třída je takový technický výkres. Architekt může nakreslit výkres domu. Je tam přesně popsáno, jak bude dům velký, z jakých materiálů bude, kde budou dveře a kde okna… Ale pořád je to jen výkres. Abychom se mohli schovat před deštěm, musí přijít zedníci a dům podle výkresu sestavit.

Tedy, pod výkres se před deštěm můžeme na chvíli schovat také, ale to by nám dlouho nevydrželo… ;)

Dosud jsme objekty (instance tříd) vytvářeli ručně kliknutím pravým tlačítkem. Teď je čas zařídit, aby se aktéři ve světě objevovali sami.

Syntaxe:
```java
new NazevTridy()
```
Příklad:
```java
new Kaktus();
new Panacek();
```

Výsledkem volání tohoto příkazu bude vytvoření nového objektu třídy `Kaktus` či `Panacek`.

## Uložení objektu do proměnné

Nově vytvořený objekt musíme někam uložit (jinak by se vytvořil, ale my bychom se k němu už nedostali). Velmi často tedy nejprve vytvoříme proměnnou, do které nově vytvořený objekt uložíme:

Syntaxe:
```java
NazevTridy nazevPromenne = new NazevTridy();
```

Příklad:
```java
Kaktus k = new Kaktus();
Panacek karel = new Panacek();
```

Proměnná už samozřejmě může existovat, nebo objekt můžeme uložit jako hodnotu atributu některé třídy. Pak proměnnou nemusíme vytvářet:

```java
public MyWorld()
{
	Kaktus k;
	for (int i = 0; i < 3; i++)
	{
		k = new Kaktus();
		this.addObject(k, i*100, i*200);
	}
}
```

## Použití objektu bez vytvoření proměnné

Můžeme ale nově vytvořený objekt hned použít, aniž bychom si ho ukládali do proměnné. Dá se tedy napsat přímo:

```java
public MyWorld()
{
	for (int i = 0; i < 3; i++)
	{
		this.addObject(new Kaktus(), i*100, i*200);
	}
}
```

Ve skutečnosti se zde proměnná stejně vytvoří, jen ji překladač programovacího jazyka vyrobí automaticky. Ušetřili jsme tedy jen jeden řádek textu, nikoli však kód počítače.
