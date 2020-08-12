
# Pojem pravděpodobnost, náhodný jev. Podmíněná pravděpodobnost, nezávislost. Náhodná veličina – diskrétní, spojitá a jejich použití. Střední hodnota, kvantily, rozptyl

## Pojem pravděpodobnost

#### Klasická definice pravděpodobnosti
Historicky nejstarší pokus o definici pravděpodobnosti, definice klasické pravděpodobnosti, převádí problém na pojem stejné možnosti výskytu dvou jevů, ten považuje za základní a dále ho nezkoumá. Předpokládá, že výsledkem náhodného pokusu (generujícího stav jevu A) může být jen konečně mnoho - např. n - stejně pravděpodobných elementárních stavů (viz házení kostkou). Zavádí pojem příznivého stavu jevu A; všech příznivých stavů (označme jejich počet m) není rozhodně více než n, nemusí však být žádný. Pravděpodobnost p(A) jevu A pak definuje jako podíl počtu příznivých stavů a počtu všech stavů:

![klasicka definice pst](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/klasicka%20def%20pst.gif)

Klasické pojetí pravděpodobnosti je dodnes nejčastěji používané pro řešení rozsáhlé řady úloh především z oblasti technických a přírodních věd. Nedává však návod, jak postupovat při nesplnění podmínky stejné možnosti výskytu dvou jevů.

#### Geometrická definice pravděpodobnosti
Jedním z prvních pokusů o rozšíření klasické teorie pravděpodobnosti i na případ nekonečné množiny elementárních stavů je zavedení geometrické pravděpodobnosti. Základní myšlenka, která dala takto chápané pravděpodobnosti název, je tato: Mějme nějakou oblast (např. v rovině) G a v ní jako její podmnožinu jinou oblast g. Vybíráme náhodně z oblasti G bod a zkoumáme, s jakou pravděpodobností p patří tento bod i do oblasti g. V geometrickém pojetí pravděpodobnosti se tato pravděpodobnost p klade rovna hodnotě

![geometricka definice pst](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/geometricka%20definice%20pst.gif)

kde m je míra oblasti - v rovině např. plošný obsah.

Geometrické pojetí pravděpodobnosti řeší úspěšně řadu úloh, postupem času však byla ukázána nemožnost jeho obecné aplikace.

**Existují i další definice pravděpodobnosti -> Axiomatická nebo Bayesova**

## Náhodný jev
**Základní prostor** &Omega; (elementárních jevů) je množinou všech možných výsledků náhodného pokusu.

**Náhodný jev A** je libovolná podmnožina základního prostoru (A). Pro náhodné jevy platí algebraické zákony a rovnosti stejné jako pro množiny.

## Podmíněná pravděpodobnost
![podminěná pst](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/podminena%20pst.gif)

**P(A|B)** čteme jako "pravděpodobnost, že nastane jev A nastal-li jev B"

###### Příklad:
Celostátní pozorování manželských párů ukázalo, že pravidelně sleduje určitý pořad 30% všech manželek a 50% všech manželů. Zároveň bylo zjištěno, že jestliže pořad sleduje manželka, pak podíl manželů, kteří pořad také sledují, je 60%. Jaká je pravděpodobnost, že u náhodně vybraného manželského páru.
Jaká je PST, že budou pořad sledovat oba manželé?

![příklad podmíněná pst](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/priklad%20podminena%20pst.gif)

### Nezávistlost

![nezávistlost náhodných jevů](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/nezavistlost%20nahodnych%20jevu.PNG)

# Náhodná veličina
**Náhodná veličina** – funkce, která každému výsledku náhodného pokusu přiřadí reálné číslo. Je to matematický model popisující více či méně dobře realitu, který vytváříme, jestliže chceme zpracovávat výsledky náhodného pokusu.
 
* počet vadných výrobků mezi tisíci výrobky
* doba do poruchy žárovky
* roční spotřeba energie v domácnosti

## Diskrétní náhodná veličina
Náhodná veličina X má **diskrétní rozdělení pravděpodobnosti** právě tehdy, když nabývá nejvýše spočetně mnoha hodnot tak, že:

![diskrétní náhodná veličina - rozdělení](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/diskretni%20nahodna%20velicina%20-%20dis%20rozdeleni%20pst.gif)

Funkce **P(X=x<sub>i</sub>)=P(x<sub>i</sub>)** je **pravděpodobnostní funkce**, může být zadána:
* předpisem
* grafem
* tabulkou
* můžeme dopočítat

Distribuční funkci diskrétní náhodné veličiny můžeme vyjádřit pomocí pravděpodobnostní funkce jako

![distribuční funkce diskrétní náhodné veličiny](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/distribucni%20funkce%20dis%20nahodne%20veliciny.gif)

tzn. jako součet pravděpodobností těch x<sub>i</sub>, které jsou menší než x.

## Spojitá náhodná veličina
Spojitá náhodná veličina nabývá jakékoliv hodnoty v určitém intervalu.

