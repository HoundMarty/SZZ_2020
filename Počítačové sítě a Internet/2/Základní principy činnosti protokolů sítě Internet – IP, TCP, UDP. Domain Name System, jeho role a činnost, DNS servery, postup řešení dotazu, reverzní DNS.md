# Základní principy činnosti protokolů sítě Internet – IP, TCP, UDP. Domain Name System, jeho role a činnost, DNS servery, postup řešení dotazu, reverzní DNS.

### IP - Internet Protocol
Internet Protocol je zodpovědný za směrování datagramů (paketů) ze zdrojového počítače do cílového hostitele přes jednu nebo více IP sítí  
Internet Protocol je v informatice základním protokolem pracujícím na síťové vrstvě používaným v počítačových sítích a Internetu. Sám o sobě neposkytuje záruky na přenos dat a rozlišuje pomocí IP adresy pouze jednotlivá síťová rozhraní. V současné době je stále ještě používána starší verze protokolu IPv4, nově se přechází na IPv6.  
Dne 3. února 2011 byly rozděleny na konferenci v Miami poslední bloky adres protokolu IPv4, čímž došlo k jejich vyčerpání

## Funkce protokolu
Internet Protocol je zodpovědný za směrování datagramů (paketů) ze zdrojového počítače do cílového hostitele přes jednu nebo více IP sítí. Paket se skládá z řídících dat (metadat) a z uživatelských dat (užitečné zatížení, anglicky payload). Řídící data poskytují síti potřebná data k doručení paketu, například adresu zdroje a cíle, kódy pro detekci chyb – kontrolní součty a informace o pořadí. 
Data se v IP síti posílají po blocích nazývaných datagramy. Jednotlivé datagramy putují sítí zcela nezávisle, na začátku komunikace není potřeba navazovat spojení či jinak „připravovat cestu“ datům, přestože spolu třeba příslušné stroje nikdy předtím nekomunikovaly. 
IP v doručování datagramů poskytuje nespolehlivou službu, označuje se také jako best effort – „nejlepší úsilí“; tj. všechny stroje na trase se datagram snaží podle svých možností poslat blíže k cíli, ale nezaručují prakticky nic. Datagram vůbec nemusí dorazit, může být naopak doručen několikrát a neručí se ani za pořadí doručených paketů. Pokud aplikace potřebuje spolehlivost, je potřeba ji implementovat v jiné vrstvě síťové architektury, typicky protokoly bezprostředně nad IP (viz TCP). 
Pokud by síť často ztrácela pakety, měnila jejich pořadí nebo je poškozovala, výkon sítě pozorovaný uživatelem by byl malý. Na druhou stranu příležitostná chyba nemívá pozorovatelný efekt. Navíc se obvykle používá vyšší vrstva, která ji automaticky opraví. 

Zdroj: [Internet Protokol](https://cs.wikipedia.org/wiki/Internet_Protocol)

### Formát IP datagramu

![Formát IP datagramu](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/IP_Datagram.png)

### TCP - Transmission Control Protocol
TCP je spojově orientovaný protokol pro přenos toku bajtů na transportní vrstvě se spolehlivým doručováním. V sadě protokolů Internetu je TCP prostřední vrstvou mezi IP protokolem pod ním a aplikací nad ním. Aplikace ke vzájemné komunikaci využívají spolehlivé spojení na způsob roury, zatímco IP protokol neposkytuje takové streamy, ale jen nespolehlivé pakety. TCP používá služby protokolu IP; opakovaným odesíláním ztracených nebo poškozených paketů přes nespolehlivou síť zajišťuje spolehlivost a přeuspořádáváním přijatých paketů zajišťuje jejich správné pořadí. Tím TCP plní úlohu transportní vrstvy ve zjednodušeném modelu ISO/OSI počítačové sítě.

## TCP porty
K rozlišení komunikujících aplikací používá TCP protokol čísla portů. Každá strana TCP spojení má přidruženo 16bitové bezznaménkové číslo portu (existuje 65535 portů) přidělené aplikaci. Porty jsou rozčleněny do třech skupin: dobře známé, registrované a dynamické/privátní. Několik příkladů: FTP (port 21 a 20), SMTP (port 25), DNS (port 53) a HTTP (port 80).

## Alternativa k TCP
Pro mnoho aplikací není TCP vhodné. Velkým problémem představuje (alespoň u normálních implementací) blokování čela fronty, kvůli kterému aplikace po ztrátě jednoho paketu nedostává následující pakety do té doby, dokud není ztracený paket znovu poslán a úspěšně přijat. To způsobuje problémy realtimovým aplikacím jako streamovaná média (např. internetové rádio), realtimové hry pro více hráčů a VoIP, u kterých je důležitější dostávat data včas, než je dostávat ve správném pořadí a kompletní. 

Složitost TCP může být problém také pro vestavěná zařízení (anglicky embedded systems). Nejznámějším příkladem je bootování po síti, které obecně používá TFTP (viz PXE). Navíc pro některé triky, jako je přenos dat mezi dvěma uzly, které jsou oba za NATem (použitím STUN nebo podobných protokolů), je mnohem jednodušší, když vám v cestě nestojí složitý protokol jako TCP. 

Tam, kde je TCP nevhodné, se často používá UDP, které poskytuje aplikaci kontrolu/ovládání nad multiplexováním a ověřováním kontrolních součtů. Zato ale UDP neprovádí fragmentaci proudu dat do paketů a zpátky jejich rekonstruování, ani opětovné posílání ztracených paketů. To dovoluje vývojáři aplikace napsat si uvedené funkce tak, jak vyhovuje jeho potřebám, nebo je nahradit použitím samoopravných kódů (anglicky forward error correction) nebo interpolace. 

**SCTP** je transportní protokol nad IP, který poskytuje spolehlivé, datagramové služby nepříliš odlišné od TCP. SCTP je novější a mnohem složitější protokol než TCP; rutinně se používá v telekomunikačních sítích pro přenos signalizace, ale v běžném provozu se nedočkal širokého nasazení, ačkoliv je obzvláště navržený k tomu, aby byl používaný v situacích, kdy jsou spolehlivost a téměř real-time ohledy důležité. 

**Venturi Transport Protocol (VTP)** je patentovaný proprietární protokol, který je navržen tak, aby nahradil TCP a transparentně překonal vnímané nedostatky vztahující se k bezdrátovému přenosu dat. 

TCP má také problémy v prostředí s vysokou šířkou pásma. TCP algoritmy pro zamezení zahlcení fungují velmi dobře pro ad-hoc prostředí, kde odesílatel dat není předem znám. Také v případě, že je prostředí dopředu známo, mohou časové principy protokolu, jako je například asynchronní typ přenosu snížit režii pro znovu odeslání dat. 

**QUIC** (Quick UDP Internet Connections) je experimentální protokol využívající UDP, který vyvinula společnost Google pro novou verzi protokolu HTTP. 

Zdroj: [Transmission Control Protocol](https://cs.wikipedia.org/wiki/Transmission_Control_Protocol)

### Navázání TCP spojení
1. Klient odešle na server datagram s nastaveným příznakem SYN a náhodně vygenerovaným pořadovým číslem (x), potvrzovací číslo=0.
2. Server odešle klientovi datagram s nastavenými příznaky SYN a ACK, potvrzovací číslo=x+1, pořadové číslo je náhodně vygenerované (y)
3. Klient odešle datagram s nastaveným příznakem ACK, pořadové číslo=x+1, číslo odpovědi=y+1

**Ukončení spojení probíhá podobně jako jeho navázání. Používá se k tomu příznaků FIN a ACK**

### TCP segment 
![TCP segment](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/TCP_segment.png)

## UDP
Protokol UDP je vhodný pro nasazení, které vyžaduje jednoduchost, malá režie nebo pro aplikace pracující systémem otázka-odpověď (např. DNS, sdílení souborů v LAN). Jeho bezstavovost je užitečná pro servery, které obsluhují mnoho klientů nebo pro nasazení, kde se počítá se ztrátami datagramů a není vhodné, aby se ztrácel čas novým odesíláním (starých) nedoručených zpráv (např. VoIP, online hry).  

### UDP Datagram
![UDP Datagram](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/UDP_datagram.png)

Port je 16bitová hodnota, která umožňuje používat porty z rozsahu 0-65535. Port 0 je rezervován, ale je možné ho použít, pokud odesílající proces neočekává žádnou odpověď

## DNS
(Domain Name System) je hierarchický, decentralizovaný systém doménových jmen, který je realizován servery DNS a protokolem stejného jména  
Kořenem stromu je tzv. kořenová doména, která se zapisuje jako samotná tečka. Pod ní se v hierarchii nacházejí tzv. domény nejvyšší úrovně  
#### Dva druhy doménových serverů:   
1. Autoritativní server je ten, na němž jsou trvale uloženy záznamy k dané doméně/zóně.
2. Rekurzivní (caching only) server je server, na který se se svými dotazy obracejí klientská zařízení. Doba uložení v cache - TTL je nastavováná v časových jednotkách (hodiny) 

#### Kořenové servery:
Tyto servery poskytují kořenový zónový soubor (root zone file) ostatním DNS serverům. Těch je 13 (ne přímo fyzicky) - písmena A-M

Pokud počítač hledá určitou informaci v DNS (např. IP adresu k danému jménu), obrátí se s dotazem na tento lokální server. Pokud nenajde patřičný záznam u sebe ptá se nadřazeného DNS serveru (Lokální => Autoritativní => kořenový)

## Postup řešení dotazu na DNS

	1. Uživatel zadal do svého WWW klienta doménové jméno www.wikipedia.org. Resolver v počítači se obrátil na lokální DNS server s dotazem na IP adresu pro www.wikipedia.org.
	2. Lokální DNS server tuto informaci nezná. Má však k dispozici adresy kořenových serverů. Na jeden z nich se obrátí (řekněme na 193.0.14.129) a dotaz mu přepošle.
	3. Kořenový server také nezná odpověď. Ví však, že existuje doména nejvyšší úrovně org a jaké jsou její autoritativní servery, jejichž adresy tazateli poskytne.
	4. Lokální server jeden z nich vybere (řekněme, že zvolí tld1.ultradns.net s IP adresou 204.74.112.1) a pošle mu dotaz na IP adresu ke jménu www.wikipedia.org.
	5. Oslovený server informaci opět nezná, ale poskytne IP adresy autoritativních serverů pro doménu wikipedia.org. Jsou to ns0.wikimedia.org (207.142.131.207), ns1.wikimedia.org (211.115.107.190) a ns2.wikimedia.org (145.97.39.158).
	6. Lokální server opět jeden z nich vybere a pošle mu dotaz na IP adresu ke jménu www.wikipedia.org.
	7. Jelikož toto jméno se již nachází v doméně wikipedia.org, dostane od jejího serveru nepochybně autoritativní odpověď, že hledaná IP adresa zní 145.97.39.155
	8. Lokální DNS server tuto odpověď předá uživatelskému počítači, který se na ni ptal. 666

Zdroj: (https://cs.wikipedia.org/wiki/Domain_Name_System) 

## Reverzní DNS
Zatímco IP adresa má na začátku obecné informace (adresu sítě), které se směrem doprava zpřesňují až k adrese počítače, doménové jméno má pořadí přesně opačné. 

Hledá-li například jméno k IP adrese 145.97.39.155, vytvoří dotaz na 155.39.97.145.in-addr.arpa. Obrácení IP adresy umožňuje delegovat správu reverzních domén odpovídajících sítím a podsítím správcům dotyčných sítí a podsítí

