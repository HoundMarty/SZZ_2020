[//]: <> (Zdroje)
[//]: <> (https://www.itnetwork.cz/navrh/algoritmy/algoritmy-grafove/uvod-do-teorie-grafu)
[//]: <> (http://user.mendelu.cz/marik/wiki/inzmat/slidy/grafy/)
[//]: <> (http://brkos.math.muni.cz/files/download/Teorie%20graf%C5%AF.pdf)
[//]: <> (https://teorie-grafu.cz/uvod/vyuziti-grafu.php#priklad1)
[//]: <> (https://homel.vsb.cz/~kov16/files/skriptum_teorie_grafu.pdf)

# Základy teorie grafů – orientovaný, neorientovaný. Reprezentace grafu a s tím související datové struktury. Sled, tah, cesta, kružnice. Vzdálenosti v grafu, poloměr a průměr grafu.

## Definice Grafu
Mějme nějaký graf, který je tvořen pomocí puntíků a čar. Puntíky jsou vrcholy grafu a čáry jsou jeho hrany. Hrana musí být zakončena vrcholem z každé strany, jinak to není hrana. 

Formálnější definice by zněla takto: Mějme graf G = (V, E), kde (V, E) je uspořádaná dvojice prvků takových, že V je množina vrcholů grafu G a E je množina hran, které spojují vrcholy z V.

Příklad grafu (izomorfního grafu). Tyto grafy jsou identické.

![Izomorfní graf](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/izomorfni_graf.PNG)

### Orientovaný vs neorientovaný
Orientovaný graf je graf, který má uspořádané dvojice vrcholů.

![Orientovaný vs neorientovaný](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/orientovany_vs_neorientovany.png)

### Vzdálenost
Hrany k sobě mohou mít přiřazené číslo, které si lze představit jako vzdálenost mezi městy nebo např. cenu, kterou musíme zaplatit za průchod hranou. Říkáme, že graf má ohodnocené hrany.

### Poloměr 
Poloměr neb otaké excentricita grafu je vzdálenost vrcholu od dalších vrcholů.

![Poloměr](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/polomer.PNG)

### Průměr
Největší excentricita v grafu se nazývá průměr.

### Reprezentace grafu
Záleží na typu grafu a co s nimi chcete dělat. Ukážeme si dvě nejčastější reprezentace grafu.

#### Matice souslednosti
Pro neorientované grafy budeme mít symetrickou matici, kde Aij = 1 pokud Vi sousedí s Vj a 0 pokud nikoliv. Pro orientované grafy to bude nesymetrické. To, že sousedí Vi s Vj neznamená, že sousedí Vj s Vi. Tedy to, že víte, jak se dostat z X do Y po jednosměrce neznamená, že to umíte i nazpátek.

![Matice souslednosti](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/matice_souslednosti.PNG)

#### Reprezentace v poli
Jednoduché typy grafů, např. binární stromy, tj. kde každý uzel má právě 2 potomky kromě listů, se dají efektivně uložit v obyčejném poli. Víte, že vrchol na pozici i má potomky na pozici 2i + 1 a 2i + 2. Zde máme příklad binárního stromu, konkrétně haldy. Halda je datová struktura, kde předek stromu je vždy menší než potomek (kořen je minimum).

![Uložení v poli](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/ulozeni_v_poli.PNG)

### Typy grafů

![Definice cestování grafem](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/definice_cest_v_grafu.PNG)
![Cestovani grafem](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/cestovani_priklad.PNG)

#### Cesta
Cesta je posloupnost vrcholů a hran, kde existuje pouze jeden způsob, jak se dostat z vrcholu V do vrcholu U

![Cesta](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/cesta.PNG)

#### Kružnice
Kružnici můžeme definovat jako cestu, jejíž koncové vrcholy spojíme do jednoho.

![Kružnice](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Matematika/imgs/kruznice.PNG)
