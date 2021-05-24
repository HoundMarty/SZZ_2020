# Signály a systémy. LTI systémy. Přenosová funkce, impulsní odezva. Konvoluce u číslicových signálů. Autokorelační funkce a její praktické využití

**Systém** dokáže generovat, zpracovávat, modifikovat a přijímat **signály**. **Signál** je provevem činnosti **systému**.
- Hudební nástroj - lze považovat za systém generující zvuk
- Zesilovač, ekvalizér - systém, který modifikuje zvukový signál
- A/D a D/A převodníky - transformují jeden typ signálu na jiný
- Reproduktor - převádí elektrický signál na akustický

![Popis systému pomocí vstupního a výstupního signálu a systémové funkce](https://user-images.githubusercontent.com/29363626/119379103-583b7880-bcbf-11eb-9836-c23eedc37614.png)

**Systémy podle charakteru signálu**
- Spojité
- Číslicové
- Hybridní

**Podle kauzality**
princip kauzality: "následek přichází až **po** příčině"
- Kauzální - odezva závisí pouze na současných a minulých hodnotách vstupu
- Nekauzální - závisí i na budoucích hodnotách (nelze realizovat online)

**Podle linearity**
- Lineární - odezva na lineární kombinaci budících signálů je rovna lineární kombinaci odezev na jednotlivé budící signály 

Příklady:
![Linearita - příklady](https://user-images.githubusercontent.com/29363626/119379611-fd565100-bcbf-11eb-9c7f-a62052a10826.png)

**Podle časové závislosti**
Pro časově nezávislý systém musí platit... Je-li signál zpožděn o čas, musí i jeho výstup být zpozděň o stejný čas. Tedy "Chování systému se nemění v čase"

Příklady:
![Stacionarita - příklady](https://user-images.githubusercontent.com/29363626/119379899-4f977200-bcc0-11eb-9ab6-dc071530a22b.png)

## LTI systémy - Linear time-invariant
lineární časově nezávislé systémy
Systémy relativně jednoduché pro popis, analýzu a syntézu. Jejich chování (u spojitých systémů) popisují diferenciální rovnice s konstantními koeficienty:
![diferenciální rovnice s konstantními koeficienty](https://user-images.githubusercontent.com/29363626/119380145-9f763900-bcc0-11eb-9648-14ca8ca41a8e.png)
u číslicových systémů jsou jejich ekvivalentem **diferenční rovnice**

- Rekurzivní - závislý na předchozích výstupech, zpětnovazební
- Nerekuzivní - je-li N=0

Chování libovolného LTI systému lze **jednoznačně** popsat tím, jak reaguje na jednotkový impulz.
Odezva na jednotkový impuls se označuje **h[n]**
Známe-li h[n], můžeme určit odezvu na libovolný signál pomocí operace nazývané **konvoluce**.

## Konvoluce
Je matematická funkce postihující **interakci signálu a systému** popsaného impulzní odezvou (h[n])

![Odvození konvoluce u číslicových signálů](https://user-images.githubusercontent.com/29363626/119382013-c8e39480-bcc1-11eb-9e45-321c46334b0e.png)

![Konvoluce obecně](https://user-images.githubusercontent.com/29363626/119382200-021c0480-bcc2-11eb-8ebc-946ab2e209e5.png)

![Příklad výpočtu](https://user-images.githubusercontent.com/29363626/119382379-3bed0b00-bcc2-11eb-86b9-4f400bc90346.png)
**Jde o součet dílčích součinů signálu x a funkce h otočené kolem bodu n**

![Metoda posuvného proužku](https://user-images.githubusercontent.com/29363626/119382734-bcac0700-bcc2-11eb-8df5-4dc5ab1e8f4f.png)

![Konvoluce periodického signálu](https://user-images.githubusercontent.com/29363626/119382784-ce8daa00-bcc2-11eb-93a6-3525070ee653.png)

**Vlastnosti konvoluce**
- Komutativní
![Komutativnost](https://user-images.githubusercontent.com/29363626/119383351-81f69e80-bcc3-11eb-8519-b31da50bc8e4.png)
- Asociativní
![Asociativita](https://user-images.githubusercontent.com/29363626/119383395-8e7af700-bcc3-11eb-86b2-f5c492d66e5c.png)



