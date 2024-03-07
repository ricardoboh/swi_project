# Model Aplikace pro rozvozce pizzy
## O aplikaci
Aplikce bude rozšířením pro podnik s prodejem pizzy. Tato mobilní aplikace bude napojená na centrální databázi všech objednávek a rozvozci si budou vybírat objednávky, které povezou. 
## Na začátku
Když rozvozce příjde do práce, přihlásí se do aplikce a bude mu přiděleno identifikační číslo R.n pod kterým se bude identifikovat pro další rozvozce. Na začátku každé směny rozvozce do aplikace zaklikne příchod poté, co si orazí štípačku v práci.
## Fungování aplikace
### Výběr objednávky
Seznam objednávek bude seřazen od té, která přišla nejdříve po tu, která přišla jako poslední.
Každý rozvozce bude mít na výběr z několika objednávek a jestliže si nějakou objednávku bude chtít vzít, klikne na tlačítko přidat do trasy --> tím se u objednávky připíše identifikační číslo, aby ostatní rozvozáci viděli, že objednávka je již zabraná.
Každá objednávka by u sebe měla mít před jakou dobou byla objednána a tento čas by se měl stále aktualizovat, aby rozvozce viděl, jak moc má s objednávkou spěchat, popřípadě změnit pořadí objednávek.
### Průběh rozvozu
Tím, že rozvozce zakliknul 'přidat do trasy' --> se adresa objednávky přidá na seznam objednávek a Google APY vypočítají nejlepší (nejkratší) cestu, jakou lze adresy objet.Jakmile Rozvozce bude mít všechny objednávky, se kterými pojede, zaklikne tlačítko 'Vyrazit na cestu' po tomto již nebude možné přidávat do cesty další objednávky. Dále bude umožňovat označit objednávku jako hotovou, po tom, co ji rozvozák doveze člověku, co objednávku vytvořil. 
### Error handling
Aplikace musí mít funkci vrátit všechny objednávky do fronty, kvůli nečekané události, jako (autonehoda, nemoc řidiče). 
Objednávku by mělo jít stornovat, protože si ji daný člověk nevyzvedl, aby nebylo možné objednávky záměrně stornovat a peníze si nechávat, u každé stornované objednávky je potřeba uvést důvod, proč byla objednávka stornována.
## Na konci
Na konci každé směny každý rozvozce bude moci zakliknout odchod a aplikace spočítá, kolik peněz má rozvozce odevzdávat firmě. Aplikace vypočítá na minuty, kolik minut byl rozvozce v práci, aby bylo jasné kolik si za ten den vydělal, poté už záleží na domluvě, jestli se rozvozce vyplatí na místě, nebo až na výplatě.

 

## FURPS model

### Functionality
**FR1** Aplikace musí správně využívat GPS.<br>
**FR2** Aplikace musí být napojena na databázi objednávek.<br>
**FR3** Aplikace musí umožnit doručovateli vidět objednávky z databáze.<br>
**FR4** Aplikace musí umožnit změnu označení "v přepravě", "čeká na doručovatele", "v přípravě".<br>
**FR5** Aplikace musí umět udělat storno objednávky z databáze (aby na storno nebylo potřeba volat někoho jiného).<br>

### Usability
**UR1** Aplikace musí mít noční režim.<br>
**UR2** Aplikace musí být jednoduchá, ideálně jedna hlavní pracovní plocha s objednávkami.<br>
**UR3** Aplikace musí používat barvy k označení stavu objednávky.<br>

### Reliability
**RR1** Aplikace se musí obnovovat jednou za 20 sekund.<br>
**RR2** Systém musí být zabezpečený proti ztrátě dat, nebo corrupted data --> Integrita dat.<br>
**RR3** Systém si musí udržovat naposledy načtená data i po výpadku network... Po výpadku internetu se nesmí zobrazit bílá obrazovka.<br>

### Performance
**PR1** Systém musí být mobile friendly --> nevyužívat mnoho baterie při práci na pozadí.<br>
**PR2** Systém musí být škálovatelný, např. přidání nové provozovny se stejným systémem.<br>
**PR3** Systém musí mít rychlou odezvu na server --> Edison volení rozvrhu.<br>

### Supportability
**SR1** Aplikace musí mít dokumentaci.<br>
**SR2** Error feedback od doručovatelů, v případě chyby.<br>
**SR3** Pravidelné zálohování dat.<br>




