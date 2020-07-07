# Derivace a diferenciál. Integrál.

Derivace je základní pojem v diferenciálním počtu, má významnou roli například při určování průběhu funkce.

### Co je to derivace?

Derivací funkce získáme směrnici těčny. Jednoduše řečeno, tečna je přímka, která se daného grafu dotýká právě v jednom bodě. Přesná definice níže.

![tečna funkce](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/te%C4%8Dna_funkce.PNG)

Černá křivka je graf funkce *y = x<sup>2</sup>*. Modrá přímka je tečna k této funkci v bodě *D = [1,1]*, označen červeně. Zeleně je vyznačen úhel *&alpha;*, který svírá tečna s osou *x* -> přesněji s kladnou poloosou *x*. Nyní si definujeme pojem směrnice tečny. Směrnice tečny je v tomto obrázku tangens úhlu alfa. Takže směrnice tečny je tangens úhlu, který daná tečna svírá s kladnou poloosou *x*. A tuto směrnici získáme právě pomocí derivací.

Dále rozlišujeme pojmy derivace funkce v bodě a derivace funkce. Derivace funkce v bodě představuje právě směrnici tečny v daném bodě. Derivace funkce je pak jiný funkce, která předepisuje směrnice pro obecný argument *x*.

### Motivace
Pomocí derivace tak umíme spočítat směrnice tečen.

![různé tečny k funkce y=x^2](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/r%C5%AFzn%C3%A9%20te%C4%8Dny%20k%20funkci..PNG)

na obrázku je funkce *y = x<sup>2</sup>* a čtyři vyznačené tečny. Dvě zelené a dvě modré. Funkce *y = x<sup>2</sup>* je na intervalu **(*-&infin;, 0)** klesající, zatímco na intervalu **(0, &infin;)** je rostoucí. Modré tečny, což jsou tečny, která prochází body, které přísluší intervalu, ve kterém funkce roste, svírají s osou úhel menší než 90°. Zatímco zelené tečny svírají s osou úhel, který je větší než 90°. Jak se to projeví do směrnic tečen?

K tomu potřebujeme znát chování funkce tangens. Z následujícího grafu vidíme, že pokud má úhel velikost menší než 90°, pak je hodnota tangensu kladná (modře zvýrazněná část); naopak pokud je úhel větší než 90°, ale menší jak 180°, pak je hodnota tangensu záporná. Závěrem tedy -> Pokud je směrnice (nezapomenout, že směrnice je právě tangens úhlu) tečny v daném bodě kladná, pak je funkce v daném bodě rostoucí, pokud je záporná, pak je klesající.

![průbeh tangens](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/pr%C5%AFb%C4%9Bh%20tangens.PNG)

### Definice
Neř přejdeme ke směrnici samotné tečny, zastavíme se u směrnice sečny. Sečna je přímka, které protíná graf ve dvou bodech. Teď si zkusíme odvodit, jak bychom tuto směrnici počítali.

![sečna funkce](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/se%C4%8Dna%20funkce.PNG)

Máme graf funkce *x<sup>2</sup> + 1* a sečnu *s*, která protíná graf ve dvou bodech **[0,5; 1,25]** a **[2, 5]**. Tyto body jsou zvýrazněné modře. Protože nás nebudou příliš zajímat konkrétní hodnoty, jsou v grafu tyto hodnoty vyznačeny obecně jako *a* a *b* popřípadě *f(a)* a *f(b)*. Přičemž *f(a)* je hodnota funkce *f* v bodě *x = a*. 

Nyní jde o to odvodit, jak vypočítat úhel označený jako &alpha;, tj. úhel, který svírá sečna s osou *x*. Obrázek si nejprve trochu upravíme, abychom tam získali trojúhelník, bude se nám s tím lépe pracovat.

![sečna funkce se zvýrazněným trojůhelníkem](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/se%C4%8Dna%20funkce%20s%20troj%C5%AFheln%C3%ADkem.PNG)

Spojili jsme úsečkou body, ve kterých se sečna protínala s grafem funkce *y = x<sup>2</sup> + 1* a dokreslili jsme na pravoúhlý trojůhelník **ABC**. V čem jsem si pomohli? Úhel označený jako &beta; má totiž stejnou velikost jako úhel &alpha;. Přitom ale známe velikost stran **AB** a **BC**. Platí, že **|AB| = *b* - *a*** (vzdálenost bodu *b* od *a*). Podobně platí, že délka **|BC| = *f(b) - f(a)***. Jak nyný spočítáme velikost úhlu &beta;, respektive &alpha;?

Tangens je poměr protilehlé odvěsny ku přilehlé odvěsně, tedy tangens úhlu &alpha; (&beta;) se rovná poměru velikosti strany **BC** ku velikosti strany **AB**. 

![tangens rovnice](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/tangens%20rovnice.PNG)

Protože směrnice je tangens úhlu, tak jsme tímto vzorcem spočítali směrnici sečny. Jak nám to ale pomůže, když chceme spočítat směrnici tečny? -> Představte si, že budeme k sobě přibližovat body ***A*** a ***C*** tak dlouho, že spolu splynou. Znázornění:

![přiblížení sečen](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/p%C5%99ibl%C3%AD%C5%BEen%C3%AD%20se%C4%8Den.PNG)

Čím více přibližujeme hodní bod průniku tomu spodnímu, tím blíže má sečna k tomu, aby se stala tečnou. Původní sečna/přímka **CA** měla do tečny daleko. Když přiblížíme bod ***C*** bodu ***A***, získáme např. sečnu ***C<sub>1</sub>A***, která je už tečně podobnější. Sečna ***C<sub>2</sub>A*** je ještě více podobnější...

Ve chvíli, kdy oba body průniku splynou v jeden, tj. když by pro nějaký bod ***C<sub>n</sub>*** platilo, že ***C<sub>n</sub> = A***. V tu chvíli máme ze sečny tečnu. Otázkou je, jak spočítat směrnici, protože nemůžeme jen tak odečíst tyto dva body, protože jsou stené...

![tangens body](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/tangens%20body.PNG)

Takto počítat nelze, nedává to smysl. Ne nadarmo jsme k sobě dané body pouze přibližovali. Budeme totiž potřebovat limitu. chceme teď spočítat směrnici tečny v daném bodě **[*a, f(a)*]** a máme k dispozici směrnice všech možných sečen. Budeme tedy postupně počítat směrnice sečen, které budeme přibližovat tak, aby nám vznikla tečna. Budeme tedy přibližovat *b* k *a*. Nemůžeme body přiblížit tak, aby se rovnaly, ale můžeme je přiblížit tak, aby se jejich rozdíl limitně blížil k nule. Tedy budeme *b* přibližovat k *a*, až se limitně budou rovnat. Tedy spočítáme limitu, kdy se *b* blíží k *a*. Takto vypadá zápis.

![tangens limita](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/tangens%20limita.PNG)

Tuto limitu nazýváme derivací funkce *f(x)* v bodě *x = a*. Připomenutí, že &alpha; je rovný úhlu &beta;. Obyčejně nepoužíváme proměnné *a* a *b*, ale hledáme derivaci v bodě *x<sub>0</sub>* a přibližujeme se s bodem *x*. Můžeme zapsat takto:

![tangens limita přes x](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/tangens%20limita%20p%C5%99es%20x.PNG)

Zatím máme, podobně jako u spojitosti funkce, definovanou derivaci v jednom bodě. Pokud máme funkci *f(x)*, která je derivovatelná na otevřeném intervalu **I**, potom hodnoty této derivace definují funkci ***f'(x)***, kterou nazýváme derivace funkce.

Derivaci zapisujeme pomocí čárky v horním indexu...
***(x<sup>2</sup>)' = 2x***

Ve vzorci, který jsme použili před cvhílí, tak můžeme tangens zaměnit za značení derivace:

![derivace limita](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/derivace%20limita.PNG)

Lze definovat i jednostranné derivace...

### Trochu jiná definice

Jiná definice derivace funkce v bodě vypadá takto:

![def derivace](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/def%20derivace.PNG)

Jak se k takové definici dostaneme? Stačí jen trochu pozměnit obrázek, ze kterého jsme vycházeli. Můžeme si totiž vyjádřit vzdálenost bodu *a* od bodu *b* jako *h = b - a*. Tím pádem můžeme bod *b* zapsat jako *a + h*, protože *h* je právě vzádelnost *b* od *a*. Obrázek by vypadal takto:

![jina def derivace](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/jian%20def%20derivace.PNG)

Dole máme body *a* a *a + h*, na ose *y* pak *f(a)* a *f(a + h)*. Nyní opět vytvoříme trojůhelník a spočítáme tangens úhlu &beta;. Jen s tím rozdílem, že délku strany **AB** už máme spočítanou, je to právě *h*.

### Vlastní a nevlastní derivace
I derivace máme vlastní a nevlastní, podobně jako limity funkcí. Co to znamená? Derivace je vlastní, pokud je hodnota derivace v bodě rovna nějakému &#8477;. Derivace je nevlastní, pokud je rovna +&infin; nebo -&infin;. Jak si to představit graficky? Kdy je směrnice "nekonečná"? Začneme lehčí otázkou - jak vypadá tečna, jejíž směrnice se rovná nějakému velkému číslu? Z grafu tangensu je vidět, že pokud je hodnota tangensu vysoká, pak se úhel blíží 90° (pokud se pohybujeme v intervalu **(0, 180)**).

Dalo by se z toho usuzovat, že pokud bude mít funkce v daném bodě nevlastní derivaci, pak bude tečna svírat s osou *x* pravý úhel, bude na ni kolmá. Jak by mohl vypadat graf takové funkce a ve kterém bodě by byla tečna kolmá k ose *x*? Třeba funkce ***y = &#8731;x***:

![tečna funkce k třetí odmocnině](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/te%C4%8Dna%20funkce%20k%20t%C5%99et%C3%AD%20mocnin%C4%9B.PNG)

## Základní vlastnosti
* Funkce má v bodě derivaci, pokud je funkce definována i v &epsilon; okolí tohoto bodu. Pokud by toto okolí neexistovalo, nedopočítáme se limit, přes které je derivace definována.
* Jednoznačnost existence (nebo neexistence) limit nám implikují, že pokud v bodě existuje derivace, je jediná. Žádná funkce nemá v jednom bodě více derivací. **Buď jednu nebo žádnou**.
* Podobně jako u jednostranných limit, pokud má funkce v bodě derivaci, pak se musí derivace zleva a zprava rovnat.
* Občas potřebujeme znát druhou derivaci nebo derivaci vyššího řádu. Funkci zderivujeme podle výšky řádu -> *f''(x) = (f'(x))'*
* **Důležitá vlastnost**: má-li funkce v bodě derivaci, pak je funkce v tomto bodě spojitá. Vychází z vlastnosti limit. Pozor na to, že to nemusí platit obráceně. Pokud je funkce psojitá v daném bodě, neznamená to, že je zde derivovatelná. typickým příkladem je funkce *f(x) = |x|*. Graf je do špičky, nelze vypočítat směrnici tečny v této špičce. ![absolutni funkce](https://github.com/HoundMarty/SZZ_2020/blob/master/Matematika/imgs/absolutni%20funkce.PNG)

* Pomocí derivací lze řešit i výpočet některých limit, slouží k tomu *L'Hospitalovo pravidlo*


