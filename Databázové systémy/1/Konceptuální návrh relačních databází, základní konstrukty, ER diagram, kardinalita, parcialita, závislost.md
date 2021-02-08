# Konceptuální návrh relačních databází, základní konstrukty, ER diagram, kardinalita, parcialita, závislost.

## Konceptuální návrh
* Popisuje jak funguje nebo bude fungovat reálný problém -> Přesně popisuje potřeby uchování dat.
* Podporuje diskuzi a komunikaci se zadavatelem -> předchází nedorozumění a chybám.
* Orientuje se na entity a jejich vztahy
* Neřeší implementaci! Pouze se snaží vystihnout kompletní problematiku.

### Základní konstrukty
Konceptuální model obsahuje názvy, vazby a atributy entity.

## Entita
Představuje objekt/osobu/věc, okterých je potřeba uchovávat informace zaznamenávané podle skutečnosti.

Například: FILM,ZVÍŘE,ZAMĚSTNANEC.

|   Entita   	|   Instance   	|
|:----------:	|:------------:	|
|    Osoba   	| Pepa Jehličí 	|
| Zaměstnání 	|   Závozník   	|
|   Výrobek  	|     Pivo     	|

## Atributy
Blíže popisují vlastnosti entit i vztahů.
* Kvantifikují příslušnou entitu.
* Kvalifikují příslušnou entitu.
* Zařazují a zpřesňují příslušnou entitu.
Nabývá hodnot z určité **domény**. Je jím právě jedna hodnota, číslo, řetězec,datum,obrázek,zvuk,... z příslušné **domény(datového typu)**.
Integritní omezení jsou pak přídavná pravidla pro zajištění souladu modelu s modelovanou realitou.

### Atributy - příklad
* OSOBA
  * jméno             řetězec obsahující písmena
  * příjmení          řetězec obsahující písmena
  * datum narození    datum
  * pohlaví           muž nebo žena
  * email             formátovaný řetězec

## Vztahy
Představují propojení jednotlivých entit. Vždy existují mezi dvěma entitami (entita může mít i vztah sama mezi sebou). Vztah je vždy pojmenová na obou svých stranách.

### Vztahy příklad
**STUDENT** (entita) **STUDUJE** (vztah) **PŘEDMĚT** (entita)

**PŘEDMĚT** (entita) **JE STUDOVÁN** (vztah) **STUDENTEM** (entita)

[//]: # (koment?)
[//]: # (příklad ER diagramu)
![ERD ukázka](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Datab%C3%A1zov%C3%A9%20syst%C3%A9my/imgs/ERD%20uk%C3%A1zka.PNG "ERD ukázka")

* Každý
* zaměstnanec (entita)
* musí (plná čára)
* pracovat (jméno vazby)
* v právě jednom (jednoduchá čára)
* oddělení (entita)

## Kardinalita
Popisuje, kolikrát se každá instance dané entity může účstanit daného typu vazby.
* Máme 3 druhy
  * 1:1
  * 1:N
  * M:N

*Poznámka* Vazby M:N jsou později dekomponovány na tzv. průnikový typ entity, neboli asociační entitu, protože je nelze realizovat v relační databázi.
 
 [//]: # (dorazit parialitu a závislost s konkrétním a přehledným příkladem) 
