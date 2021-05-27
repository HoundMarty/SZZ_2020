
# Vyšší programovací jazyky (Java, C, C# apod.). Struktura programu, implementace příkazů a datových typů. Práce se soubory, operace vstupu a výstupu. Algoritmizace základních úloh, třídění, vyhledávání, porovnání algoritmů.

## Vyšší programovací jazyky:
Vyšší programovací jazyk (též vysokoúrovňový jazyk, problémově orientovaný jazyk) je v informatice označení pro programovací jazyk s větší mírou abstrakce. Vyšší abstrakcí je míněno přiblížení zápisu zdrojového kódu programu v daném programovacím jazyce k tomu, jak problémy zpracovává svým myšlením člověk. Nižší programovací jazyk se naopak svým zápisem přibližuje tomu, jak po technické stránce pracuje počítač (resp. jeho procesor)

## Programovací paradigmata 
jsou způsob, jak klasifikovat programovací jazyky na základě jejich vlastností. Jazyky lze rozdělit do několika paradigmat Programovací paradigma
(https://cs.qaz.wiki/wiki/Programming_paradigm![obrazek])

*Například programy napsané v C ++, Object Pascal nebo PHP mohou být čistě procedurální , čistě objektově orientované nebo mohou obsahovat prvky obou nebo jiných paradigmat. Návrháři a programátoři softwaru rozhodují o tom, jak tyto prvky paradigmatu použít. Programovací paradigma* - https://cs.qaz.wiki/wiki/Programming_paradigm


 **Procedurální (imperativní)**
  – popisuje výpočet pomocí posloupností příkazů a určuje přesný postup (algoritmus), jak danou úlohu řešit
        Strukturované – algoritmus se rozděluje na dílčí úlohy, které se spojují v jeden celek
        Objektově orientované - metody jsou zapouzdřeny v objektech), což umožňuje snadnější přenos kódu mezi různými projekty (abstrakce a zapouzdření). Propojení umožnilo zavést dědičnost, ale kvůli zjednodušení si vyžádalo zavedení polymorfismu.

**Neprocedurální (deklarativní)**
  – programování pomocí definic co se dělat má a ne jak se to má dělat

## Struktura programu: (Vlastními slovy sepsáno - nevím jak jinak)
Ta se skládá z několika prvků jako
	- Import potřebných knihoven a tříd
	- Jednotlivé třídy
	- Z objektů a funkcí
	- Ze samotného kódu uvnitř tříd a funkcí
	- Komentáře

implementace příkazů a datových typů: (Deklarace)
Zavádí jméno (identifikátor) a zpravidla určuje jeho datový typ a další aspekty pro proměnné, funkce (procedury), konstanty apod.

**Příklad:**
```
char priklad1 = 'e';
int priklad2 = 5;
void priklad3(void)
{
  int x = 7;
}
```

##Práce se soubory:
V případě C# pro práci se soubory využíváme systémovou knihovnu System.IO
V zásadě se k souborům přistupuje pomocí tzv. Streamů., v Javě to je třeba BufferedWriter
Druhou možností je využít třídu File

```
using (StreamWriter sw = new StreamWriter(@"soubor.txt"))
{
    sw.WriteLine("První řádek");
    sw.WriteLine("Tento text je na druhém řádku");
    sw.WriteLine("A do třetice.");
    sw.Flush();
}
```
"Flush() Vymaže vyrovnávací paměti pro tento datový proud a způsobí, že se do souboru zapisují data do vyrovnávací pamět"

## Operace vstupu a výstupu

```
static void bubbleSort(int []arr)
    {
        int n = arr.Length;
        for (int i = 0; i < n - 1; i++)
            for (int j = 0; j < n - i - 1; j++)
                if (arr[j] > arr[j + 1])
                {
                    // swap temp and arr[i]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
    }

```
```
static public int Partition(int[] arr, int left, int right) {
         int pivot;
         pivot = arr[left];
         while (true) {
            while (arr[left] < pivot) {
               left++;
            }
            while (arr[right] > pivot) {
               right--;
            }
            if (left < right) {
               int temp = arr[right];
               arr[right] = arr[left];
               arr[left] = temp;
            } else {
               return right;
            }
         }
      }
      static public void quickSort(int[] arr, int left, int right) {
         int pivot;
         if (left < right) {
            pivot = Partition(arr, left, right);
            if (pivot > 1) {
               quickSort(arr, left, pivot - 1);
            }  
            if (pivot + 1 < right) {
               quickSort(arr, pivot + 1, right);
            }
         }
```

## Algoritmizace základních úloh: 

### Porovnání algoritmů - třídící:
Bubble sort O(n^2)
Quick sort - nejhorší scénář O(n^2), průměrně však O(n log n)
Merge sort - průměrně i nejhorší scénář stále O(n log n)


### Vyhledávání - Binární vyhledávací strom - BST (Binary spanning tree)
**Postup hledání:**
1. Pokud je strom prázdný, ukončíme prohledávání.
2. Jinak testujeme shodu uzlu U a hledané položky Y. V případě shody ukončíme prohledávání.
3. Pokud Y menší než hodnotaU.L, hledáme v L podstromu.4Jinak prohledáme P podstrom

### Vyhledávání - Hash
Využití je např. pro rychlé vyhledávání položky v poli nebo v jiném homogenním datovém typu. Pomocí hašovací funkce přiřazujeme hodnotě klíče index (ukazatel) do homogenní datové struktury. Při zápisu obsahu položky zapíšeme položku na odpovídající místo. Pokud je obsazeno, pak pomocí vhodného algoritmu přiřadíme pro položku další volný index. Při vyhledávání položky spočteme s pomocí klíče index hledané položky. Pokud již bylo odpovídající místo přepsáno položkou s jiným klíčem, opět podle stejného algoritmu prohledáváme další položky. Při správně zvolené velikosti (počtu položek) homogenní datové struktury a vhodně zvolené hašovací funkci má tento algoritmus složitost v průměrném (tj. očekávaném) případě shora omezenou na O(1)

**Mezi hlavní vlastnosti této funkce patří:**
jakékoliv množství vstupních dat poskytuje stejně dlouhý výstup (otisk),
malou změnou vstupních dat dosáhneme velké změny na výstupu (tj. výsledný otisk se od původního zásadně na první pohled liší),
z hashe je prakticky nemožné rekonstruovat původní text zprávy (což je rozdíl oproti klasickému šifrování),
v praxi je vysoce nepravděpodobné, že dvěma různým zprávám odpovídá stejný hash, jinými slovy pomocí hashe lze v praxi identifikovat právě jednu zprávu (ověřit její správnost).

Hašování v základní variantě dovoluje testovat vstupní data na shodu, tedy rovnost. Nezachovává podobnost dat ani uspořádání


