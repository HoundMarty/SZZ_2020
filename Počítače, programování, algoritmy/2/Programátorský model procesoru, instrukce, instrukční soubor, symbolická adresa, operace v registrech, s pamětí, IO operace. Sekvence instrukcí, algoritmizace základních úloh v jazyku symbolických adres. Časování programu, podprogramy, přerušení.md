
# Programátorský model procesoru, instrukce, instrukční soubor, symbolická adresa, operace v registrech, s pamětí, IO operace. Sekvence instrukcí, algoritmizace základních úloh v jazyku symbolických adres. Časování programu, podprogramy, přerušení.

## Programátorský model procesoru
Tento procesor využívá harvardskou architekturu, tzn. bude mít oddělenou pamět pro program a pamět pro data. Programová pamět v tomto modelu je zanedbaná. Předpokládáme, že v ní je program, který se vykonává. Dále předpokládáme, že se jedná o procesor typu **RISC** a tak vykonání každé instrukce zabere právě jeden hodinový cyklus. Celý procesor je osmibitový a proto všechny datové sběrnice a registry budou mít osm bitů. Adresová sběrnice k datové paměti bude šestnáctibitová. To znamená, že do paměti se vejde 2<sup>16</sup> = 65536 bytů dat.

![programátorský model procesoru](https://github.com/HoundMarty/SZZ_2020/blob/master/Po%C4%8D%C3%ADta%C4%8De%2C%20programov%C3%A1n%C3%AD%2C%20algoritmy/imgs/program%C3%A1torsk%C3%BD%20model%20procesoru.PNG)

Aby procesor mohl komunikovat s okolním světem, potřebuje i nějaké vstupy a výstupy. Ty budou také osmibitové a pracovat se s nimi bude obdobně jako s datovou pamětí. Adresová sběrnice pro vstupy i výstupy bude osmibitová. to znamená, že vstupů a výstupů může být až 2<sup>8</sup> = 256 bytů.

Uvnitř procesoru se nachází:
* Řadič instrukcí - dekóduje instrukci na vstupu a provede potřebné operace
* ALU - Aritmeticko-logická jednotka, ta provádí vlastní výpočty
* Univerzálně použitelné registry R0..R7 - slouží jako rychlá pamět pro výpočty
* Registr PSW(Program State Word) - tento regist obsahuje stav procesoru.
* Registr DPTR(Data Pointer) - slouží pro nepřímé adresování v datové paměti, je šestnáctibitový ale přistupujeme k němu osmibitově pomocí registrů DPL a DPH
* Registr SP(Stack Pointer) - slouží jako ukazatel na vrchol zásobníku, podobně jako DPTR je šestnáctibitový ale pracujeme s nim osmibitově pomocí registrů SPL a SPH
* Registr PC(Program Counter) - tento registr obsahuje adresu aktuálně vykonávané instrukce v programové paměti. Je šestnáctibitový, takže program může mít maximálně 65536 instrukcí

### Instrukce
Strojová instrukce je v informatice označení kódovaného příkazu pro provedení elementární operace procesoru, kterou je procesor schopen přímo vykonat (procesor je základní součástí počítače). Posloupnost strojových instrukcí je označována jako strojový kód. Různé procesory mají různé sady strojových instrukcí. Některé procesory podporují více sad strojových instrukcí (např. současné procesory pro počítače IBM PC kompatibilní podporují sadu x86-16, IA-32 a x86-64, které se celkově označují jako x86).

#### Architektura instrukčního souboru
**ISA**(Instruction Set Architecture) popisuje jakým způsobem programátor nahlíží na daný procesor. Definuje, které operace stroj umí provádět, formáty zpracovávaných dat, způsob, jakým procesor může manipulovat s proměnnými, či říká, jak lze komunikovat s paměti nebo periferiemi. **ISA** nedefinuje, jakým způsobem je daný HW realizován. Například programy psané pro **x86 ISA**(tj. instrukční sadě kompatibilní s procesory **8086**,**80286**, až po nejmodernější procesory **core I3/5/7**) jsou spustitelné jak na dvě dekády starých počítačích, tak na nejmodernějších strojích od různých výrobců. 

#### RISC a CISC
Počítače, jejichž **ISA** podporuje hodně různorodých operací jsou historicky nazývány počítači s komplexním instrukčním souborem. V anglické literatuře bývají označovány jako **CISC**(Complex Instruction Set Computers, např. **x86**). Jejich protipólem jsou počítače, které podporují jen omezený výčet operací a nazývají se počítači s redukovaným instrukčním souborem(anglicky **RISC** - Reduced ISC, např. **ARM**,**MIPS**).

#### Řízení toku programu
Řízení toku programu lze rozdělit na podmíněné skoky, volání funkcí, návraty z funkcí a obsluhu přerušení. Skoky (**JUMP**) se porávdějí změnou hodnoty adresy programu a to tak, že je aktuální adresa změněna většinou relativně.

Řízení **skoků** se může provádět s pomocí speciálního registru, který ukládá příznaky poslední dokončené operace ALU. Takový registr se nazývá **příznakový** a příznaky v něm uložené se nazývají **flag**. Příznakový registr obsahuje typicky vlajky:
* **Carry**(přetečení)
* **Zero**
* **Sing**(znaménko)
* **Overflow**(přeplnění)

#### Instrukční cyklus
Instrukční cyklus (někdy strojový cyklus) je sled všech operací nutných k vykonání jedné instrukce a běh programu se skládá ze sledu mnoha instrukčních cyklů.

## Počítačové systémy
Základní schéma použití univerzálního programovatelného automatu je známe už od 40. let dvacátého století. Schéma se skládá z neměnitelné paměti programu, měnitelné paměti dat, řídící jednotky, ALU, IO bloku. Harvardská architektura byla prezentována na americké univerzitě Harvard a uplatnila se při kontrukci elektromagnetického počítače Harvard Mark I. Ve čtyřicátých letech představil americký matematik maďarského původu John Von Neumann svůj koncept architektury počítače. Von Neumann sdružil datovou a programovou pamět a umožnil tak vytváření programů, které se mohou samy modifikovat (tj. umožňuje vytvářet programy samotným počítačem).

![Architektury](https://github.com/HoundMarty/SZZ_2020/blob/master/Po%C4%8D%C3%ADta%C4%8De%2C%20programov%C3%A1n%C3%AD%2C%20algoritmy/imgs/Architektury.PNG)

Architektura počítačů s oddělenou datovou a instrukční pamětí nazýváme **Harvardskou**, počítače se sdílenou pamětí používají **Von Neumannovou** architekturu.

Moderní počítače používají tzv. **modifikovanou harvardskou architekturu**. Pamět programu a dat bývá zdánlivě oddělená (např. pomocí cache), ale fyzicky se jedná o stejnou pamět, do které lze zapisovat. Drobnou modifikací konceptu bylo též seskupení řadiče, IO portů a ALU do jednoho celku, který se nazývá CPU(Central Processing Unit).
