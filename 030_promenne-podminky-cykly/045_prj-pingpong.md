# Vyzkoušej si – projekt Ping pong

## Zadání
Vytvoř hru v&nbsp;Greenfootu, ve které budou na začátku na obrazovce dva objekty &mdash; například míčky.
- První z&nbsp;objektů se bude pohybovat stále zleva doprava a zpět na obrazovce. (Posunuje se doprava, dokud nedorazí na okraj obrazovky. Tam se otočí a&nbsp;posunuje se zpět.)
- Druhý objekt se bude pohybovat shora dolů a&nbsp;zpět s&nbsp;tím, že při dotyku horního okraje obrazovky zrychlí a při dotyku spodního okraje zpomalí.

<details><summary>Nápověda: Otočení míčku</summary>

Pro otočení míčku hned při jeho vytvoření můžeš u&nbsp;druhého míčku využít konstruktor třídy („metodu“, která se zavolá při vytvoření objektu dané třídy). 
Konkrétně u&nbsp;druhého míčku chceš, aby se jednou hned po vytvoření objektu otočil směrem dolů.
    
U&nbsp;aktérů se sice konstruktor nevytváří automaticky, ale můžete si ho zapsat ručně. Najdi si [kapitolu o&nbsp;konstruktorech](../020_tridy/04_konstruktor.md).

</details>

## Výzva: Odraz od okraje obrazovky

1. Zkus vytvořit třetí objekt, který se bude na začátku pohybovat šikmo vzhůru. Při dotyku okraje obrazovky se „odrazí“ podle pravidla, že úhel dopadu je roven úhlu odrazu.
2. Zkus první dva aktéry realizovat jednou třídou. Míček se bude chovat různě podle toho, jestli se dotýká horního, dolního, nebo jiného okraje obrazovky. (V&nbsp;tomto případě nejspíš nevyužiješ konstruktor míčku a budeš míček otáčet při jeho umístění do světa ručně.)
3. S&nbsp;využitím metody `getRotation()` zkus všechny tři míčky realizovat jednou jedinou třídou.