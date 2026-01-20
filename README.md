# Ročníková práce: Upgrade operační paměti a údržba PC

**Autor:** [Šmehlík Tadeáš]  
**Školní rok:** 2025/2026  
**Téma:** Výměna RAM a kompletní vyčištění počítačové sestavy

## Úvod

Tématem mé ročníkové práce je hardwarová údržba osobního počítače, konkrétně rozšíření operační paměti (RAM) a důkladné vyčištění vnitřních komponent od prachu. Cílem je prodloužit životnost zařízení, zvýšit jeho výkon pro náročnější aplikace a snížit provozní teploty komponent.

Rozhodl jsem se pro tento projekt z praktických důvodů. Mnoho uživatelů podceňuje vliv prachu na chlazení a dopad nedostatečné kapacity RAM na plynulost systému. Touto prací chci demonstrovat správný postup manipulace s hardwarem a ověřit vliv čistoty PC na jeho teplotní charakteristiky.

## 1. Cíle ročníkové práce

### 1.1 Hardwarová část
* Vybrat kompatibilní paměťové moduly pro stávající základní desku.
* Bezpečně demontovat staré komponenty.
* Provést fyzické čištění chladičů, ventilátorů a filtrů pomocí stlačeného vzduchu.
* Správně nainstalovat nové moduly RAM (Dual Channel zapojení).
* Zajistit cable management pro lepší airflow (proudění vzduchu).

### 1.2 Softwarová část
* Vytvořit diagnostický skript v jazyce Python pro detekci parametrů paměti.
* Změřit teploty před a po vyčištění (Stress test).
* Ověřit stabilitu systému pomocí nástroje MemTest86.
* Nastavit XMP/DOCP profil v BIOSu pro maximální výkon pamětí.

### 1.3 Testování a vyhodnocení
* Porovnat využití RAM při běžné zátěži před a po upgradu.
* Analyzovat pokles teplot na procesoru a grafické kartě po vyčištění.

## 2. Teoretické pozadí

### 2.1 Operační paměť (RAM) a Dual Channel
RAM (Random Access Memory) slouží k dočasnému ukládání dat, se kterými procesor právě pracuje. Pro mou práci je klíčové pochopení technologie **Dual Channel**, která zdvojnásobuje datovou propustnost mezi řadičem paměti a paměťovými moduly. Aby tato technologie fungovala, je nutné osadit moduly do správných slotů na základní desce (obvykle sloty 2 a 4).

### 2.2 Problematika chlazení a prachu
Prach funguje jako tepelný izolant. Pokud zanese žebrování chladiče, ventilátor nedokáže efektivně odvádět teplo, což vede k tzv. **Thermal Throttlingu** – stavu, kdy procesor sníží svůj výkon, aby se nepoškodil přehřátím.

### 2.3 Elektrostatický výboj (ESD)
Při manipulaci s komponentami je nutné dbát na ochranu před statickou elektřinou, která může nenávratně poškodit citlivé čipy. V práci využívám antistatickou podložku nebo se pravidelně uzemňuji o kovovou část skříně.

## 3. Realizace a postup

### 3.1 Diagnostika před zásahem
Před otevřením skříně jsem použil vlastní Python skript (viz složka `src/`), který využívá knihovnu `psutil`. Tento skript mi vypsal:
* Celkovou kapacitu paměti.
* Využitou paměť v klidovém stavu.
* Frekvenci pamětí (pokud je dostupná přes OS).

### 3.2 Fyzické čištění
Proces čištění probíhal v několika krocích:
1. Odpojení PC od sítě a vybití kondenzátorů (stisk zapínacího tlačítka).
2. Demontáž grafické karty pro lepší přístup.
3. Vyfoukání prachu stlačeným vzduchem (směr ven ze skříně).
4. Čištění lopatek ventilátorů jemným štětcem (fixace lopatek proti roztočení).

### 3.3 Výměna RAM
Původní moduly (2x 8GB DDR4 2666 MHz) byly nahrazeny novými (2x 16GB DDR4 3200 MHz). Dbal jsem na slyšitelné "cvaknutí" zámků slotu, které indikuje správné dosednutí.

## 4. Softwarová část — Diagnostický nástroj

Součástí práce je skript `diagnostika.py`. Ten slouží k rychlému ověření, zda systém novou paměť detekoval správně, bez nutnosti instalace komplexních benchmarků třetích stran.

**Ukázka funkce skriptu:**
Skript načte systémová data a uloží report do souboru `report_ram.txt`, který obsahuje časovou značku, celkovou kapacitu a procentuální vytížení. To umožňuje snadné porovnání stavu "PŘED" a "PO".

## 5. Výsledky a stav projektu k pololetí

V této fázi mám:
* **Splněno:** Úspěšná výměna pamětí z 16GB na 32GB.
* **Splněno:** Počítač je zbaven prachu, teploty v klidu klesly o 4°C.
* **Splněno:** BIOS správně detekuje XMP profil na 3200 MHz.
* **Software:** Diagnostický skript funguje a generuje reporty.

Zatím chybí:
* Dlouhodobé testování stability při maximální zátěži (plánováno na další týdny).
* Výměna teplovodivé pasty na procesoru (plánováno do druhé části roku).

## 6. Závěr

Výměna RAM proběhla bez komplikací a systém vykazuje výrazně vyšší odezvu při multitaskingu. Fyzické vyčištění přispělo k tiššímu chodu ventilátorů. Projekt potvrdil, že i základní údržba má měřitelný dopad na výkon a kultivovanost chodu počítače.

## Citace

1. **Crucial.** *How to Install RAM.* Online. 2024. Dostupné z: https://www.crucial.com/articles/about-memory/how-to-upgrade-desktop-memory [cit. 2025-01-20].
2. **Linus Tech Tips.** *Stop Doing This To Your PC (Dust Cleaning Guide).* Online. YouTube, 2023. Dostupné z: https://www.youtube.com/ [cit. 2025-01-20].
3. **Python Software Foundation.** *psutil documentation.* Online. 2025. Dostupné z: https://psutil.readthedocs.io/ [cit. 2025-01-20].
4. **GOOGLE.** Gemini [software]. Verze z 20. ledna 2026. Mountain View: Google, 2026.
