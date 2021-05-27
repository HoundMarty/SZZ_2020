# Objektově orientované programování, význam a základní principy, struktura programu. Zapouzdření, data metody, správa přístupu. Dědičnost, polymorfismus, pozdní vazba. Abstraktní třídy, rozhraní jako abstraktní datová struktura. Kompatibilita typů. Hierarchie tříd. Genericita a její využití. Výjimky, jejich využití a ošetření.

## Objektově orientované programování
(metody jsou zapouzdřeny v objektech), což umožňuje snadnější přenos kódu mezi různými projekty (abstrakce a zapouzdření). Propojení umožnilo zavést dědičnost, ale kvůli zjednodušení si vyžádalo zavedení polymorfismu

### Zapouzdření 
zaručuje, že objekt nemůže přímo přistupovat k „vnitřnostem“ jiných objektů, což by mohlo vést k nekonzistenci. Každý objekt navenek zpřístupňuje rozhraní, pomocí kterého (a nijak jinak) se s objektem pracuje, a k tomu se používají: modifikátory přístupu, jmenný prostor…( Public, Private, Protected)

### Dědičnost
objekty jsou organizovány stromovým způsobem, kdy objekty nějakého druhu mohou dědit z jiného druhu objektů, čímž přebírají jejich schopnosti, ke kterým pouze přidávají svoje vlastní rozšíření. Tato myšlenka se obvykle implementuje pomocí rozdělení objektů do tříd, přičemž každý objekt je instancí nějaké třídy. Každá třída pak může dědit od jiné třídy (v některých programovacích jazycích i z několika jiných tříd).

### Polymorfismus
odkazovaný objekt se chová podle toho, jaké třídy je instancí. Pozná se tak, že několik objektů poskytuje stejné rozhraní, pracuje se s nimi navenek stejným způsobem, ale jejich konkrétní chování se liší podle implementace. U polymorfismu podmíněného dědičností to znamená, že na místo, kde je očekávána instance nějaké třídy, můžeme dosadit i instanci libovolné její podtřídy, neboť rozhraní třídy je podmnožinou rozhraní podtřídy. U polymorfismu nepodmíněného dědičností je dostačující, jestliže se rozhraní (nebo jejich požadované části) u různých tříd shodují, pak jsou vzájemně polymorfní

### Časná vazba 
vztahuje se k událostem, které mohou být známy během překladu. Speciálně se vztahuje k takovému volání funkcí, které může být řešeno během překladu. Časně vázané položky zahrnují "normální" funkce, přetěžované funkce a nevirtuální členy spřátelených tříd. Když jsou typy těchto funkcí kompilovány během překladu, jsou známy všechny potřebné adresní informace nutné k jejich volání. Hlavní výhodou časné vazby je jejich efektivnosti, rychlost komplice a jejich volání. Hlavní nevýhodou je nedostatek flexibility.

### Pozdní vazba
vztahuje se k událostem, které se vyskytují při běhu programu. Volání pozdně vázané funkce je volání, při němž adresa funkce, která se má volat, není známa dokud se program nespustí. Například virtuální funkce je pozdně vázaný objekt. Hlavní výhodou pozdní vazby je flexibilita při běhu programu. Hlavní nevýhodou je, že s voláním funkce je spojena větší režie. To způsobuje, že jsou tato volání pomalejší, než volání s časnou vazbou.

## Genericita programování
Základní myšlenkou, která se skrývá za pojmem generické programování, je rozdělení kódu programu na algoritmus a datové typy takovým způsobem, aby bylo možné zápis kódu algoritmu chápat jako obecný, bez ohledu nad jakými datovými typy pracuje. 
Konkrétní kód algoritmu se z něj stává dosazením datového typu.

**Jiné vysvětlení:**
Genericita je možnost programovacího jazyka definovat místo konkréhích datových typů jen „vzorytypů“. V definicích tříd, atributů tříd i metod použijeme zástupný datový typ E. Při definici třídypíšeme E do lomených závorek: <E>. Konkrétní datový typ bude určen později, když E nahradímeskutečným existujícím typem
  
**Ukázka v Javě:**
```
  public class Pole<E> {
  E[] data;        
  int kapacita;    
  int pocetPrvku=0;
  }
```
## Abstraktní třídy, rozhraní jako abstraktní datová struktura

### Abstraktní třída 
může deklarovat některé společné metody a poskytovat jejich základní implementaci. Pokud odvozená třída takovou metodu nepředefinuje, pak se pro její instance použije implementace poskytnutá v bázové třídě. 

- Metody, které neimplementuje, musí být označeny jako abstract.
- Abstaktní metody nemohou mít tělo. Nemohou být v abstraktní třídě implementovány.
- Může obsahovat instanční proměnné.
- Statické metody nemohou být označeny jako abstract.
    
### Rozhraní  
- Může obsahovat statické metody.
- Může obsahovat metody, které jsou implementovány (mají tělo).
- Pro implementaci rozhraní se používá klíčové slovo implements.
- Rozhraní nemůže mít instanční proměnné.
- Rozhraní může mít pouze proměnné typu public static final (konstanty).
- Metody v rozhraní jsou defaultně public abstract.
  
 
#### Rozdíl mezi rozhraním a abstraktní třídou:
Rozhraní nemá konstruktor.
Rozhraní může obsahovat pouze konstanty (public static final), kdežto v abstraktní třídě mohou být deklarovány i proměnné jiného typu (třídní, statické nefinální, privátní, …). Abstraktní třídy tedy mohou mít stav.
A hlavně jak bylo napsáno v jedné odpovědi na Stackoverflow: „The main difference between an abstract class and interface in Java 8 is the fact that an abstract class is a class and an interface is an interface.“ (Třída je třída a rozhraní je rozhraní 🙂 ).
  
## Hierarchie tříd
Hierarchie tříd, také nazývaná třídní taxonomie, je skupina souvisejících tříd, které jsou spojeny dědičností, aby dělaly podobné věci. Vrcholem hierarchie může být jediná základní třída, ze které jsou odvozeny všechny ostatní třídy pod ní, nebo hierarchie může mít více základních tříd, jejichž funkce se později sloučí do jedné nebo více odvozených tříd. 
  
Vztahy mezi třídami lze ilustrovat jako stromy a každý menší strom v rámci velké taxonomie lze také považovat za hierarchii. 

## Výjimky
  
Výjimka (anglicky exception) je v programování výjimečná situace, která může nastat za běhu programu. Jedná se o zobecnění vnitřního přerušení vyvolaného chybou při provádění programu. Ve vyšších programovacích jazycích je obvykle výjimka spojena s objektem nesoucím informace o chybovém stavu. 

Typickým přístupem prosazujícím použití výjimek je tzv. **Defenzivní programování**, které se vyznačuje snahou o ošetření všech neočekávaných stavů, ke kterým by mohlo za běhu programu dojít. 
  
V opozici k defenzivnímu programování stojí do značné míry **kontraktové programování**, které se zakládá na předpokladu, že je nutné pouze zajistit stavy, které nejsou ošetřeny kontraktem nebo zadáním.

```
 try {
  line = console.readLine();
  if (line.length() == 0) {
    throw new EmptyLineException("The line read from console was empty!");
  }
  console.printLine("Hello %s!" % line);
  console.printLine("The program ran successfully");
 } catch (EmptyLineException e) {
  console.printLine("Hello!");
 } catch (Exception e) {
  console.printLine("Error: " + e.message());
 } finally {
  console.printLine("The program terminates now");
 }
 ```
