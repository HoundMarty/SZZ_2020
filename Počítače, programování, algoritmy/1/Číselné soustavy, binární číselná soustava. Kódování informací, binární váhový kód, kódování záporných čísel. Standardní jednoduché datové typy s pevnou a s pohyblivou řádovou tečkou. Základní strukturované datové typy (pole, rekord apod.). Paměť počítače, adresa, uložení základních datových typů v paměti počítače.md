# Číselné soustavy, binární číselná soustava. Kódování informací, binární váhový kód, kódování záporných čísel. Standardní jednoduché datové typy s pevnou a s pohyblivou řádovou tečkou. Základní strukturované datové typy (pole, rekord apod.). Paměť počítače, adresa, uložení základních datových typů v paměti počítače.

## Číselné soustavy

Libovolné kladné číslo **F(Z)** lze zapsa pomocí mnohočlenu ve tvaru:

![vzorec číselné soustavy]()

Kde **F(Z)** je číslo vyjádřené v číselné soustavě o základu **Z**, **a<sub>i</sub>** jsou číselné koeficienty, **m** je počet řádových míst. Pro jednoduchost v číselných soustavách zapisujeme pouze koeficienty **a<sub>i</sub>**. V praxi potom často řešíme problém, který koeficient vyjadřuje nejvyšší řád a který nejnižší. Zpravidla se řídíme konvencí, která říká, že nejvyšší řád je vlevo a nejnižší vpravo. U dvojkové soustavy nejvyšší řád označujeme jako **MSB**(Most Significant Bit) a nejnižší řád jako **LSB**(Least Significant Bit).

![tabulka vyjádření 0-15]()

#### Vyjádřete číslo 275(10) binárně.
Číslo v desítkové soustavě 275(10) je možno vyjádřit jako **2&times;10<sup>2</sup>+7&times;10<sup>1</sup>+5&times;10<sup>0</sup>**. Číslo 1101(2) ve dvojkové soustavě vyjadřuje hodnotu **1&times;2<sup>3</sup>+1&times;2<sup>2</sup>+0&times;2<sup>1</sup>+1&times;2<sup>0</sup>**, neboť předpokládáme, že MSB je vlevo.

## Záporná čísla
V případě, kdy chceme rozlišit kladná a záporná čísla ve dvojkové soustavě použijeme znaménko mínus stejně jako v soustavě dekadické. Pro kódování znaménka v počítači se používají různé způsoby. Nejčastěji jsou to tyto tři:
* Vyhrazení znaménkového bitu
* Přičtění konstanty
* Pomocí dvojkového doplňku

V případě kdy jeden bit(většinou ten nejvýznamnější) představuje znaménko, ostatní bity představují absolutní hodnotu daného čísla. Konvence říká, že v případě, že znaménkový bit je roven jedné, jedná se o záporné číslo a je-li roven nule, jedná se o číslo kladné. Znaménkový bit nám snižuje rozsah čísel, která můžeme zakódovat daným počtem bitů. Např. pomocí osmi bitů můžeme vyjádřit čísla v rozsahu -127 až 127 (přičemž máme kladnou a zápornou nulu).

### Přičtění konstanty
Při využití tohoto způsobu kódování záporných binárních čísel dochází k posouvání nuly tím, že ke každému číslu přičteme vhodnou konstantu. Např. pro čísla v rozsahu -127 až 128 bychom volili konstantu 127.

### Dvojkový doplněk
Dvojkový doplněk binárního čísla získáme jako jeho inverzi zvětšenou o jedničku. Kódování záporných čísel pomocí dvojkového doplňku nám umožňuje snadno provádět odčítání ve dvojkové soustavě(přičtením záporného čísla).

Rozsah čísel, který je možné pomocí dvojkového doplňku zakódovat je (-2<sup>n-1</sup>) až (2<sup>n-1</sup>-1), to znamená, že pomocí např. 4bitů můžeme zakódovat čísla v rozsahu: -8 až 7, pomocí 8mi bitů čísla v rozsahu: -128 až 127 atd.

![dvojkový doplněk]()

Při převodu kladného čísla do dvojkového doplňku musíme nejprve kladné binární číslo doplnit zleva nulami na správný počet bitů(např. říslo 5<sub>10</sub> = 101<sub>2</sub> doplníme na 0101<sub>2</sub>). Vpřípadě, že tam neučiníme, nedostaneme správnou hodnotu.

#### Vypočtěte dvojkový doplněk k číslu 1110<sub>2</sub> = 14<sub>10</sub>.
Číslo 1110<sub>2</sub> nejprve doplníme na potřebný počet bitů (pro vyjádření čísla -14 potřebujeme 5 bitů) a tím dostaneme 01110. Inverze tohoto čísla je 10001. Přičtením jednotky v LSB dostaneme číslo 10010<sub>2</sub> = -14<sub>10</sub> 

## Standardní datové typy

![rozdělení datových typů]()

#### Datové typy s pevnou řádovou tečkou
Jsou to nejjednodušší celočísené typy, pomocí kterých lze vyjadřovat celé čísla. Můžeme je dále rozdělit na **znaménkové** a **neznaménkové**. Rozsah hodnot, které pomocí nich lze vyjádřit je dán jejich velikostí v paměti(počtem bitů).

|    Typ   |                Rozsah               |
|:--------:|:-----------------------------------:|
|   Byte   |               0 .. 255              |
|   Word   |              0 .. 65535             |
|   Dword  |        0 .. 2<sup>32</sup>-1        |
| ShortInt |             -128 .. 127             |
|  Integer |           -32768 .. 23767           |
|  LongInt | -2<sup>32</sup> .. 2<sup>23</sup>-1 |
|   Char   |  0 .. 255 - odkaz do ASCII tbaulky  |

###### Ukládání dat do paměti
Pro zjednodušení budeme o paměti uvažovat jako o tabulce, která má na každém řádku osmibitové číslo (může být až 64bit... podle velikosti sběrnice). Adresa 0 je nahoře a každý další řádek má adresu o 1 vyšší. Překladače vyšších programovacích jazyků ukládají promměnné postupně do paměti v pořadí, jak jsou deklarovány. Pro promměné které mají velikost jeden bajt(Byte, Char) je situace jednoduchá. vícebajtové promměné se ukládají do paměti postupně od nejméně významného bajtu (LSB).

![ukládání dat do paměti]()

#### Datové typy s plovoucí řádovou tečkou
Abychom mohli pracovat s reálnými čísly ve dvojkové soustavě, můžeme využít stejný přístup jako v desítkové soustavě. To znamené, že číslo nejprve převedeme do dvojkové soustavy a případně ještě do normalizovaného tvaru.

Převeďte číslo 2,1234 &times; 10<sup>2</sup> do dvojkové soustavy v normalizovaném tvaru.

Nejprve si převedeme desítkové číslo z normalizovaného tvaru do tvaru, který je vhodný pro převod do dvojkové soustavy (to je tvar bez exponentu). Provedeme převod celé i desetinné části a nakonec přepíšeme výsledek do normalizovaného tvaru ve dvojkové soustavě (přidáme exponent tak, aby před desetinou čárkou bylo pouze číslo 1).

2,1234 &times; 10<sup>3</sup> = 2123,4 = 100001001011,011001100<sub>2</sub> = 1,00001001011011001100<sub>2</sub> &times; 2 <sup>11</sup>

Pokud už máme reálné číslo ve dvojkové soustavě v normalizovaném tvaru, můžeme se zabývat problémeme jak ho uložit do paměti počítače. Ve skutečnosti totiž musíme uložit tři různé informace - znaménko, absolutní hodnotu a exponent. Musíme si zvolit způsob kódování znaménka u exponentu, počet bitů u exponentu a počet bitů na vlastní číslo (mantisu). Tím určíme rozsah a přesnost čísel, která můžeme takto kódovat.
Je zřejmé, že možností je velmi mnoho. Ve vyšších programovacích jazicích se používají hlavně tyto tři datové typy: **Single, Double (někdy označen jako Real), Extended.**

##### Datový typ single
