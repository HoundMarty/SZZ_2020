# Základní principy WWW, HTTP, HTML. Jazyk (X)HTML, jeho charakteristika, možnosti a omezení. CSS – vlastnosti, hodnoty, dědění, kaskádování. Blokový model CSS

## Základní principy WWW
World Wide Web je označení pro systém prohlížení, ukládání a odkazování dokumentů nacházejících se v internetu. Je postaven na hypertextových odkazech. 

### Princip komunikace
1. The browser goes to the DNS server, and finds the real address of the server that the website lives on (you find the address of the shop).
2. The browser sends an HTTP request message to the server, asking it to send a copy of the website to the client (you go to the shop and order your goods). This message, and all other data sent between the client and the server, is sent across your internet connection using TCP/IP.
3. If the server approves the client's request, the server sends the client a "200 OK" message, which means "Of course you can look at that website! Here it is", and then starts sending the website's files to the browser as a series of small chunks called data packets (the shop gives you your goods, and you bring them back to your house).
4. The browser assembles the small chunks into a complete web page and displays it to you (the goods arrive at your door — new shiny stuff, awesome!).

(https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works> )

### Dotazovací metody
GET - Požadavek na uvedený objekt se zasláním případných dat (proměnné prohlížeče
HEAD - Metoda podobná GET, avšak nepředává data. Poskytne pouze metadata o požadovaném cíli (velikost, typ, datum změny, …).
POST Odesílá uživatelská data na server.
PUT - Nahraje data na server. Objekt je jméno vytvářeného souboru. Používá se velmi zřídka, pro nahrávání dat na server se běžně používá FTP nebo SCP/SSH
DELETE - Smaže uvedený objekt ze serveru.
TRACE - Odešle kopii obdrženého požadavku zpět odesílateli, takže klient může zjistit, co na požadavku mění nebo přidávají servery, kterými požadavek prochází.
OPTIONS - Dotaz na server, jaké podporuje metody.
CONNECT - Spojí se s uvedeným objektem přes uvedený port. Používá se při průchodu skrze proxy pro ustanovení kanálu SSL.

"Bezpečné metody" - tj. metody které jsou pouze read only - GET, HEAD, OPTIONS, TRACE

### Verze HTTP
HTTP/1.0
	- Naprostý základ, pouze GET, HEAD, POST
HTTP/1.1
	- Přidány nové metody 
	- Optimalizace
HTTP/2.0
	- Velká optimalizace pro multimédia
HTTPS
	- Secure verze, používá SSL/TLS pro šifrování komunikace

## HTML
Jazyk HTML je charakterizován množinou značek (tzv. tagů) a jejich vlastností (atributů) definovaných pro danou verzi

Vývoj jazyka především v 90. letech
HTML4 = rok 1997, HTML5 = rok 2014

##Dokument v jazyku HTML má předepsanou strukturu
	* Deklarace typu dokumentu – značka <!DOCTYPE html> sděluje prohlížeči, že otevřel HTML dokument.
	* Kořenový element – prvek html (značky <html> a </html>) – reprezentuje celý dokument.
	* Hlavička dokumentu – prvek head (značky <head> a </head>) – obsahuje metadata, která se vztahují k celému dokumentu. Definuje např. kódování, název dokumentu, autora, popis, klíčová slova, titulek dokumentu nebo kaskádové styly.
	* Tělo dokumentu – prvek body (značky <body> a </body>) – zahrnuje vlastní obsah dokumentu

#### Parsování HTML
1. Dokument je nejprve prohlížečem načítán a rozkládán (tzv. syntaktická analýza) na jednotlivé prvky
2. Každému prvku je poté přiřazen styl (způsob zobrazení)
3. Na dokument je dále aplikován předepsaný kód skriptovacích jazyků
4. Takto zpracovaný dokument je na závěr vykreslen uživateli

## XHTML - Extensible Hypertext markup language
	* Byl zamýšlen jako nástupce HTML4
	* V XHTML na rozdíl od HTML musí být ukončené všechny tagy včetně nepárových
	* Dokument musí začínat XML deklarací
	* Je více důsledný na zápis a vyžaduje větší "disciplánu/řád" než HTML
  
 ## CSS - Cascading style sheets
Jazyk pro popis způsobu zobrazení elementů na stránkách napsaných v jazycích HTML, XHTML nebo XML. Hlavním smyslem je umožnit návrhářům oddělit vzhled dokumentu od jeho struktury a obsahu

### Výhody/možnosti:
	- Rozsáhlé možnosti formátování
	- Oddělení struktury a stylu, možnost cachování stylů
	- Vlastnosti elementů lze měnit pomocí javascriptu a jiných jazyků
	- Lze s ním formátovat i XML
	- Přizpůsobení vizuálu zařízení

### Nevýhody:
	- Každý prohlížeč může CSS překládat jinak - v Chromu to funguje v IE nikoliv apod.

### Limity:
	- CSS neposkytuje možnost pro symbolický zápis proměnné nebo konstanty, všechny hodnoty musí být vepsány přímo v kódu
	- Omezení na 4096 selectorů ve starších verzích prohlížečů
	- Žádné cykly nebo programování
	- Nelze procházet strom elementů pozpátku
  
### CSS Selector
  * Výběr elementu, který chceme stylovat
  ![CSS Selectory - ukázka](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/CSS_Selectors.png)
 
### Hodnoty:
Každý blok deklarací pak obsahuje deklarace oddělené středníky ; a každá deklarace sestává z identifikátoru vlastnosti, následuje dvojtečka : a hodnota vlastnosti

### Dědění vs Kaskádování
Tagy dědí styl od nadřazených prvků- z rodiče na potomka (ne všechny elementy mohou dědit - například border)
Kaskáda je popis vlastností aplikovaných na konkrétní tag

#### Kaskádu v CSS definují tři pravidla:
	1. pořadí rozhoduje a poslední vyhrává
	2. selektor s vyšší váhou (specificitou) vyhrává
	3. pravidlo označené jako důležité (!important) vyhrává
  
  (https://www.vzhurudolu.cz/prirucka/css-dedicnost)

## Blokový model CSS:
Celá stránka se skládá z boxů/bloků
Typickým příkladem je třeba <div>, <p>, <ul>, <li>

![Blokový model obr. 1](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/Blokovy_model_css.png)

![Blokový model obr. 2](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/Blokovy_model_2_css.png)

V podstatě jde o možnosti Možnosti "marginu", paddingu, velikosti a umístění boxů




