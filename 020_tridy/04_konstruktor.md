# Konstruktor

_Konstruktor_ je speciální metoda, která se spustí vždy při vytvoření nového objektu dané třídy.

> Například když vytvářím nového panáčka (nový objekt třídy Panáček), tak se zavolá konstruktor třídy `Panáček`.

Úkolem konstruktoru je obvykle zejména nastavit správné počáteční hodnoty atributů nově vytvářeného objektu.

Například při vytváření panáčka se má správně nastavit jeho rychlost, směr a jméno.

Syntaxe:
```java
public NazevTridy()
{
	// Posloupnost příkazů: co se má stát při vytvoření instance...
}
```

Syntaxe konstruktoru s parametry:
```java
public NazevTridy(Typ1 parametr1, Typ2 parametr2,...)
{
	// Posloupnost příkazů: co se má stát při vytvoření instance...
}
```