# Sekvenční obvody

Na rozdíl od [kombinačních logických](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/Kombina%C4%8Dn%C3%AD%20logick%C3%A9%20obvody%20(jejich%20charakteristika%2C%20mo%C5%BEnosti%20realizace%20pomoc%C3%AD%20logick%C3%BDch%20hradel%2C%20multiplexor%C5%AF%20a%20dekod%C3%A9r%C5%AF).md)  obvodů mají zpětnou vazbu.

## KO - Klopné obvody
Mají dva stavy a mezi nimi se přepínají.

### Astabilní
Sám se překlápí mezi stavy, generuje periodický obdélníkový signál. Perioda každého stavu je t = ln(2)RC, celková perioda je tedy T = t1 + t2 = ln(2) R2 C1 + ln(2) R3 C2.

Princip: Jeden z tranzistorů má o maličko nižší potřebné napětí na bázi, aby se otevřel. Tzn. na začátku se jeden tranzistor (řekněme Q1) otevře dřív. V tu chvíli se C1 začíná vybíjet a C2 naopak nabíjet. Jakmile se C1 vybije, otočí se na něm polarita a nabíjí se opačným směrem. To způsobí napětí na Q2, který se následně otevře, což zařídí vybíjení C2 a následné uzavření Q1. V tu chvíli se proces se otáčí.

![Astabilní](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/astabilni.png "Astabilní KO")

### Monostabilní
Má jeden stabilní stav, pro přechod do druhého je potřeba jej nakopnout, po čase t = ln(2) R2 C1 se zase vrátí zpět do svého stabilního stavu.

![Monostabilní](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/monostabilni.png "Monostabilní KO")

### Bistabilní

Má oba stavy stabilní, pro přechod je potřeba do něj kopnout vždy. Lze jej tedy použít jako jednoduchou paměť.

![Bistabilní](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/bistabilni.png "Bistabilní KO")

### RS
Reset/Set

| R |	S |	Akce             | Q                   | Q<sub>další</sub> |
|:-:|:-:|:----------------:|:-------------------:|:-----------------:|
| 0	| 0	| Ponechá stav     | Q<sub>minulý</sub>  | Q                 |
| 0	| 1	| Set	             | 0	                 | 1                 |
| 1	| 0	| Reset	           | 1	                 | 0                 |
| 1	| 1	| Nedefinovaný stav| Nedefinovaný stav   | Nedefinovaný stav |

![RS KO](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/rs_ko.gif "RS KO")

### T
Toggle, přepínač. Změna se provede pouze pokud přijde signál hodin.

| T | Q | Q<sub>další</sub> |     Akce     |
|:-:|:-:|:-----------------:|:------------:|
| 0 | 0 |    0              | Ponechá stav |
| 0 | 1 |    1              | Ponechá stav |
| 1 | 0 |    1              |   Přepnutí   |
| 1 | 1 |    0              |   Přepnutí   |

### JK
Kombinace RS a T. Odstraňuje nedefinovaný stav u RS (J = S, K = R) při kterém funguje jako T.

| J | K |  Q<sub>další</sub>  |     Akce     |
|:-:|:-:|:-------------------:|:------------:|
| 0 | 0 |  Q<sub>minulý</sub> | Ponechá stav |
| 0 | 1 |     0               |     Reset    |
| 1 | 0 |     1               |      Set     |
| 1 | 1 | !Q<sub>minulý</sub> |   Přepnutí   |

### D
Data – je-li na D 1, nastaví se při impulzu z hodin na 1, je-li 0, nastaví se na 0. Bez impulzu hodin stav vstup D ignoruje a pamatuje si předchozí stav.

| Hodiny | D |    Q               |
|:------:|:-:|:------------------:|
|    1   | 0 |    0               |
|    1   | 1 |    1               |
|    0   |   | Q<sub>minulý</sub> |

## Čítače
Nejjednodušeji je to řada D klopných obvodů které mají vždy svůj invertovaný výstup připojený na svůj vlastní vstup, a jako vstup hodin používají výstup předchozího klopného obvodu (kromě prvního, ten má normální hodinový vstup). Kromě binárního čítače fungují také jako děličky frekvencí.

![citace](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/citace.jpg "Čítač pomocí D KO")

## Registry
Pro rozšíření okruhu [Více info ohledně registrů](https://learnabout-electronics.org/Digital/dig57.php)

Posuvný registr je skupina klopných obvodů, která má propojené vstupy a výstupy tak, že s náběžnou hranou hodinového signálu jsou data (bity) synchronně posunuty o jeden klopný obvod. Jeho základním použitím je převod paralelních binárních dat na sériová nebo naopak.

Posuvné registry je možno realizovat z RS klopných obvodů a zpožďovacích linek, tento způsob se však již dlouho nepoužívá a posuvné registry se dodávají jako samostatné integrované obvody, nebo jsou samy vnitřní součástí složitějších obvodů.

### SIPO
Zkratkou SIPO se označují posuvné registry se sériovým vstupem a paralelním výstupem (Serial Input Paralel Output). Posuvný registr má jeden vstup dat, jeden hodinový vstup a řadu výstupů. Tento typ posuvného registru se hodí zejména k dekódování dat ze sériové linky - například RS232 nebo SPI. dalším využitím je buzení segmentových displejů po seriové lince. Příkladem tohoto typu registru je obvod 74HC164, což je samostatný integrovaný osmibitový SIPO posuvný registr.

![4bit_SIPO_reg](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/4bit_posuvny_registr_SIPO.png "4bit SIPO registr")

![Reakce na impuls](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/posuvny_registr_cas_diagram.png "Posuvný registr - časový diagram")
### PISO
PISO jsou posuvné registry s paralelním vstupem a seriovým výstupem (Parallel Input Serial Output). Slouží předevší ke kódování paralelních binárních dat do sériové podoby. Příkladem tohoto typu registru je obvod 74HC166, což je samostatný integrovaný osmibitový PISO posuvný registr.

### Kruhový čítač
Kruhový čítač je zvláštním použitím posuvného registru, kdy je poslední bit registru přiveden zpět na vstup registru. Jako výchozí stav je do posuvného registru možno zapsat stavovou informaci, jako přednastavení bitů, a tato je pak posouvána v kruhu. Kruhové čítače se používají jako hodinové generátory, elektronické kontaktní spínače a řídicí jednotky.

## Stavové outomaty
Sekvenční automat je šestice: A=(X,Y,Q,q0,P,V) kde:

1. X je vstupní abeceda (množina hodnot vstupního vektoru)
2. Y je výstupní abeceda (množina hodnot výstupního vektoru)
3. Q je vnitřní abeceda (množina hodnot vektoru vnitřního stavu)
4. q0 je podmnožinou Q, je to počáteční stav, ze kterého se vždy startuje
5. P je přechodová funkce, která některým dvojicím z X * Q přirazuje prvek z Q a platí q<sub>(i+1)</sub> = P(x<sub>i</sub>,q<sub>i</sub>), pro i = 0,1,2,…,n
5. V je výstupní funkce, která některým dvojicím z X * Q přirazuje prvek z Y.

Existují dva způsoby definice výstupní funkce: Mealyho a Moorův.

### Mealyho
Výstup je funkcí vstupu i stavu.

![Mealy_mat](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/mealy.PNG "Mealyho automat")

### Tabulka přechodů a výstupů Mealyho automatu
| Stav Q<sub>t</sub> | Vstup N | budoucí stav Q<sub>t+1</sub> | výstup Z |
|:------------------:|:-------:|:----------------------------:|:--------:|
|         S0         |    0    |              S1              |     0    |
|         S0         |    1    |              S0              |     0    |
|         S1         |    0    |              S2              |     0    |
|         S1         |    1    |              S3              |     0    |
|         S2         |    0    |              S2              |     0    |
|         S2         |    1    |              S0              |     1    |
|         S3         |    0    |              S0              |     0    |
|         S3         |    1    |              S0              |     1    |

### Moorův
Výstup je funkcí pouze stavu.

![Moor_mat](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/2/moor.PNG "Moorův automat")

### Tabulka přechodů a výstupůMoorova automatu
|    |  1 |  0 | Z |
|:--:|:--:|:--:|:-:|
| S0 | S0 | S1 | 0 |
| S1 | S3 | S2 | 0 |
| S2 | S4 | S2 | 0 |
| S3 | S0 | S4 | 0 |
| S4 | S0 | S1 | 1 |

#### Návrh asynchronních sekvenčních systémů
* Nutno zajistit, aby při přechodu do nějakého stavu byl tento stabilní (změna vstupu, která způsobila přechod, nezpůsobí další přechod)
* Nutno odstranit hazardy, které by mohly způsobit nežádoucí změnu stavu
* Používat jen u jednoduchých zapojení, kde se dá intuitivně vyhnout nežádoucím jevům


# Shrnutí
* mají zpětnou vazbu (paměť, stav)
* klopné obvody: astabilní, monostabilní, bistabilní podle v kolika stavech jsou stabilní
* astabilní generuje hodiny, monostabilní krátký impulsy a má jeden vstup, bistabilní má set a reset
* všechny tři jsou multivibrátory (přepíná mezi více stavama, prostě je to název)
* klopné obvody mají 2 výstupy: normální a invertovaný
* RS má nedefinovaný stav (R=1, S=1), staví se ze dvou NANDů
* T je přepínač, ke změně dochází jenom při náběžné hraně hodinového signálu
* JK je RS, avšak nemá nedefinovaný stav, místo něj ten stav funguje jako T (tj. na vstupu má i hodiny)
* D nastaví na výstup to, co je na vstupu s hodinovým impulsem
* čítač je řada D klopných obvodů, vstupem je jejich vlastní invertovaný výstup ⇒ delička frekvence (dělí dvěma), jako hodiny používá výstup z předchozího D KO, výstupy reprezentují jednotlivé bity čísla
* paralelní registr je několik D KO vedle sebe, posuvný registr je několik D KO zapojených za sebe (lze ho zapojit jako čítač)
* stavový automat je typ zapojení, který má několik stavů a může mezi nima přecházet pomocí vstupů - jestli výstup závisí jenom na stavu je to Moorův automat, jestli závisí i na vstupech je to Mealyho automat
* automaty se reprezentují pomocí pravdivostních tabulek nebo grafů přechodů, při implementaci se na stavy používají KO, na výstupy kombinační log. obvody (cyklus + switch)
* astabilní KO se nějakou dobu inicializuje/stabilizuje a generuje periodický obdélníkový signál, využívá kondenzátory
* monostabilní generuje jeden obdélníkový impuls, odpovídá době vybíjení kondenzátoru
* z posuvnýho registru se čítač dělá zapojením posledního invertovaného výstupu na první vstup (dá se tím udělat třeba dělení frekvence deseti)
* sekvenční automat je šestice obsahující množinu hodnot vstupů, množinu hodnot výstupů, množinu hodnot stavů, počáteční stav, přechodovou funkci pro změnu stavu, výstupní funkce pro zjištení výstupu

