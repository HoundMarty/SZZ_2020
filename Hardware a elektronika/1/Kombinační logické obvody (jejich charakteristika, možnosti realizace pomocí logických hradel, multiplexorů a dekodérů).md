# Kombinační logické obvody

Jsou to takové logické obvody, která okamžitě reagují na vstup. Jinými slovy neberou potaz v historii, nemají paměť. Skladají se pouze z logických hradel (AND,OR,NAND) a neobsahují zpětnou vazbu. Jakoukoliv implementaci je možné vyjádřit pomocí hradel NAND a invertorů. To se dá odůvodnit přes tzv. duální tvrzení (duální tvrzení - výsledek operace se nezmění, pokud invertujeme vstupy, výstupy i operaci (or↔and, tedy A or B = not(A) nand not(B))). NAND se používá, protože je konstrukčně nejjednodušší (AND je NAND s invertorem). Vyplýva to z možnosti zapsat A OR B = NOT(A) NAND NOT(B). Hradlo NAND je mozne použít jako invertor, pokud se připojí na oba vstupy stejný signál (ale je to „drahé“).

* kombinační obvody nemají zpětnou vazbu (a tedy ani paměť)
* reagují na vstup téměř okamžitě patřičnou úpravou výstupu (pouze fyziklní limity)
* skládají se z log. hradel, vše se dá udělat pomocí NANDů díky duálnímu tvrzení booleovy algebry: A or B = not(A) nand not(B), např AND se implementuje jako not(NAND), NAND lze použít i jako invertor, ale přímé použití invertoru je „levnější“
* kodér vs dekodér: kódování z jednoho do druhého a naopak. Například kód 1 z N na binární číslo (běžně má kodér 2n vstupů a n výstupů, dekodér naopak)
* multiplexor vs demultiplexor: výběr jednoho signálu z mnoha vs poslání vstupu na jeden z výstupů, má adresní vodiče, vnitřně využívá dekodér (jak multiplexor, tak demultiplexor)
* sčítačka: jednobitová poloviční: XOR a AND, výstup z XORu je výsledek, z ANDu je carry
* úplná sčítačka: dvě poloviční za sebou, znát schéma! (výsledek je prostě součet těch 3 vstupů, tedy A, B a Cin, vyšší bit výsledku je Cout, nižší S)

###### Logické hradla
![Logické hradla](https://github.com/HoundMarty/SZZ_2020/blob/master/Hardware%20a%20elektronika/1/log_hradla_znaceni.gif?raw=true "Log. hradla")
