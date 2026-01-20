# Ročníková práce: Hardwarový upgrade a údržba PC

**Autor:** Šmehlík Tadeáš
**Třída:** T3A 
**Školní rok:** 2025/2026  
**Téma:** Výměna operační paměti RAM a čištění chladicího systému

## Úvod

Tématem mé ročníkové práce je údržba a vylepšení mého stolního počítače. Konkrétně jsem se zaměřil na rozšíření operační paměti (RAM) a vyčištění vnitřku skříně od prachu.

Pro toto téma jsem se rozhodl, protože můj počítač už při hraní novějších her a současně spuštěném prohlížeči začínal ztrácet dech. Často docházelo k zásekům způsobeným nedostatkem paměti. Navíc se počítač v zátěži více zahříval a byl hlučný, což naznačovalo zanesené chladiče. Cílem je tedy zrychlit systém a snížit provozní teploty.

## 1. Cíl projektu

### 1.1 Hardwarová část
* Vybrat správný typ pamětí kompatibilní s mojí základní deskou (DDR3).
* Bezpečně rozebrat PC a zbavit ho prachu (kompresor/stlačený vzduch).
* Vyměnit starý 4GB modul za nové 4x 4GB (celkem 16GB).
* Zapojit paměti do správných slotů pro funkci Dual Channel.
* Zlepšit "cable management" (uspořádání kabelů) pro lepší průtok vzduchu.

### 1.2 Softwarová část
* Zapnout v BIOSu profil XMP (DOCP), aby paměti běžely na deklarované frekvenci 1550 MHz.
* Otestovat stabilitu systému v zátěži (stress test).

### 1.3 Testování
* Porovnat teploty procesoru v klidu a v zátěži.
* Ověřit, zda systém vidí celou kapacitu paměti.

## 2. Teoretické pozadí

### 2.1 Operační paměť (RAM)
RAM je superrychlá paměť, kam si procesor ukládá data, se kterými zrovna pracuje. Když dojde, systém musí používat pomalý disk (tzv. swapování), což způsobuje sekání her i aplikací.
Důležité je zapojení **Dual Channel**. To znamená, že když osadíme dva moduly do správných slotů (většinou 2. a 4. slot od procesoru), zdvojnásobí se šířka pásma a tím i rychlost přenosu dat.

### 2.2 Chlazení a prach
Prach je nepřítel elektroniky. Funguje jako izolant – teplo se drží na chladiči a ventilátor ho nedokáže odfouknout. Komponenty se pak přehřívají a snižují výkon (thermal throttling), aby se nepoškodily. Čistý počítač = tichý a výkonný počítač.

### 2.3 Statická elektřina (ESD)
Než sáhnu na komponenty, musím se "uzemnit" (např. sáhnout na topení nebo nenalakovanou část skříně). Statická elektřina by mohla odpálit citlivé čipy na pamětech nebo desce.

## 3. Realizace (Hardware)

### 3.1 Čištění
Počítač jsem odpojil ze sítě a podržel zapínací tlačítko, abych vybil kondenzátory. Vzal jsem ho na balkon a profoukl stlačeným vzduchem.
* **Důležité:** Při foukání do ventilátorů jsem je držel prstem. Kdyby se roztočily moc rychle, mohly by fungovat jako generátor a poslat proud zpátky do desky, nebo si zničit ložiska.

### 3.2 Výměna RAM
Původní 4GB Ram DDR3 1500 MHz jsem vyndal. Nové (2x 4GB DDR3 1600 MHz) + (2x 4GB DDR3 1550 MHz) jsem zacvakl do slotů DIMM_A2 a DIMM_B2. Musí být slyšet jasné cvaknutí, jinak tam paměť nesedí správně.

### 3.3 BIOS
Po prvním spuštění běžely paměti jen na základních 1333 MHz. Musel jsem jít do BIOSu a zapnout **XMP Profile 1**, čímž se frekvence zvedla na 1550 MHz a upravilo se časování.

### 3.4 Komplikace s Dual Channel zapojením
Při osazování všech čtyř slotů (2x 1600MHz a 2x 1550MHz) nastala komplikace. Po prvním zapnutí mi systém ukazoval použitelných 6,3 GB

**Problém:** Po diskuzi s chatbotem jsem zjistil že problém dělají rozdílné MHz obou druhů Ram

**Řešení:**
1. Musel jsem moduly v paticích přeházet tak, aby v 1. a druhém slotu byly stejné druhy Ram a v 3. a 4. také stejné druhy
2. V BIOSu jsem musel ručně "podtaktovat" (Underclock) celé rozhraní na jednotnou frekvenci 1550 MHz

## 4. Softwarová část — Můj skript

Abych nemusel spoléhat jen na Správce úloh ve Windows, napsal jsem si v Pythonu skript `ram_monitor.py`. Používá knihovnu `psutil`.
Pomohl jsem si pomocí AI

Díky tomu mám přesný důkaz, jak na tom PC byl před výměnou a jak je na tom teď.

## 5. Stav projektu k pololetí

Aktuálně mám hotovou hardwarovou část i software pro měření.
* **Výměna:** Úspěšná, systém ukazuje 14,8 GB použitelné paměti.
* **Čištění:** Teploty grafiky klesly v zátěži o cca 5 °C. Počítač už nehučí.


V druhém pololetí chci ještě zkusit přetaktovat procesor, když mám teď lepší teploty, a dodělat hezčí grafy z naměřených dat v Excelu.

## Zdroje
* Alza.cz: *Jak vybrat operační paměť RAM*
* YouTube kanál *Linus Tech Tips*: Guide to PC cleaning
* Dokumentace knihovny *psutil* pro Python

## Citace
* How To Install Ram - Step By Step Installation Guide (SUPER EASY) https://youtu.be/tv2ZWRePx5U?si=ECzq3Yhy0rweapMa
* 1024 tutoriálů: #0004 Výměna/přidání RAM pamětí https://youtu.be/c0SSqD4lLgA?si=LD4QR8mdR_WqL5CT
* Jak vyčistit počítač? Moje oblíbené tipy. https://youtu.be/SIzVZHXeZzI?si=BtyZEFVihCOAaV2S
* BIOS - Jak a co nastavit? https://youtu.be/o6aZnWuBgNc?si=AFimnN77LamVOWKE
* https://gemini.google.com/app
