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
|   Uložení jídel dané restaurace  |                      |
|  Ukládání hracích karet     |                      |
|  Ukládání odznaků     |          |
|   Uložení poznámky pro restauraci    |          |
|   Uložení zprávy o technickém problému    |          |
|       |          |



|   GET    |     Popis       |
|   ---    |           ---           |
|  Načtení doručovací adresy |          |
|  Změna jazyka  |                      |
|   Filtr výsledků    |        načte restaurace podle zadaných hodnot         |
| Načtení doporučených restaurací nebo obchodů | Načtení doporučení na míru uživateli |
|   Načtení hodnocení dané restaurace    |                    |
|   Načtení informací o uživateli   |                      |
|    Načtení slev   |                      |
|   Načtení náhodných restaurací či obchodů v sekci   |     |
|   Načtení dat uživatele    |                      |      
|   Načtení jídel dané restaurace    |                      |    
|  Načtení hracích karet     |                      |
|  Načtení odznaků     |          |  
|   Načtení poznámky od zákazníka    |          |  
|   Načtení restaurací nebo obchodů podle doručení či vyzvednutí  |                      |
|       |                      |

|   DELETE     |         Popis             |
|   ---    |           ---           |
|   Vymazat restauraci z oblíbených    |                      |
|   Vymazat uživatele    |                      |
|   Vymazat adresu    |                      |
|       |                      |

|   PUT    |          Popis            |
|   ---    |           ---           |
|   Změnit data uživatele    |                      |
|   Upravit doručovací adresu   |                      |
|   Zeměna objednávky    |                      |
|       |                      |




| CLASSES | |
|  ---  |         ---          |
| Košík |                      |
|   Modal |                      |




| OBJECTS | |
|  ---  |         ---          |
| Položka košíku |     |
|   Modal pro jednotlivé jídlo či zboží    |                      |


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
    Objednávka "1" *-- "*" PoložkaMenu
    Restaurace "1" *-- "*" PoložkaMenu
    Uživatel "0..*" --> "0..*" Restaurace
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