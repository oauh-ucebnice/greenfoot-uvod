# Vyzkoušej si – projekt Sněžení (1. část)

Na začátku hry umístěte na horní okraj obrazovky 2 vločky (aktéry Greenfootu). 
 - K umisťování vloček si ve světě Grennfootu připravte metodu „umísti vločku“. Vločka bude umístěna na náhodné pozici na ose X.

Atributy vločky:
 - „Aktivní“… logická hodnota, na začátku „pravda“.
Chování vločky: 
Dokud má atribut „aktivní“ hodnotu „pravda“:
 - Vločka padá dolů.
 - Jakmile se vločka dotkne okraje obrazovky (`isAtEdge()`), zavolá metodu „umísti vločku“ světa a nastaví atribut „aktivní“ na „nepravda“.
Pro volání metody „umísti vločku“ je třeba nejprve získat aktuální svět:
    ```java
    MyWorld svet = (MyWorld) this.getWorld();
    ```

