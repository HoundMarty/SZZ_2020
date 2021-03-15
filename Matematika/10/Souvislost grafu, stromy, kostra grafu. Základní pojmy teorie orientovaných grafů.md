
# Souvislost grafu, stromy, kostra grafu. Základní pojmy teorie orientovaných grafů.

### Definice Souvislost
Řekneme, že vrchol v je dosažitelný z vrcholu u v grafu G, jestliže v G existuje (u, v)-sled. Graf G je souvislý,
jestliže pro každou dvojici vrcholů u, v ∈ V (G) existuje (u, v)-sled. V opačném případě je graf nesouvislý.
Můžeme říci, že graf je souvislý, jestliže každý vrchol v je dosažitelný z každého vrcholu u, případně
z jednoho pevně zvoleného vrcholu u. V Kapitole 5. budeme dokonce rozlišovat „ jak mocÿ je graf souvislý.
Jestliže graf není souvislý, tak je možno jej rozdělit na několik souvislých indukovaných podgrafů.

### Definice Komponenta grafu
Řekneme, že L je komponenta grafu G, jestliže je L souvislý podgraf grafu G a současně pro každý souvislý
podgraf W grafu G platí, že W je podgraf L a nebo vrcholové množiny podgrafů W a L jsou disjunktní.
Počet komponent grafu G značíme ω(G).

![Souvislost a Komponenty]()

## Nejprve podáme formální definici orientovaného grafu.
### Definice Digraf
Mějme neprázdnou množinu vrcholů V . Dvojice (V, A), kde A je nějaká podmnožina kartézského součinu
V × V (množina uspořádaných dvojic prvků z V ), se nazývá orientovaný graf D nebo stručně digraf 15 D.
Prvkům množiny A říkáme orientované hrany, stručně hrany případně šípy. Jsou-li u, v dva různé
vrcholy digrafu D, tak orientovanou hranu (u, v) budeme značit stručně uv. Vrchol u se nazývá výchozí
nebo počáteční a v koncový vrchol hrany uv. (Orientovanou) smyčkou rozumíme orientovanou hranu, která
má stejný počáteční i koncový vrchol. Hrany uv a vu se nazývají opačně orientované nebo jen opačné hrany.

![Orientovaný graf]()

Pojmy incidence, sousednost a nezávislost se zavedou analogicky jako pro jednoduché grafy.
#### Upozorníme
na jeden důležitý detail. Jestliže digraf obsahuje orientovanou hranu uv a neobsahuje opačnou hranu vu, tak
vrchol v považujeme za sousední s vrcholem u, ale vrchol u není sousední s vrcholem v (vrchol v je dosažitelný
z vrcholu u, ale naopak ne).

![orientovany_graf]()

![cesty cykly dosažitelnost]()
