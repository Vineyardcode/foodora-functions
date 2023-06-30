| BACKEND | Popis |
|---|---|

| API CALLS | 
|---|

| POST | Popis |
|   ---    |           ---           |
| Registrace | Zaregistruje uzivatele  |
| Login | Přihlášení uživatele  |
| Hodnocení restaurace nebo obchodu |   |
| Přidání restaurace nebo obchodu do oblíbených |   |
| Uložení doručovací adresy |   |
| Uložení minulých objednávek |                      |
| Uložení jídel dané restaurace  |                      |
| Ukládání hracích karet     |                      |
| Ukládání odznaků     |          |
| Uložení poznámky pro restauraci    |          |
| Uložení zprávy o technickém problému    |          |
| Přidání položky do košíku | |


|   GET    |     Popis       |
|   ---    |           ---           |
| Načtení doručovací adresy | |
| Změna jazyka | |
| Filtr výsledků | Načte restaurace či obchody podle zadaných hodnot |
| Načtení doporučených restaurací nebo obchodů | Načtení doporučení na míru uživateli |
| Načtení hodnocení dané restaurace | |
| Načtení informací o uživateli | |
| Načtení slev | |
| Načtení náhodných restaurací či obchodů v sekci | |
| Načtení dat uživatele | |
| Načtení jídel dané restaurace | |
| Načtení hracích karet | |
| Načtení odznaků | |
| Načtení poznámky od zákazníka | |
| Načtení restaurací nebo obchodů podle doručení či vyzvednutí | |
| Načtení položek košíku | |
| Načtení modálního okna pro jednotlivé jídlo či zboží | |


| DELETE | Popis |
| --- | --- |
| Vymazat restauraci z oblíbených | |
| Vymazat uživatele | |
| Vymazat adresu | |


| PUT | Popis |
| --- | --- |
| Změnit data uživatele | |
| Upravit doručovací adresu | |
| Změna objednávky | |


| CLASSES | |
| --- | --- |
| Uživatel | |
| Restaurace | |
| Obchod | |
| Jídlo | |
| Košík | |
| Adresa | |
| Objednávka | |
| Hodnocení | |
| Sleva | |
| Hrací karta | |
| Odznak | |
| Poznámka | |
| Modální okno | |


| FRONTEND | Popis |
|-------------------------|-------|
| Registrace uživatele    | Umožňuje uživatelům vytvořit nový účet a poskytnout potřebné informace, jako je jméno, e-mail a heslo. |
| Přihlášení uživatele    | Umožňuje uživatelům přihlásit se do svého účtu pomocí přihlašovacích údajů. |
| Vyhledávání restaurací  | Poskytuje funkci vyhledávání, která umožňuje uživatelům najít restaurace na základě různých kritérií, jako je poloha, kuchyně nebo název restaurace. |
| Prohlížení menu         | Zobrazuje restaurační menu s kategoriemi a položkami, které umožňují uživatelům procházet dostupné možnosti jídla. |
| Objednávání jídla       | Umožňuje uživatelům vybrat položky z menu, určit množství, přidat speciální instrukce a zadat objednávky. |
| Správa nákupního košíku | Umožňuje uživatelům zobrazit a spravovat svůj nákupní košík, včetně přidání nebo odebrání položek, úpravy množství a výpočtu celkové ceny objednávky. |
| Proces objednávky       | Poskytuje plynulý a intuitivní proces objednávání, který umožňuje uživatelům zkontrolovat své objednávky, vybrat možnosti doručení nebo vyzvednutí, zadat doručovací adresy a vybrat platební metody. |
| Sledování objednávky    | Zobrazuje aktualizace stavu provedených objednávek v reálném čase, jako je potvrzení objednávky, příprava a postup doručení. |
| Správa uživatelského profilu | Umožňuje uživatelům zobrazit a aktualizovat informace v jejich uživatelském profilu, včetně jména, kontaktních údajů, doručovacích adres a platebních preferencí. |
| Historie objednávek     | Poskytuje sekci s historií, kde uživatelé mohou zobrazit své předchozí objednávky, včetně detailů, jako jsou položky objednávky, celková cena a informace o doručení/vyzvednutí. |
| Hodnocení a recenze     | Umožňuje uživatelům hodnotit a recenzovat restaurace nebo konkrétní jídla, poskytující zpětnou vazbu a doporučení ostatním uživatelům. |
| Notifikace              | Odesílá uživatelům oznámení týkající se aktualizací objednávek, akcí, slev nebo speciálních nabídek. |
| Lokalizace jazyka       | Poskytuje možnost přepínání mezi různými jazyky, aby se uspokojily uživatele z různých regionů. |
| Pomoc a podpora         | Nabízí sekci s podporou nebo kontaktními informacemi, kde uživatelé mohou vyhledat pomoc nebo nahlásit problémy týkající se objednávek, plateb nebo používání aplikace. |



| DOMÉNOVÝ MODEL | |
|  ---  |         ---          |

```mermaid
classDiagram
    class Uživatel {
        - ID uživatele
        - jméno
        - kontaktní informace
        - adresa
    }

    class Restaurace {
        - ID restaurace
        - název
        - typ kuchyně
        - umístění
        - kontaktní informace
    }

    class PoložkaMenu {
        - ID položky
        - název
        - popis
        - cena
        - dietní informace
    }

    class Objednávka {
        - ID objednávky
        - ID uživatele
        - ID restaurace
        - dodací adresa
        - stav objednávky
        - celková cena
    }

    class Doručovatel {
        - ID doručovatele
        - jméno
        - kontaktní informace
        - dostupnost
    }

    class Platba {
        - ID platby
        - platební metoda
        - stav transakce
        - celková částka
    }

    class Hodnocení {
        - ID hodnocení
        - ID uživatele
        - hodnocení
        - komentáře
        - datum
    }

    class Akce {
        - ID akce
        - popis
        - platnost
        - procentuální sleva
    }

    Uživatel --|> Objednávka
    Objednávka "1" *-- "many" PoložkaMenu
    Restaurace "1" *-- "many" PoložkaMenu
    Uživatel "many" --> "many" Restaurace
    Objednávka -- Doručovatel
    Uživatel --|> Platba
    Uživatel --|> Hodnocení
    Restaurace -- Akce

    class Uživatel {
        + registrace()
        + login()
        + vyhledatRestaurace()
        + přidatDoKošíku()
        + provéstObjednávku()
        + sledovatStavObjednávky()
        + zrušitObjednávku()
        + přidatHodnocení()
    }

    class Restaurace {
        + přijmoutObjednávku()
        + spravovatAkce()
    }

    class Doručovatel {
        + aktualizovatStavDoručení()
    }