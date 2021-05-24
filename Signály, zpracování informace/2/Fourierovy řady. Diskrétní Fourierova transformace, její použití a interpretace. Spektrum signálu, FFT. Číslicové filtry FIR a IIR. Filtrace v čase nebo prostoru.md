#zdroj k prostudování
https://betterexplained.com/articles/an-interactive-guide-to-the-fourier-transform/

# Fourierovy řady. Diskrétní Fourierova transformace, její použití a interpretace. Spektrum signálu, FFT. Číslicové filtry FIR a IIR. Filtrace v čase nebo prostoru
Kombinací zastoupení vyšších harmonických lze vytvořit prakticky libovolný periodický signál – harmonická syntéza.
Platí i obrácené tvrzení: Libovolný periodický signál lze rozložit na jednotlivé harmonické složky - harmonická analýza.

## Fourierovy řady (Fourierův rozvoj)
Umožnují rozložit a složit jakýkoliv **periodický spojitý** signál na harmonické složky.

**Polární tvar Fourierových řad**
![Polární tvar Fourierových řad](https://user-images.githubusercontent.com/29363626/119375276-e8c38a00-bcba-11eb-8012-1bc4e8168540.png)
- Libovolný periodický spojitý signál x(t) lze rozložit na součet dílčích složek
- dílčí složky jsou hamornicky vázané kosinusovky s amplitudami c<sub>k</sub> a fázovými posuny φ<sub>k</sub>
- při analýze signálu je nutné spočítat koeficienty c<sub>k</sub> a φ<sub>k</sub>

**Exponenciální tvar Fourierových řad**
![Exponenciální tvar Fourierových řad](https://user-images.githubusercontent.com/29363626/119375623-4e177b00-bcbb-11eb-9d86-4a9cce306b2d.png)
- Součet harmonicky vázaných exponenciel
- X<sub>k</sub> je komplexní koeficient, definován i pro záporné indexy k

**Vztah mezi oběma tvary**
- Oba vztahy jsou ekvivalentní
- polární usnadňuje interpretaci 
- exponenciální tvar usnadňuje výpočet na PC
vztahy mezi koeficienty:
 ![vztahy mezi koeficienty](https://user-images.githubusercontent.com/29363626/119375906-aa7a9a80-bcbb-11eb-8ffb-f8aa44fca6b5.png)

## Diskrétní Fourierova transformace (DFT)
**Pouze exponenciální tvar**
![DFT](https://user-images.githubusercontent.com/29363626/119376074-db5acf80-bcbb-11eb-8c16-01af576d5956.png)
- DFŘ - číslicové (diskrétní) Fourierovy řady
- aplikovatelné na **konečný periodický** signál daný výštem vzorků (N)
- **DFT** - Diskrétní Fourierova transformace - používá se pro výpočet spektra libovolného signálu
- **FFT** - rychlá metoda výpočtu DFT

**Praktické použití Fourierovy analýzy**
- umožňuje provést frekvenční analýzu signálu, tj. určit z jakých dílčích signálů (kosinusovek o různých frekvencích a amplitudách) se skládá
- výsledkem je spektrum signálu, ze spektra lze získat detailní informace o obsahu signálu 
- spektrum periodických signálů lze jednoduše zobrazit jakožto závislost amplitudy a fáze na frekvenci
- znalost spektra umožňuje např. kompresi signálů
- je-li spektrum signálu v čase proměnné, počítá se postupně v rámci kratších úseků signálu a zobrazuje se pak pomocí spektrogramu

## FFT - Optimalizovaný výpočet DFT
- jedná se o optimalizovaný výpočet DFT - poskytuje úplně stejné hodnoty ale rychleji.
- nejlépe funguje v případech, že **N je mocninou 2**

**Shrnutí**
- Výpočet spektra u číslicových signálů je možný díky diskrétní Fourierově transformaci - DFT
- U periodických číslicových signálů DFT poskytne stejný výsledek, jako bychom dostali pomocí FŘ aplikovaných na nevzorkovanou funkci. Podmínkou je celistvý násobek periody.
- Pokud není podmínka splněna nebo jde-li o obecný signál, bude spektrum obsahovat ještě další složky soustředěné kolem hlavních frekvenčních složek („rozmazání spektra“).
- FFT je algoritmus, který umožňuje velmi rychlý výpočet DFT (speciálně pro N = 2B).

## Filtry 
Systémy modifikující vstupní signál
![Filtry](https://user-images.githubusercontent.com/29363626/119385025-d864dc80-bcc5-11eb-80ce-d2ec72b0e797.png)

![Vztahy mezi jednotlivými popisy filtrů](https://user-images.githubusercontent.com/29363626/119385110-fb8f8c00-bcc5-11eb-8db5-667265bbd069.png)

### FIR - Nerekurzivní systém (Finite Impulse Response) - Systém s konečnou odezvou
Výhody FIR
- Jednoduchý a intuitivní návrh
- Filtr je vždy stabilní
- mohou zajistit lineární průběh fázové charakteristiky

Nevýhody FIR
- hůře se dosahuje velké strmosti... tedy přechodu mezi propustným a nepropustným pásmem.
- pro dosažení velké strmosti jsou nutné filtry s mnoha koeficienty, které mají dlouhé spoždění


Příklady FIR
![Zesilovač](https://user-images.githubusercontent.com/29363626/119383487-aeaab600-bcc3-11eb-9c4c-0774851680ad.png)
![Zpožďovač](https://user-images.githubusercontent.com/29363626/119383526-b9654b00-bcc3-11eb-983d-c8dd454351f0.png)
![Derivátor (diferenciátor)](https://user-images.githubusercontent.com/29363626/119383575-c8e49400-bcc3-11eb-93e2-5213ec9415f5.png)
![Průměrovací filtr 3. řádu nekauzální](https://user-images.githubusercontent.com/29363626/119383635-dbf76400-bcc3-11eb-91eb-55cca04e503b.png)
![Průměrovací filtr kauzální](https://user-images.githubusercontent.com/29363626/119383697-f3cee800-bcc3-11eb-948d-3fafd0385318.png)

### IIR - Rekurzivní systém (Infinite Impulse Response) - Systém s nekonečnou odezvou
Vstupní signál zaveden na vstup - **zpětná vazba**
![IIR popis](https://user-images.githubusercontent.com/29363626/119385733-dd765b80-bcc6-11eb-9ee5-decca77a3092.png)

Vlastnosti:
- Poměrně složitý návrh
- Filtr je zpětnovazební, může být nestabilní.
- Stabilní bude za předpokladu, že všechny jeho póly leží uvnitř jednotkové kružnice
- S IIR filtry lze dosáhnout velmi strmých přechodů
- Nemají lineární průběh fázové charakteristiky

##  Filtrace v čase nebo prostoru
**Z-transformace** nástroj usnadňující analýzu chování LTI systémů a jejich návrh. Transformuje číslicové signály a popisy číslicových systémů **do prostoru komplexních čísel**.
Operaci konvoluce převádí na snažší operaci součinu. Existuje přímá vazba mezi Fourierovou transformací a Z-transformací.
![Úvod Z_transformace](https://user-images.githubusercontent.com/29363626/119384335-d5b5b780-bcc4-11eb-9e48-6afacad3ba0f.png)
![Terminologie](https://user-images.githubusercontent.com/29363626/119384398-ef56ff00-bcc4-11eb-8b04-09ec52a24f0f.png)
![Přenosová funkce a impulzní odezva](https://user-images.githubusercontent.com/29363626/119384581-3644f480-bcc5-11eb-9cd1-79efb9c2b634.png)

![Souvislosti](https://user-images.githubusercontent.com/29363626/119384835-8fad2380-bcc5-11eb-9cf0-bb176146d87a.png)

