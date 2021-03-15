
# Stromy a jejich procházení. Prohledávání grafu do hloubky a do šířky. Hledání kostry grafu. Hledání nejkratších cest v grafu.

### Definice Stromu
--> Strom je souvislý graf neobsahující kružnici.

nebo také 

--> Graf se nazývá acyklický, jestliže žádný jeho podgraf není cyklus. Acyklický graf se nazývá les.
Souvislý acyklický graf se nazývá strom

Z definice stromu vyplývá, že mezi každými dvěma vrcholy existuje právě jedna cesta (alespoň jedna cesta, protože je souvislý; nemůže nastat situace více cest, protože díky neexistenci kružnice není možné zvolit "objížďku").

![Stromy](https://user-images.githubusercontent.com/29363626/111161344-59537980-859b-11eb-92ef-d033e8dbd7cc.png)

### Průchod stromu
![Průchod stromu](https://user-images.githubusercontent.com/29363626/111162542-87858900-859c-11eb-84c1-010af4146909.png)

### DFS
![Průchod do hloubky](https://user-images.githubusercontent.com/29363626/111165241-17c4cd80-859f-11eb-8a35-ce0ab40c9566.png)

### BFS
![image](https://user-images.githubusercontent.com/29363626/111165480-5eb2c300-859f-11eb-9e59-bf79a7c0d3e6.png)

### Kostra grafu
Úloha hledání minimální kostry nám popisuje, jak máme spojit všechny vrcholy grafu "co nejlevněji" - hranami s nejnižší váhou (ohodnocením). Praktickým využitím mohou být například rozvody elektřiny mezi městy - jak propojit města co nejmenší délkou elektrického vedení.

#### Popis Kruskalova algoritmu
* Všechny hrany si seřadíme podle velikosti (vzestupně - od hrany s nejmenší váhou).
* Hranu s nejmenší váhou použijeme jako první hranu kostry.
* Pokud jsme tím už vytvořili kostru (graf měl jen dva vrcholy), končíme. V opačném případě vezmeme hranu s druhou nejmenší váhou.
* POZOR! Pokud by nám v grafu vznikla kružnice, hranu nepoužijeme.
* Opakujeme minulý krok, dokud vznikající kostra nespojí všechny vrcholy grafu.

![Kostra grafu - Kruskal](https://user-images.githubusercontent.com/29363626/111164172-19da5c80-859e-11eb-8a0a-29699f2e3057.png)

#### Jarníkův algoritmus
![Kostra grafu - Jarník](https://user-images.githubusercontent.com/29363626/111164486-6a51ba00-859e-11eb-8ccd-14d813086a6e.png)

### Nejkratší cesta v grafu
Nejkratší cestu v grafu můžeme najít pomocí více algoritmů... Uvádím video k algoritmu od Dijkstry jakožto první svého druhu.

https://www.youtube.com/watch?v=_lHSawdgXpI

