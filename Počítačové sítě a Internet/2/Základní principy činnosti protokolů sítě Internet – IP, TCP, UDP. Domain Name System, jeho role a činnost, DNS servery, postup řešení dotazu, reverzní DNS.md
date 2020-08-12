# Základní principy činnosti protokolů sítě Internet – IP, TCP, UDP. Domain Name System, jeho role a činnost, DNS servery, postup řešení dotazu, reverzní DNS.

### IP - Internet Protocol
Internet Protocol je v informatice základním protokolem pracujícím na síťové vrstvě používaným v počítačových sítích a Internetu. Sám o sobě neposkytuje záruky na přenos dat a rozlišuje pomocí IP adresy pouze jednotlivá síťová rozhraní. V současné době je stále ještě používána starší verze protokolu IPv4, nově se přechází na IPv6. 

## Funkce protokolu
Internet Protocol je zodpovědný za směrování datagramů (paketů) ze zdrojového počítače do cílového hostitele přes jednu nebo více IP sítí. Paket se skládá z řídících dat (metadat) a z uživatelských dat (užitečné zatížení, anglicky payload). Řídící data poskytují síti potřebná data k doručení paketu, například adresu zdroje a cíle, kódy pro detekci chyb – kontrolní součty a informace o pořadí. 
Data se v IP síti posílají po blocích nazývaných datagramy. Jednotlivé datagramy putují sítí zcela nezávisle, na začátku komunikace není potřeba navazovat spojení či jinak „připravovat cestu“ datům, přestože spolu třeba příslušné stroje nikdy předtím nekomunikovaly. 
IP v doručování datagramů poskytuje nespolehlivou službu, označuje se také jako best effort – „nejlepší úsilí“; tj. všechny stroje na trase se datagram snaží podle svých možností poslat blíže k cíli, ale nezaručují prakticky nic. Datagram vůbec nemusí dorazit, může být naopak doručen několikrát a neručí se ani za pořadí doručených paketů. Pokud aplikace potřebuje spolehlivost, je potřeba ji implementovat v jiné vrstvě síťové architektury, typicky protokoly bezprostředně nad IP (viz TCP). 
Pokud by síť často ztrácela pakety, měnila jejich pořadí nebo je poškozovala, výkon sítě pozorovaný uživatelem by byl malý. Na druhou stranu příležitostná chyba nemívá pozorovatelný efekt. Navíc se obvykle používá vyšší vrstva, která ji automaticky opraví. 

Zdroj: [Internet Protokol](https://cs.wikipedia.org/wiki/Internet_Protocol)

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
