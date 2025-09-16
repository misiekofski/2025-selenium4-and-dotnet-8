# Ćwiczenia praktyczne z Selenium
---
## Wprowadzenie
- Zestaw praktycznych ćwiczeń z wykorzystaniem stron testowych
- Każde ćwiczenie rozwija konkretne umiejętności automatyzacji
- Strony z the-internet.herokuapp.com to stabilne środowisko testowe

> Notatka: Zachęć kursantów do eksperymentowania i modyfikowania przykładów.
---
## Ćwiczenie 1: Shifting Content - Menu
**Strona:** `https://the-internet.herokuapp.com/shifting_content/menu?mode=random`

### Zadanie:
- Napisz test, który sprawdzi, czy wszystkie elementy menu są dostępne
- Uwzględnij, że pozycje menu mogą się zmieniać

```csharp
[Test]
public void TestShiftingMenu()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/shifting_content/menu?mode=random");
    
    // TODO: Znajdź wszystkie elementy menu
    // TODO: Sprawdź czy zawierają oczekiwane teksty
    // TODO: Kliknij w losowy element i zweryfikuj nawigację
}
```
--
### Wskazówki:
- Użyj `FindElements()` dla listy elementów
- Sprawdź tekst każdego elementu menu
- Zastanów się nad selektorami odpornymi na zmiany pozycji
---
## Ćwiczenie 2: Shifting Content - Lista
**Strona:** `https://the-internet.herokuapp.com/shifting_content/list`

### Zadanie:
- Zweryfikuj wszystkie elementy listy
- Sprawdź, czy lista zawiera oczekiwaną liczbę elementów

```csharp
[Test]
public void TestShiftingList()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/shifting_content/list");
    
    // TODO: Znajdź wszystkie elementy listy
    // TODO: Sprawdź liczbę elementów
    // TODO: Zweryfikuj zawartość tekstową każdego elementu
}
```
--
### Wskazówki:
- Zwróć uwagę na dynamiczną naturę contentu
- Użyj Assert.That() do weryfikacji liczby elementów
- Przeanalizuj strukturę HTML listy
---
## Ćwiczenie 3: Infinite Scroll
**Strona:** `https://the-internet.herokuapp.com/infinite_scroll`

### Zadanie:
- Zaimplementuj automatyczne scrollowanie
- Zlicz liczbę załadowanych paragrafów

```csharp
[Test]
public void TestInfiniteScroll()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/infinite_scroll");
    
    var actions = new Actions(driver);
    int initialCount = driver.FindElements(By.ClassName("jscroll-added")).Count;
    
    // TODO: Zaimplementuj scrollowanie w pętli
    // TODO: Dodaj czekanie na załadowanie nowego contentu
    // TODO: Sprawdź czy liczba paragrafów wzrosła
}
```
--
### Wskazówki:
- Użyj `Keys.PageDown` lub `Keys.End`
- Dodaj `Thread.Sleep()` lub WebDriverWait
- Sprawdź różnicę w liczbie elementów przed i po scrollowaniu
---
## Ćwiczenie 4: Tabele
**Strona:** `https://the-internet.herokuapp.com/tables`

### Zadanie:
- Przeanalizuj strukturę tabel
- Znajdź konkretne dane w tabeli

```csharp
[Test]
public void TestTables()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/tables");
    
    // TODO: Znajdź tabelę
    // TODO: Wyciągnij nagłówki kolumn
    // TODO: Znajdź wiersz z konkretnym imieniem (np. "John")
    // TODO: Sprawdź wartość w konkretnej kolumnie dla tego wiersza
}
```
--
### Wskazówki:
- Użyj XPath do nawigacji po tabeli
- `//table//tr[contains(td, 'John')]` - znajdź wiersz z tekstem
- `//table//tr[1]//th` - znajdź nagłówki
- Rozważ utworzenie pomocniczej metody do wyszukiwania w tabeli
---
## Ćwiczenie 5: Challenging DOM
**Strona:** `https://the-internet.herokuapp.com/challenging_dom`

### Zadanie:
- Przetestuj interakcję z dynamicznie generowanymi elementami
- Sprawdź funkcjonalność przycisków

```csharp
[Test]
public void TestChallengingDOM()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/challenging_dom");
    
    // TODO: Znajdź i kliknij każdy z trzech przycisków
    // TODO: Sprawdź czy strona się odświeża/zmienia
    // TODO: Zweryfikuj zawartość tabeli
    // TODO: Przetestuj linki "edit" i "delete" w tabeli
}
```
--
### Wskazówki:
- Przyciski mają dynamiczne ID - użyj innych selektorów
- Sprawdź Canvas element - czy się zmienia?
- Tabela ma linki akcji - przetestuj je
- Zwróć uwagę na zmiany w URL po kliknięciach
---
## Ćwiczenie 6: JavaScript Errors
**Strona:** `https://the-internet.herokuapp.com/javascript_error`

### Zadanie:
- Wykryj błędy JavaScript na stronie
- Przetestuj obsługę błędów w teście

```csharp
[Test]
public void TestJavaScriptErrors()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/javascript_error");
    
    // TODO: Sprawdź logi przeglądarki pod kątem błędów JS
    // TODO: Zweryfikuj czy strona się załadowała pomimo błędów
    // TODO: Przetestuj różne sposoby wykrywania błędów
}
```
--
### Wskazówki:
- Użyj DevTools do sprawdzenia błędów: `driver.GetDevToolsSession()`
- Sprawdź `driver.Manage().Logs.GetLogEntries(LogType.Browser)`
- Rozważ, czy błędy JS powinny powodować failure testu
---
## Dodatkowe wyzwania
### Wyzwanie 1: Robust Test Suite
- Połącz wszystkie ćwiczenia w jeden test suite
- Dodaj setup/teardown dla każdego testu
- Zaimplementuj retry mechanism dla niestabilnych testów

### Wyzwanie 2: Reporting
- Dodaj screenshoty do każdego testu
- Stwórz HTML report z wynikami
- Dodaj mierzenie czasu wykonania testów

### Wyzwanie 3: Page Object Model
- Przepisz testy używając wzorca POM
- Stwórz osobne klasy dla każdej strony
- Dodaj wspólną klasę bazową dla wszystkich stron

> Notatka: Zachęć kursantów do dzielenia się rozwiązaniami i dyskusji o różnych podejściach.