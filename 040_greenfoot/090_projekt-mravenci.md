# Souhrnná úloha – Mravenci v letadle

Na začátek rozmísti na hrací ploše několik mravenců. Mravenci budou lozit stále dokola po dráze ve tvaru čtverce. Při kliknutí na mravence se mravenec otočí o&nbsp;180&nbsp;°.
Při stisku klávesy „m“ se přidá další mravenec na souřadnice myši. 

Přidejte aktéra letadlo: bude uprostřed obrazovky a&nbsp;obrázek bude zmenšený. Letadlo budeme ovládat šipkami. Při přeletu letadla nad mravencem mravenec nasedne do letadla (zmizí z&nbsp;hrací plochy).

<details><summary>Postup</summary>

Třída „mravenec“
1. Vytvoř aktéra s&nbsp;názvem „Mravenec“. Mravenec bude mít atribut „počet kroků“, celé číslo, na začátku 0.
2. Mravenec se bude pohybovat vpřed. Po každém kroku zvýší hodnotu proměnné „počet kroků“ o&nbsp;jedničku.
3. Pokud je „počet kroků“ větší nebo roven 10, otočí se o&nbsp;90&nbsp;stupňů a&nbsp;hodnotu „počet kroků“ nastaví na 0.
4. Pokud jsme na mravence kliknuli myší, otočí se o&nbsp;180&nbsp;°.

Svět – třída „mraveniště“
5. Zapiš svět Greenfootu s&nbsp;názvem „Mraveniště“.
6. V&nbsp;konstruktoru umísti na plochu 10 mravenců tak, aby byly vodorovně vedle sebe 100 pixelů nad dolním okrajem obrazovky - od levého po pravý okraj. (Použijte cyklus.)
7. Další dva mravence umístěte do levé a&nbsp;pravé části obrazovky 100&nbsp;pixelů od horního a&nbsp;pravého/levého okraje. (Viz obrázek.)
8. Při stisknutí klávesy „m“ zjisti souřadnice myši a&nbsp;na tyto souřadnice umísti nového mravence (stisk klávesy testujte v&nbsp;metodě „act“).

Třída „letadlo“
9. Vytvoř třídu „letadlo“ – nastav jí jako obrázek letadlo, které zmenšíš na 50 % původní velikosti.
10. Letadlo bude zatáčet pomocí šipek doprava a&nbsp;doleva (metoda „turn“) a&nbsp;poletí vpřed stále stejnou rychlostí.
11. Pokud se letadlo dotkne mravence, mravenec využije metodu `getWorld()` a&nbsp;odstraní se ze světa (z&nbsp;hrací plochy) – doplň do třídy mravenec.