# PRVNÍ CVIČENÍ

### *Co je hlavním motivem pro vývoj programovacího paradigmatu od imperativního k objektovému?*<br/>
 `Evoluce` v IT, lidé potřebovali řešit nové problémy především z hlediska znovupoužitelnosti, nebo dědičnosti. Potom také evoluce programovacích jazyků a trendů.<br/>

### *Co je imperativní programování?*<br/>
Programovací paradigma, které `programujeme pro počítač` 'v jeho jazyku, aby tomu rozuměl'. Je to set instrukcí, jak vyřešit daný problém.<br/>

### *Co je modulární programování?*<br/>
Návrh kódu `rozdělený do` jednotlivých funkcí `modulů`, které jsou nezávislé a zaměnitelné. Tyto moduly zajišťují `dílčí funkčnost programu`.<br/>

### *Jaké jsou hlavní kvality software?*<br/>
- **Vnitřní** - Jak vše funguje... (skryté uživateli)<br/>
- **Vnější** - Popisuje chování navenek... (správnost, robusnost)
funkce printf(...)nevíme, jak přesně funguje, co se v ní děje, ale víme, že když tam vložíme string, vypíše se do terminálu.<br/>

### *Co je pochopitelnost modulu? Uveďte příklad.*<br/>
Modul by měl vykonávat `1 jasně definovanou` a pochopitelnou `funkci`.<br/>
***PŘÍKLAD:***<br/>
Funkce na spočítání výsledku sčítání dvou čísel.<br/>
```c
int sum(int n1, int n2) {
    return n1+n2;
}
```

### *Co je  samostatnost modulu? Uveďte příklad.*<br/>
Modul by měl být relativně samostaný, `co nejmenší počet vazeb na ostatní moduly`.<br/>
***PŘÍKLAD:***<br/>
Funkce na dealokaci paměti.<br/>
```c
void myFree(void *pointer) {
    free(pointer);
}
```

### *Co je kombinovatelnost modulu? Uveďte příklad.*<br/>
Moduly musí být `kombinovatelné mezi sebou` a být použitelné i v jiném kontextu.<br/>
***PŘÍKLAD:***<br/>
Funkce na spočítání násobení dvou sčítanců (v C lang). Modul pro vytvoření tlačítka v GUI<br/>
```c
int sum(int n1, int n2) {
    return n1+n2;
}

int multiply(int s1, int s2) {
    return s1*s2;
}

multiply(sum(1,3), sum(2,4));
```

### *Co je zapouzdření modulu? Uveďte příklad.*<br/>
Moduly skrývají to, co pro klienta není potřebné (většina funkcionality je v praxi skryyta a jen malá část je viditelná).<br/>
- **Skrytá část** --> `Implementace` modulu<br/>
- **Veřejná část** --> `Interface`, využitelné funkce, metody a proměnné k další manipulaci.

***PŘÍKLAD:***<br/>
Databáze v reálném životě, jako uživatel nevidíme jak se vše propojené, co je #id atd...<br/>

### *Co je explicitní rozhraní modulu? Uveďte příklad.*<br/>
Z deklarace modulu `musí být zřejmé`, `co potřebujeme`, k správné funci modulu.<br/>
***PŘÍKLAD:***<br/>
Funkce na vypočítání mocniny. <br/>
```c
int power(int base, int power) {
    int result = 1;
    if(power != 0) {
        for(int i = 0; i < power; i++) {result *= base;}
    }
    return result;
}
```

### *Co je syntaktická podpora modularity?*<br/>
Ze zápisu musí být jasné, kde zápis `modulu začíná a` kde `končí`.<br/>

### *Co je pět kritérií modularity?*<br/>
**DEKOMPONOVATELNOST<br/>
KOMBINOVATELNOST<br/>
POCHOPITELNOST<br/>
KONTINUITA<br/>
OCHRANA<br/>**

### *Co je pět pravidel zajišťujících dobrou modularitu?*<br/>
Pravidla, která `napomáhají` udržet kód v rámci `pěti kritérií modularity`.<br/><br/>
**PŘÍMÉ MAPOVÁNÍ<br/>
PÁR ROZHRANÍ<br/>
MALÁ ROZHRANÍ<br/>
EXPLICITNÍ ROZHRANÍ<br/>
SKRÝVÁNÍ INFORMACÍ**

### *Popište jednotlivá kritéria modularity. Uveďte příklady.*
1. **DEKOMPONOVATELNOST**<br/>Software lze `rozdělit` na několik `menších problémů`, spojených `jendoduchou strukturou` tak, aby byly samostatné. 
PŘÍKLAD:
Eshop produkt v košíku.

2. **KOMBINOVATELNOST**<br/>Prvky software se dají `kombinovat` za účelem tvorby `nového software`.<br/> 
***PŘÍKLAD:***<br/>
Funkce na spočítání násobení dvou sčítanců.

3. **POCHOPITELNOST** <br/>Software, ve kterém se i `jiný vývojář` `lehce zoorientuje`.<br/>
***PŘÍKLAD:***<br/>
Správné pojmenování proměnných

4. **KONTINUITA**<br/>Software ve kterém `malá změna modulu` neovlivní celkový program, ale `ovlivní` jen jeden konkrétní, nebo `jen málo jiných modulů`.<br/>
***PŘÍKLAD:***<br/>
Kalendář --> změna barvy jednotlivých eventů

5. **OCHRANA**<br/>Software, ve kterém `chyba v jednom` modulu `nevyvolá chybu v dalších` modulech.<br/>
***PŘÍKLAD:***<br/>
Corupted data zapsané v databázi, webová stránka nespadne, nebo se neobjeví error, jen se vypíší nesmyslné data.

### *Popište jednotlivá pravidla pro dobrou modularitu. Uveďte příklady.*<br/>
1. **PŘÍMÉ MAPOVÁNÍ**<br/>Struktura realizovaného software by `měla zůstat stejná`, jako struktura při `plánování realizace a modelování`.<br/>
***PŘÍKLAD:***<br/>
Databáze definovaná vazbami, předem určenými v návrhu databáze.

2. **PÁR ROZHRANÍ**<br/>Každý modul by měl `komunikovat s` pár `dalšími`.<br/>
***PŘÍKLAD:***<br/>
Funkce printf("%s", stringModule); v C lang. Komunikuje se všemi moduly, které vrací string.

3. **MALÁ ROZHRANÍ**<br/>Jestliže dva `moduly` spolu `komunikují`, měly by si `vyměňovat co nejméně` informací.<br/>
***PŘÍKLAD:***<br/>
Pro vypsání výsledku programu, funkce nemusí znát všechny proměnné, jen ty, které potřebuje ke své činnosti.

4. **EXPLICITNÍ ROZHRANÍ**<br/>Když modul A komunikuje s modulem B, musí být alespoň z jednoho modulu `zřejmé, že spolu komunikují`.<br/>
***PŘÍKLAD:***<br/>
Na webové aplikaci, když se uživatel přihlašuje a poté vidí svůj profil, intuitivně pozná, že stránka pro přihlašování komunikuje s uživatelským profilem.

5. **SKRÝVÁNÍ INFORMACÍ**<br/>Designer modulu musí určit části, které jsou `dostupné i pro ostatní vývojáře`.<br/>
***PŘÍKLAD:***<br/>
Třídy v OOP, private and public sections.

### *K čemu je konstruktor? Uveďte příklad.*
Konstruktor inicializuje data objektu hodnotami parametrů v konstruktoru. (`Naplní paměť daty`)<br/>
***PŘÍKLAD:***
```cpp
className *konstructor = className(2, 10);
```

### *K čemu je destruktor? Kdy ho potřebujeme a kdy ne? Uveďte příklad.*
Destruktor `uvolňuje paměť od konstruktorů`, které již nejsou potřeba.
Destruktor *nepotřebujeme, když jsou data statická*, používáme ho jedině, když třídu ukládáme, jako pointer.<br/>
***PŘÍKLAD:***<br/>
```cpp
className *konstructor = className(2, 10);
del konstruktor;
```

# DRUHÉ CVIČENÍ

### *Co je hlavními příčinami změn software?*<br/>
`Přidávání nových funkcí` softwaru, `Oprava chyb`, nebo errorů, které byli v předchozích verzích, `Zlepšení designu`, úprava legacy code, `Optimalizace` stávajícího software.

### *Jaké jsou hlavní faktory ovlivňující objektovou orientovanost?*<br/>
`Metoda a jazyk`, přehlednost kódu `Implementace a prostředí`, nástroje pro vývoj `Knihovny`, opakovatelná použitelnost.

### *Vysvětlete, co rozumíme pojmy objektově orientovaná metoda (přístup) a jazyk.*<br/>
Jde o veškeré `textové, či grafické materiály`, které jsou spojeny se software, je to způsob uvažování nad problémem, ale také způsob vyjadřování. 

### *Vysvětlete, co rozumíme podporou objektově orientované implementace.*<br/>
Programovací jazyk, nebo framework, který je schopen `poskytovat nástroje a mechanismy` pro efektivní práci s objekty a OOP koncepty.  

### *Vysvětlete, co rozumíme podporou opakované použitelnosti.*<br/>
Softwarové komponenty jsou navrženy tak, aby bylo možné je oddělit od ostatních a také je kombinovat s ostatními --> `modularita a kombinovatelnost` knihovna pro práci s databázemi.

### *Vysvětlete pojmy třída a objekt a použijte správnou terminologii.*<br/>
`TŘÍDA` je část softawaru, která popisuje `abstraktní datový typ` objekty se `společným chováním reprezentovaným seznamem operací`, které umí vykonávat.
`OBJEKT` je konkrétní instance dané třídy, která má svoji vlastní sadu dat a může vykonávat metody v třídě.

### *Zdůrazněte vlastnosti třídy z pohledu modularity.*<br/>
Třídy by měly být `samostané` a `kombinovatelné` s ostatními. Třída by měla `zapouzdřovat` své interní detaily, což znamená, že k proměnné key se dostaneme jen přes GetKey() funkci. `Opakované použití`, což znamená `knihovny`.

### *Vysvětlete princip zapouzdření v OOP.*<br/>
Třída `skrývá` informace o svých proměnných, k proměnné `key` se dostaneme jen přes funkci GetKey(). Zvyšuje úroveň abstrakce a izolace. --> Volání metody, ne proměnné.

### *Vysvětlete princip zasílání zpráv.*<br/>
Je to výpočetní mechanismus, zaslána zpráva daného jména a s potřebnými parametry
```cpp
aPerson.ChangeLastName("Charles");
```

### * Vysvětlete principy deklarace a definice jednoduché třídy v C++.*<br/>
`Deklarace` je Popis třídy s proměnnými a metodami, které ve třídě můžeme použít.<br/>
`Definice (implementace)` je popis jednotlivých metod, které se ve třídě nacházejí. Konstruktor, destruktor atd..
