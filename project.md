# System aukcyjny

## Wprowadzenie

Specyfikacja wymagań funkcjonalnych w ramach informatyzacji procesu sprzedaży produktów w oparciu o mechanizm aukcyjny. 

## Procesy biznesowe

---
<a id="bc1"></a>
### BC1: Sprzedaż aukcyjna 

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2)

**Opis:** Proces biznesowy opisujący sprzedaż za pomocą mechanizmu aukcyjnego. |

**Scenariusz główny:**
1. [Sprzedający](#ac1) wystawia produkt na aukcję. ([UC1](#uc1))
2. [Kupujący](#ac2) oferuje kwotę za produkt wyższą od aktualnie najwyższej oferty. ([BR1](#br1))
3. [Kupujący](#ac2) wygrywa aukcję ([BR2](#br2))
4. [Kupujący](#ac2) przekazuje należność Sprzedającemu. ([BR3](#br3))
5. [Sprzedający](#ac1) przekazuje produkt Kupującemu. ([UC3](#uc3))

**Scenariusze alternatywne:** 

2.A. Oferta Kupującego została przebita, a [Kupujący](#ac2) pragnie przebić aktualnie najwyższą ofertę.
* 2.A.1. Przejdź do kroku 2.

3.A. Czas aukcji upłynął i [Kupujący](#ac2) przegrał aukcję. ([BR2](#br2))
* 3.A.1. Koniec przypadku użycia.

---

## Aktorzy

<a id="ac1"></a>
### AC1: Sprzedający

Osoba oferująca towar na aukcji.

<a id="ac2"></a>
### AC2: Kupujący

Osoba chcąca zakupić produkt na aukcji.

<a id="ac3"></a>
### AC3: System

System sprawdzający, poprawność danych i ogólna obsluga aukcji.

## Przypadki użycia poziomu użytkownika

### Aktorzy i ich cele

[Sprzedający](#ac1):
* [UC1](#uc1): Wystawienie produktu na aukcję
* [UC2](#uc2): Podanie danych produktu i ceny
* [UC3](#uc3): Przekazanie produktu kupujacemu

[Kupujący](#ac2)
* [BR1](#br1): Oferowanie najwyzszej oferty za produkt na ukcji
* [BR2](#br2): Wygrana aukcji
* [BR3](#br3): Przekazanie naleznosci sprzedajacemu


[System](#ac3)
* [SY1](#sy1): Prosba o podanie przez sprzedajacego danych produktu i ceny
* [SY2](#sy2): Weryfikacja poprawnosci danych
* [SY3](#sy3): Poinformowanie o wystawieniu produktu na aukcje
---
<a id="uc1"></a>
### UC1: Wystawienie produktu na aukcję

**Aktorzy:** [Sprzedający](#ac1)

**Scenariusz główny:**
1. [Sprzedający](#ac1) zgłasza do systemu chęć wystawienia produktu na aukcję.   ([UC1](#uc1))
2. System prosi o podanie danych produktu i ceny wywoławczej.([SY1](#sy1))
3. [Sprzedający](#ac1) podaje dane produktu oraz cenę wywoławczą. ([UC2](#uc2))
4. System weryfikuje poprawność danych. ([SY1](#sy1))
5. System informuje o pomyślnym wystawieniu produktu na aukcję. ([SY1](#sy1))

**Scenariusze alternatywne:** 

5.A. Podano niepoprawne lub niekompletne dane produktu.
* 5.A.1. System [System](#ac3) informuje o błędnie podanych danych.
* 5.A.2. Przejdź do kroku 2.

---

<a id="uc2"></a>
### UC2: Sprawdzenie statusu akcji

**Aktorzy:** [Sprzedający](#ac1), [Kupujący](#ac2), ...

**Scenariusz główny:**
1. [Sprzedający](#ac1) lub [Kupujący](#ac2) zgłasza chęć sprawdzenia statusu aukcji.
2. System przeszukuje aktywne aukcje.
3. System wyświetla aktualny stan aukcji, w tym aktualną najwyższą ofertę i czas pozostały do zakończenia.
**Scenariusze alternatywne:** 

4.A. **Brak aktywnej aukcji.**
   * 4.A.1. System informuje, że nie ma aktywnych aukcji do wyświetlenia.

---

## Obiewkty biznesowe (inaczje obiekty dziedzinowe lub informatycjne)

### BO1: Aukcja

Aukcja jest formą zawierania transakcji kupna-sprzedaży, w której Sprzedający określa cenę wywoławczą produktu, natomiast Kupujący mogą oferować własną ofertę zakupu każdorazowo proponując kwotę wyższą od aktualnie oferowanej kwoty. Aukcja kończy się po upływie określonego czasu. Jeśli złożona została co najmniej jedna oferta zakupy produkt nabywa ten Kupujący, który zaproponował najwyższą kwotę. 

### BO2: Produkt

Fizyczny lub cyfrowy obiekt, który ma zostać sprzedany w ramach aukcji.

## Reguły biznesowe

<a id="br1"></a>
### BR1: Złożenie oferty

Złożenie oferty wymaga zaproponowania kwoty wyższej niż aktualnie oferowana o minimum 1,00 PLN.


<a id="br2"></a>
### BR2: Rozstrzygnięcie aukcji

Aukcję wygrywa ten z [Kupujący](#ac2)ch, który w momencie jej zakończenia (upłynięcia czasu) złożył najwyższą ofertę.

## Macierz CRUDL


| Przypadek użycia                                  | Aukcja | Produkt | ... |
| ------------------------------------------------- | ------ | ------- | --- |
| UC1: Wystawienia produktu na aukcję               |    C   |    C    | ... |
| ???                                               |  ...   |  ...    | ... |


