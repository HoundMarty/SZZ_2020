# Vzorkování, kvantování. Vzorkovací teorém. Aliasing. Práce se zvukem na počítači.
Analogový signál - spojitý v čase (prostoru) a hodnotách - je převeden na číslicový signál - definovaný pouze v některých časových (prostorových) bodech a nabývající pouze konečného počtu hodnot.

**Dvě základní operace** Vzorkování a kvantování

## Vzorkování
- Vzorkování je proces diskretizace spojitého signálu.

![Vzorkování signálu](https://user-images.githubusercontent.com/29363626/119259663-8f326100-bbcf-11eb-8c0b-d7e30e8ad636.png)

## Kvantování
- Převedení jednoho vzorku z vzorkování na diskrétní hodnotu.
- **Lineární kvantování** - jednotlivé úrovně jsou od sebe stejně vzdáleny
- **Nelineární kvantování** -  vzdálenost mezi úrovněmi je různá

![Kvantování](https://user-images.githubusercontent.com/29363626/119260720-50eb7080-bbd4-11eb-803a-d68c7bbf7199.png)

### Vzorkování i Kvantování ztrácí informaci

## Vzorkovací teorém
- **Podmínka vzorkování** - vzorkovací frekvence musí být alespoň 2 x vyšší než nejvyšší frekvence obsažená ve vzorkovaném signálu.
- Při splnění vzorkovacího teorému nedojde k Aliasiangu.

### Poznámky k AD převodu
Po převedení různých fyzikálních veličin do bezrozměrných čísel hrozí problém ztráty informace o původním významu signálu
Je proto nutné zvlášť uchovat údaje o 
- Původní veličině
- Původních jednotkách a jejich převodním  vztahu
- Vzorkovací frekvenci
- Čase snímání

## Aliasing

![Aliasing](https://user-images.githubusercontent.com/29363626/119261123-36b29200-bbd6-11eb-8e7b-e95e091bc4e5.png)

### Antialiasing 
Před A/D převodník vložit speciální obvod **antialiasingový filtr**, který nepropustí složky o frekvencích vyšších než f<sub>s</sub>/2 (tzv. dolní propust).
## Práce se zvukem na PC
- Nástroje umožňující práci se signálem
- programovací jazyky
- převodníky
- zvukové karty
- WAV: používá strukturu RIFF, nekomprimované
- ztrátová komprese: MP3; bezztrátová komprese: FLAC
