# Ćwiczenia praktyczne z Selenium
--
## Wprowadzenie
- Zestaw praktycznych ćwiczeń z wykorzystaniem stron testowych
- Każde ćwiczenie rozwija konkretne umiejętności automatyzacji
- Strony z the-internet.herokuapp.com to stabilne środowisko testowe

--
## Ćwiczenie 1: Shifting Content - Menu
**Strona:** `https://the-internet.herokuapp.com/shifting_content/menu?mode=random`

### Zadanie:
- Napisz test, który sprawdzi, czy wszystkie elementy menu są dostępne
- Spróbuj w nie kliknąć po kolei w pętli
--
### Wskazówki:
- Użyj `FindElements()` dla listy elementów
- Sprawdź tekst każdego elementu menu
- Zastanów się nad selektorami odpornymi na zmiany pozycji
--
## Ćwiczenie 2: Shifting Content - Lista
**Strona:** `https://the-internet.herokuapp.com/shifting_content/list`

### Zadanie:
- Zweryfikuj wszystkie elementy listy
- Sprawdź, czy lista zawiera oczekiwaną liczbę elementów

--
### Wskazówki:
- Zwróć uwagę na dynamiczną naturę contentu
- Użyj Assert.That() do weryfikacji liczby elementów
- Przeanalizuj strukturę HTML listy
--
## Ćwiczenie 3: Infinite Scroll
**Strona:** `https://the-internet.herokuapp.com/infinite_scroll`

### Zadanie:
- Zaimplementuj automatyczne scrollowanie
- Zlicz liczbę załadowanych paragrafów
--
### Wskazówki:
- Użyj `Keys.PageDown` lub `Keys.End`
- Dodaj `Thread.Sleep()` lub WebDriverWait
- Sprawdź różnicę w liczbie elementów przed i po scrollowaniu
--
## Ćwiczenie 4: Tabele
**Strona:** `https://the-internet.herokuapp.com/tables`

### Zadanie:
- Przeanalizuj strukturę tabel
- Znajdź konkretne dane w tabeli
--
### Wskazówki:
- Użyj XPath do nawigacji po tabeli
- `//table//tr[contains(td, 'John')]` - znajdź wiersz z tekstem
- `//table//tr[1]//th` - znajdź nagłówki
- Rozważ utworzenie pomocniczej metody do wyszukiwania w tabeli
--
## Ćwiczenie 5: Challenging DOM
**Strona:** `https://the-internet.herokuapp.com/challenging_dom`

### Zadanie:
- Przetestuj interakcję z dynamicznie generowanymi elementami
- Sprawdź funkcjonalność przycisków
--
### Wskazówki:
- Przyciski mają dynamiczne ID - użyj innych selektorów
- Sprawdź Canvas element - czy się zmienia?
- Tabela ma linki akcji - przetestuj je
- Zwróć uwagę na zmiany w URL po kliknięciach
--
## Ćwiczenie 6: JavaScript Errors
**Strona:** `https://the-internet.herokuapp.com/javascript_error`

### Zadanie:
- Wykryj błędy JavaScript na stronie
- Przetestuj obsługę błędów w teście
--
### Wskazówki:
- Użyj DevTools do sprawdzenia błędów: `driver.GetDevToolsSession()`
- Sprawdź `driver.Manage().Logs.GetLogEntries(LogType.Browser)`
- Rozważ, czy błędy JS powinny powodować failure testu