# Webové aplikace – charakteristika programování na straně serveru a klienta. Základy jazyka JavaScript. DOM a přístup k prvkům stránky. Jazyk PHP. Problematika uchovávání stavových informací, cookies.

## Charakteristika programování na straně serveru
 * Skripty jsou vykonávány na straně serveru, 
	* Skript reaguje na vstup od klienta a není nikdy odeslán od webového prohlížeče
	* Nejznámější jazyky: PHP, NodeJS, ASP.NET, Python

## Charakteristika programování na straně klienta
	* Klient si v rámci načtení webové stránky stáhne i skripty ze serveru
	* Kód skriptu si může uživatel zobrazit
	* Není vyžadován dodatečný SW na serveru(výhoda u externích hostingů)

## JavaScript
	* Objektově orientovaný skpriptovací jazyk 
	* Interpretaci jazyka provádí webový prohlížeč
	* Slabě typované proměnné - je jedno co do ní uložíme
	* Podporuje if, while, loops, switch, do while
	* Místo tříd používá prototypování - dají se dělat téměř stejné věci jako s třídou, jen v případě dědičnosti nebo vytváření nových instancí se bavíme o tzv. klonování původního objektu - prototypu
 *(Nejdůležitějším rozdílem mezi dědičností založenou na třídách a prototypech je, že třída definuje typ, který lze vytvořit za běhu, zatímco prototyp je sám instancí objektu)*
 
 ## DOM: - Document Object Model
	* Multiplatformní na jazyku nezávislé rozhraní, kde HTML nebo XML je reprezentováno jako stromová struktura, kde každý uzel je objekt, který reprezentuje část daného dokumentu
	* Jedná se o objektově orientovanou reprezentaci webové stránky, která může být modifikována skriptem
 
 ![DOM stromová struktura](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/DOM_tree.png)
 
## Přístup k prvkům stránky:
Ty jsou dostupné díky API  
Pokud použijeme document nebo window elementy, v tu chvíli přistupujeme k DOM elementu  
Laicky řečeno, pokud chceme pomocí JavaScriptu cokoliv měnit na webové stránce, nebo z ní něco dostat, přistupujeme k DOM elemetnu  

Zdroj: (https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

Ukázka: 
![Interakce s DOM elementy](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Po%C4%8D%C3%ADta%C4%8Dov%C3%A9%20s%C3%ADt%C4%9B%20a%20Internet/imgs/DOM_interaction.png)

## PHP: - Hypertext Preprocessor, původním názvem Personal Home Page
Při použití PHP pro dynamické stránky jsou skripty prováděny na straně serveru – k uživateli je přenášen až výsledek jejich činnosti.   
Interpret PHP skriptu je možné volat pomocí příkazového řádku, dotazovacích metod HTTP nebo pomocí webových služeb  
 * Jazyk PHP je dynamicky typován - tzn. že datový typ proměnné je vázán na hodnotu, nikoliv na proměnnou.
	* PHP podporuje reference, pomocí kterých lze do proměnných ukládat odkazy na libovolnou jinou proměnnou, nebo i prvek jejího poleý, tzn. že datový typ proměnné je vázán na hodnotu, nikoliv na proměnnou.
	* Rozsáhlý soubor funkcí v základní knihovně PHP 
	* Nativní podpora mnoha databázových systémů, 

## Problematika uchovávání stavových informací, cookies
Aby server nemusel držet veškeré informace o klientovi, jeho předvolby na webové stránce, jeho nákupní košík apod., pro snížení zátěže serverů byl v 90. letech vytvořen systém cookies.  
HTTP cookie je soubor, ve kterém lze ukládat libovolná data, která vývojáři jednotlivých webových stránek se rozhodnou ukládat  
Jsou navrženy tak, aby si webová stránka pamatovala nejrůznější informace, ať už se jedná o uživatelské přihlášení, nákupní košík, různá nastavení na webu, vyplněné formuláře apod. Prakticky lze ale do nich uložit téměř cokoliv.  

### Druhy Cookies
Session Cookie  
Persistent cookie  
Secure Cookie  
Same-Site Cookie  
Third-party cookie  
SuperCookie  
Cookie wall  

### Vytvoření cookie:
Cookies jsou nastavovány pomocí HTTP hlavičky Set-Cookie zaslané v HTTP response od serveru.
Ukázka odpovědi serveru:
> HTTP/1.0 200 OK
> Content-type: text/htm 
> Set-Cookie: theme=light
> Set-Cookie: sessionToken=abc123; Expires=Wed, 09 Jun 2021 10:18:14 GMT

### Z čeho se skládá cookie:
1. Jméno  cookie/proměnné 
2. hodnota 
3. Atributy - volitelná položka - Atributy ukládají informace, jako je platnost souboru cookie, doména, flagy apod.

### Attributy cookie
 Ty používají prohlížeče k určení, kdy odstranit soubor cookie, zablokovat soubor cookie nebo zda odeslat soubor cookie na server. Nejsou součástí dat, která se odesílají na server, tam se posílá jen název cookie a hodnota.




