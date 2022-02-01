# Vyzkoušej si – projekt „Zažeň kraba!“

## Zadání
Vytvoř hru v&nbsp;Greenfootu, ve které budou na začátku na obrazovce dva objekty: _hlídač_ a _krab_. Hra bude určena pro dva hráče.

### Popis _hlídače_
- Úkolem hlídače je zajistit, aby se krab nedostal k&nbsp;levému okraji obrazovky.
- Hlídač je trvale umístěn na levém okraji obrazovky uprostřed. Nepohybuje se, ale otáčí se směrem ke kurzoru myši.
- Při stisknutí mezerníku vystřelí hlídač _kapku vody_ (modrou kuličku) ve směru, kterým je otočen.

### Popis _kraba_
- Kraba ovládá druhý hráč pomocí směrových kláves (šipky) a snaží se dosáhnout levého okraje obrazovky.

### _Kapka vody_
- Pohybuje se stále vpřed ve směru, kterým byla vystřelena.

## Dobrovolné: Dokončení hry

Chceš-li, dokonči hru tak, aby se dala hrát:

- Pokud se _kapka vody_ dotkne kraba, krab se přesune na pravý okraj obrazovky (souřadnice Y se nezmění).
- Pokud se _kapka vody_ dotkne okraje obrazovky či kraba, zmizí.
- Pokud _hlídač_ vystřelí kapku vody, dalších několik kol hry nemůže kapky odpalovat (například 20 kol).
- Nastav rychlost pohybu kraba, rychlost pohybu kapky a délku minimálního intervalu mezi vystřelením kapek tak, aby oba hráči měli přiměřeně stejnou šanci uspět.

## Výzva

- Při zásahu kraba se krab posune o&nbsp;400 bodů ve směru letu kapky. (Nezůstává tedy na stejné souřadnici Y.)
- Hlídač může kapku vody odpalovat kdykoli, má ale k&nbsp;dispozici pouze omezený počet kapek vody. Jakmile je vyčerpá, musí čekat, než některá ze stávajících kapek zmizí.
