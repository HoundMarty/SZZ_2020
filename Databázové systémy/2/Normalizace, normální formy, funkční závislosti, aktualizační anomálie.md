# Normalizace, normální formy, funkční závislosti, aktualizační anomálie.

## Normální formy
* Množina pravidel pro správnou strukturu datového modelu
* Proces takové úpravy -> **NORMALIZACE**
* Snahou je omezit nadbytečnost (redundanci) a závislosti, což usnadňuje napr. modifikaci dat.
* Obvykle je databáze normalizovaná do 3. normální formy, ale existuje jich více.

### 1. normální forma
Všem atributům jsou jako jejich domény přiřazeny pouze atomické (nedělitelné) typy, neopakují se atributy stejného typu
![první NF příklad](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Datab%C3%A1zov%C3%A9%20syst%C3%A9my/imgs/prvni_NF.PNG "První normálová forma")

### 2. normálová forma
###### **Pro splnění 2NF musí být schéma v 1NF.**
* Každý neklíčový atribut je plně závislý na každém kandidátním klíči.
* Schéma nesmí obsahovat žádné částečné závislosti neklíčových atributů na kandidátním klíči (každá neklíčová hodnota musí záviset na celém klíči).
* Zavedením jednoduchých klíčů a splněním 1NF lze jednoduše dosáhnout 2NF.

![druhá NF příklad](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Datab%C3%A1zov%C3%A9%20syst%C3%A9my/imgs/druha_NF.PNG "Druhá normálová forma")

### 3. normálová forma
###### **Pro splnění 3NF musí být schéma v 2NF.**
* Dále nesmí být žádný neklíčový atribut tranzitivně závislý na žádném kandidátním klíči schématu (nesmí záviset na jiném neklíčovém atributu).
* Všechny neklíčové atributy musí být vzáemně nezávislé.
* Pro zavedení 3NF se často vytváří číselníky.

![třetí NF příklad](https://github.com/HoundMarty/SZZ_2020-21/blob/master/Datab%C3%A1zov%C3%A9%20syst%C3%A9my/imgs/treti_NF.PNG "Třetí normálová forma")

[//]: # (https://akela.mendelu.cz/~xturcin0/naOstro/Navrh_databaze.pdf <- zdroj)
