# Model Aplikace pro rozvozce pizzy
## O aplikaci
Aplikce bude rozšířením pro již fungující systém v podniku s prodejem pizzy. Tato mobilní aplikace bude napojená na databázi všech objednávek a rozvozci si budou vybírat objednávky, které povezou. 
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
**UR4** Aplikace musí používat vložení adresy pomocí hlasu.<br>
**UR5** Aplikace musí mít dostupnou nápovědu 'návod na ovládání'.</br>

### Reliability
**RR1** Aplikace se musí obnovovat jednou za 20 sekund.<br>
**RR2** Systém musí být zabezpečený proti ztrátě dat, nebo corrupted data --> Integrita dat.<br>
**RR3** Systém si musí udržovat naposledy načtená data i po výpadku internetového připojení. Po výpadku internetu se nesmí zobrazit bílá obrazovka.<br>
**RR4** Systém musí mít implementovaný návrat k poslednímu funkčnímu stavu.<br>

### Performance
**PR1** Systém musí být mobile device friendly --> nevyužívat mnoho baterie při práci na pozadí.<br>
**PR2** Systém musí být škálovatelný, např. přidání nové provozovny se stejným systémem.<br>
**PR3** Systém musí mít rychlou odezvu na server.<br>

### Supportability
**SR1** Aplikace musí mít dokumentaci.<br>
**SR2** Error feedback od uživatelů, v případě chyby.<br>
**SR3** Pravidelné zálohování dat.<br>


![use case diagram](https://github.com/ricardoboh/swi_project/blob/main/use_case_pic.png?raw=true)
</br></br>

## Use case scenarios
**Title:** Zaznamenání odchodu</br>
**Actors:** Rozvozce</br>
**Trigger:** Rozvozce klikne na tlačítko v aplikaci.</br>
**Pre-condition:** Rozvozce musí být přihlášen a musí mít zaznamenaný příchod.</br>
**Post-condition:** Rozvozcovi musí být vypočítána mzda.</br>
**Minimal guaranties:** V aplikaci vyskočí pop-up okno s vypočítanou mzdou.</br>
**Main success:**</br>
&emsp;&emsp;&emsp;&emsp;1. Uživatel zaznamená odchod.</br>
&emsp;&emsp;&emsp;&emsp;2. Čas se uloží do databáze.</br>
&emsp;&emsp;&emsp;&emsp;3. Zaměstnancovi je vypočítána mzda a vyskočí pop-up okno.</br></br>
**1a.**: Čas příchodu je stejný, jako čas odchodu.</br>
&emsp;&emsp;*1.a1* - Uživateli je sděleno, že čas, který zadal není v souladu s jeho pracovní dobou.</br>
&emsp;&emsp;*1.a2* - Čas se neuloží do databáze.</br>
&emsp;&emsp;*1.a3* - Zaměstnancovi není vypočítána mzda a pop-up okno nevyskočí.</br>
**3a.**: Zaměstnancova hodinová sazba je 0,-</br>
&emsp;&emsp;*3.a1* Účetní, nebo managerovi se odešle výzva k nastavení mzdy.</br>
&emsp;&emsp;*3.a2* Use case pokračuje dál, s výslednou mzdou 0,-</br>
</br>
</br>

**Title:** Přidání adresy na trasu</br>
**Actors:** Rozvozce</br>
**Trigger:** Rozvozce zadá adresu rozvozu.</br>
**Pre-condition:** Rozvozce musí být přihlášen.</br>
**Minimal guaranties:** V aplikaci se adresa přidá do seznamu adres.</br>
**Main success:**</br>
&emsp;&emsp;&emsp;&emsp;1. Rozvozce zadá adresu rozvozu.</br>
&emsp;&emsp;&emsp;&emsp;2. Vypočítá se nejlepší možná trasa.</br>
&emsp;&emsp;&emsp;&emsp;3. Seznam adres je přeuspořádán vzhledem k nejrychlejšímu času doručení.</br>
&emsp;&emsp;&emsp;&emsp;4. Use-case se opakuje do té doby, než uživatel klikne na začít rozvoz.</br></br>
**1a.**: Rozvozce zadal stejnou adresu, kterou již v seznamu má.</br>
&emsp;&emsp;*1.a1* - Uživateli vyskočí info a zeptá se, jestli adresu chce přidat podruhé.</br>
&emsp;&emsp;&emsp;&emsp;*1.a2.ANO* - Pokračuje se v use case 2. krokem</br>
&emsp;&emsp;&emsp;&emsp;*1.a2.NE* - Pokračuje se v use case 1. krokem</br>
</br>
**1b.**: Rozvozce zadal neplatnou adresu, která neexistuje.</br>
&emsp;&emsp;*1.b1* - Uživateli vyskočí upozornění, že adresa není platná.</br>
&emsp;&emsp;*1.b2* - Uživateli se nabídne korekce adresy, pokud existuje.</br>
&emsp;&emsp;*1.b3* - Use case pokračuje 1. krokem.</br>
</br>
**1c.**: Rozvozce zadal neúplnou adresu. (chybí číslo popisné)</br>
&emsp;&emsp;*1.c1* - Uživateli vyskočí upozornění, že adresa není úplná.</br>
&emsp;&emsp;*1.c2* - Uživateli se nabídne korekce adresy, pokud existuje.</br>
&emsp;&emsp;*1.c3* - Use case pokračuje 1. krokem.</br>
</br>
**2a.**: Není možné vypočítat trasu. (lesy, polní cesty atd..)</br>
&emsp;&emsp;*2.a1* - Uživateli vyskočí upozornění, že není možné vypočítat trasu, ale je mu ukázána mapa s možností "drop a pin to closest road" a rozvozce tak místo adresy zadá souřadnice.</br>
&emsp;&emsp;*2.a2* - Use case pokračuje 2. krokem.</br>
</br>
**3a.**: Rozvozce chce pořadí upravit podle sebe</br>
&emsp;&emsp;*3.a1* - Rozvozci je umožněno přeuspořádat si adresy podle sebe.</br>
&emsp;&emsp;*3.a2* - Use case pokračuje 4. krokem, ale již bez 3. kroku.</br>
</br>

![activity diagram](https://github.com/ricardoboh/swi_project/blob/main/activity_diagram_swi.png?raw=true)
