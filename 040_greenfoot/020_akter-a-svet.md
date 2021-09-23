# Souhrn: Ovládání aktéra a světa

Shrňme si nyní, co můžeme dělat s&nbsp;aktérem Greenfootu (jaké metody můžeme volat):

 - `getX()`, `getY()` &hellip; zjištění aktuální pozice aktéra ve světě

 - `move(pocetKroku)` &hellip; posun o&nbsp;zadaný počet kroků vpřed
 - `turn(uhel)` &hellip; otočení o&nbsp;zadaný úhel vpravo
 - `isAtEdge()` &hellip; vrací „pravda“, pokud je aktér na okraji obrazovky
 - `setLocation(x, y)` &hellip; přesun aktéra na zadanou pozici
 - `setRotation(uhelOtoceni)` &hellip; nastaví otočení aktéra oproti základní pozici
 - `getWorld()` &hellip; vrací svět, ve kterém aktér právě je umístěný

Metody, které můžeme využít u&nbsp;světa:
 - `getWidth()`, `getHeight()` &hellip; zjištění rozměrů světa
 - `addObject(akter, x, y)` &hellip; přidání aktéra do světa
 - `removeObject(akter`) &hellip; vyjmutí aktéra ze světa

Další užitečné funkce v&nbsp;Greenfootu:
 - `Greenfoot.getRandomNumber(limit)` &hellip; Generování náhodných čísel.
 - `Greenfoot.getRandomNumber((max-min+1))+min` &hellip; Generování náhodných čísel z&nbsp;rozsahu `min`...`max`