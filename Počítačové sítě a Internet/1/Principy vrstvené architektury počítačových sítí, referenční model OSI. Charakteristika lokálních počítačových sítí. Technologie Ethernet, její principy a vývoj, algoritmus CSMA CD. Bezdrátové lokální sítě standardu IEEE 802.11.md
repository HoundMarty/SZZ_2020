# Principy vrstvené architektury počítačových sítí, referenční model OSI. Charakteristika lokálních počítačových sítí. Technologie Ethernet, její principy a vývoj, algoritmus CSMA CD. Bezdrátové lokální sítě standardu IEEE 802.11.

### Vrstvový model
Každá ze sedmi vrstev vykonává skupinu jasně definovaných funkcí potřebných pro komunikaci. Pro svou činnost využívá služeb své sousední nižší vrstvy. Své služby pak poskytuje sousední vyšší vrstvě. 
Podle referenčního modelu není dovoleno vynechávat vrstvy, ale některá vrstva nemusí být aktivní. Takové vrstvě se říká nulová, nebo transparentní. 

Komunikaci mezi systémy tvoří: 
* komunikace mezi vrstvami jednoho systému, řídí se pravidly, která se obvykle nazývají rozhraní (interface),
* komunikace mezi stejnými vrstvami různých systémů, řídí se protokoly.

Na počátku vznikne požadavek některého procesu v aplikační vrstvě. Příslušný podsystém požádá o vytvoření spojení prezentační vrstvu. V rámci aplikační vrstvy je komunikace s protějším systémem řízena aplikačním protokolem. Podsystémy v prezentační vrstvě se dorozumívají prezentačním protokolem. Takto se postupuje stále níže až k fyzické vrstvě, kde se použije pro spojení přenosové prostředí. Současně se při přechodu z vyšší vrstvy k nižší přidávají k uživatelským (aplikačním) datům záhlaví jednotlivých vrstev. Tak dochází k postupnému zapouzdřování původní informace. U příjemce se postupně zpracovávají řídící informace jednotlivých vrstev a vykonávají jejich funkce. 

Mnemotechnická pomůcka pro zapamatování: **Aplikace potkala prezentaci, zrealizovaly transport sítí, spojily se fyzicky.** 
### model ISO/OSI

![ISO/OSI](https://github.com/HoundMarty/SZZ_2020/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/ISO-OSI%20prirovnani.png)

Autor: No machine-readable author provided. Pitel assumed (based on copyright claims). – No machine-readable source provided. Own work assumed (based on copyright claims)., CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=1979301


### LAN
Local area network (**LAN**) je termín používaný pro lokální sítě: množinu geograficky blízkých stanic propojených do jednoho jednotně adresovaného segmentu. To znamená, že na lokální síti mají všechny počítače IP adresu ze stejného intervalu hodnot. Takováto síť může mít různou topologii, zpravidla využívající switchů (aktivních prvků přeposílající pakety mezi jednotlivými porty) a bridgů (spojujících jednotlivé fyzické segmenty). Domácí počítačová síť je příkladem LAN, se kterou většina uživatelů běžně pracuje. Na následujícím obrázku si popíšeme příklad takové sítě a úlohu aktivních prvků, které se při jejím sestavení často využívají. 

![LAN síť](https://github.com/HoundMarty/SZZ_2020/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/LANka.PNG)

## IEEE 802.11
IEEE 802.11 je standard pro Wi-Fi.Standard 802.11 zahrnuje několik druhů modulací pro posílání radiového signálu, přičemž všechny používají stejný protokol. Nejpoužívanější modulace jsou definované v dodatcích k původnímu standardu s písmeny a, b, g. 802.11n přináší další techniku modulace. Původní zabezpečení bylo vylepšeno dodatkem i. Další dodatky (c–f, h, j) pouze opravují nebo rozšiřují předchozí specifikaci. 
Standardy 802.11b, 802.11g a 802.11n používají 2,4 GHz pásmo. Proto mohou zařízení interferovat s mikrovlnnými troubami, bezdrátovými telefony, s Bluetooth nebo s dalšími zařízeními používajícími stejné pásmo. Oproti tomu standard 802.11ac používá 5 GHz pásmo a není tedy ovlivněn zařízeními pracujícími v pásmu 2,4 GHz. 

### Ethernet
Ethernet je název souhrnu technologií pro počítačové sítě (LAN, MAN, WAN) z větší části standardizovaných jako IEEE 802.3, které používají kabely s kroucenou dvojlinkou, optické kabely (ve starších verzích i koaxiální kabely) pro komunikaci přenosovými rychlostmi od 1 Mbit/s po 100 Gbit/s. Byl vyvinut firmou Xerox. Sítě Ethernet realizují fyzickou a linkovou vrstvu referenčního modelu OSI, takže je možné po nich provozovat jeden nebo více protokolů síťové vrstvy, například AppleTalk, DECnet, IPX/SPX, a především protokoly **IPv4 a IPv6**, které se používají pro služby sítě Internet. 

## Ethernet frame
Ethernetový rámec je v informatice protokolová datová jednotka linkové vrstvy v síti Ethernet. Na fyzické vrstvě mu předchází preambule a oddělovač začátku rámce (SFD), které s ethernetovým rámcem tvoří paket. 
Ethernetový rámec začíná ethernetovou hlavičkou, která obsahuje cílovou a zdrojovou MAC adresu (anglicky Destination MAC Address, Source MAC Address) a pole Délka/Typ (anglicky Length/Type). Dále obsahuje datové pole (anglicky Payload) a kontrolní posloupnost rámce (anglicky Frame Control Check, FCS), což je 32-bitový cyklický redundantní součet používaný pro detekci poškození dat při přenosu. Datové pole začíná v ethernetovém rámci hlavičkou protokolu (například Internet Protocol). 

![Ethernet 2 frame](https://github.com/HoundMarty/SZZ_2020/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/Ethernet%20typ%202%20frame.png)
zdroj: 
* [wiki Ethernetový rámec](https://cs.wikipedia.org/wiki/Ethernetový_rámec)
* [wiki Ethernet](https://cs.wikipedia.org/wiki/Ethernet)

## CSMA/CD
Carrier Sense Multiple Access with Collision Detection (CSMA/CD) je protokol pro přístup k přenosovému médiu v počítačových sítích. Patří do třídy CSMA, tedy metod s vícenásobným kolizním přístupem a nasloucháním nosné. 
Na rozdíl od čistého CSMA u CSMA/CD stanice při svém vysílání současně kontroluje přenosové médium, zda nezachytí jiné vysílání, které koliduje s jejím. Z této vlastnosti je odvozena přípona „s detekcí kolizí“ (with Collision Detection) v názvu metody. Pokud stanice zjistí kolizi, zastaví vysílání, počká náhodnou dobu a opakuje svůj pokus znovu. CSMA/CD je proto efektivnější než samotné CSMA či CSMA/CA − v nich se kolize nezjišťují a dojde-li k nim, zbytečně se odvysílá celý datový rámec, který bude beztak nutno opakovat. 

## CSMD/CD - Ethernet
Nejrozšířenějším představitelem CSMA/CD je klasický Ethernet. Ten byl postaven na sběrnicové topologii a algoritmus CSMA/CD v něm řídí přístup stanic ke sdílené sběrnici představované koaxiálním kabelem. Stanice, která chce odeslat datový rámec, se podle jeho pravidel chová následovně: 
* Naslouchá, zda je médium volné. Dokud není, čeká na jeho uvolnění.
* Zahájí vysílání. Současně s odesíláním rámce naslouchá, zda nepřichází signál od jiné stanice. Pokud ano, došlo ke kolizi. Stanice ukončí vysílání, odešle signál umožňující rozpoznat kolizi také ostatním (jam signal) a přejde k opakování pokusu podle bodu 3.
* Stanice vybere náhodné číslo z intervalu od 0 do 2<sub>k</sub> - 1, kde k je pořadové číslo pokusu (od 10. pokusu se interval již nezvětšuje a horní hranice zůstává 2<sub>10</sub> - 1, tedy 1023). Náhodné číslo určuje délku čekací doby, po jejímž uplynutí stanice opakuje pokus o odeslání od bodu 1. Maximální počet pokusů je 16, poté je pokus o odeslání považován za neúspěšný.

**Modernější varianty Ethernetu však opouštějí sdílené přenosové médium, používají přepínače s plně duplexním režimem provozu a metoda CSMA/CD u nich není nadále uplatňována.** 
