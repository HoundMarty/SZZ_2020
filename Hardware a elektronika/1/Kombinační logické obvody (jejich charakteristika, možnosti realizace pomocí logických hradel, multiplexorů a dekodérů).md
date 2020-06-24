# Kombinační logické obvody

Jsou to takové logické obvody, která okamžitě reagují na vstup. Jinými slovy neberou potaz v historii, nemají paměť. Skladají se pouze z logických hradel (AND,OR,NAND) a neobsahují zpětnou vazbu. Jakoukoliv implementaci je možné vyjádřit pomocí hradel NAND a invertorů. To se dá odůvodnit přes tzv. duální tvrzení (duální tvrzení - výsledek operace se nezmění, pokud invertujeme vstupy, výstupy i operaci (or↔and, tedy A or B = not(A) nand not(B))). NAND se používá, protože je konstrukčně nejjednodušší (AND je NAND s invertorem). Vyplýva to z možnosti zapsat A OR B = NOT(A) NAND NOT(B). Hradlo NAND je mozne použít jako invertor, pokud se připojí na oba vstupy stejný signál (ale je to „drahé“).

* kombinační obvody nemají zpětnou vazbu (a tedy ani paměť)
* reagují na vstup téměř okamžitě patřičnou úpravou výstupu (pouze fyziklní limity)
* skládají se z log. hradel, vše se dá udělat pomocí NANDů díky duálnímu tvrzení booleovy algebry: A or B = not(A) nand not(B), např AND se implementuje jako not(NAND), NAND lze použít i jako invertor, ale přímé použití invertoru je „levnější“
* kodér vs dekodér: kódování z jednoho do druhého a naopak. Například kód 1 z N na binární číslo (běžně má kodér 2n vstupů a n výstupů, dekodér naopak)
* multiplexor vs demultiplexor: výběr jednoho signálu z mnoha vs poslání vstupu na jeden z výstupů, má adresní vodiče, vnitřně využívá dekodér (jak multiplexor, tak demultiplexor)
* sčítačka: jednobitová poloviční: XOR a AND, výstup z XORu je výsledek, z ANDu je carry
* úplná sčítačka: dvě poloviční za sebou, znát schéma! (výsledek je prostě součet těch 3 vstupů, tedy A, B a C<sub>in</sub>, vyšší bit výsledku je C<sub>out</sub>, nižší S)

###### Logické hradla
![Logické hradla](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/log_hradla_znaceni.gif?raw=true "Log. hradla")


###### Pravdivostní tabulky hradel
![pst_tabulky](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/hradla_tabulka_pravdivostni.png?raw=true "pst_tabulky_log_hradel")


## Binární sčítačka
#### Poloviční
![polo_scitacka](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/polo_scitacka.png?raw=true "polo_scitacka")

A,B jsou vstupy

S je výsledná suma

C je carry bit

| A | B | S | C |
|:-:|:-:|:-:|:-:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

#### Úplná
![uplna_scitacka](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/scitacka.png?raw=true "uplna_scitacka")

| A | B | C<sub>in</sub> | S | C<sub>out</sub> |
|:-:|:-:| :-: |:-:| :-:  |
| 0 |	0 |	 0  |	0	| 0    |
| 0	| 1 |	 0  |	1	| 0    |
| 1	| 0 |	 0  |	1	| 0    |
| 1	| 1 |	 0  | 0	| 1    |
| 0	| 0 |	 1	| 1	| 0    |
| 0	| 1 |	 1	| 0	| 1    |
| 1	| 0 |	 1	| 0	| 1    |
| 1	| 1	|  1	| 1	| 1    |

## Multiplexor
Z několika vstupů vybírá jeden. Realizace pomocí dekodéru a AND hradel a OR hradla. S<sub>0</sub> a S<sub>1</sub> jsou bity „adresy“, podle které se vybírá jeden ze vstupů I<sub>0–3</sub> a posílá se na výstup. Počet vstupů je 2<sup>n</sup>, kde n je počet bitů adresy. To protože je 2n kombinací hodnot bitů adresy.

![Multipexor](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/multiplexor.png?raw=true "Multiplexor")

## Demultiplexor
Jeden vstup přiřadí do správného výstupu. Dekodér a AND hradla. Opět zde figuruje adresa S<sub>0 – n</sub>, tentokrát její rozsah určuje počet výstupů. Princip je přesně opačný, než u multiplexoru.

![Demultipexor](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/demultiplexor.png?raw=true "Demultiplexor")
