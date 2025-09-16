# CSS Selectory i XPath - Praktyczny przewodnik
---
## Wprowadzenie
- CSS Selectory i XPath to dwa najpopularniejsze sposoby lokalizowania elementów
- Każda metoda ma swoje zalety i zastosowania
- Zrozumienie obu jest kluczowe dla efektywnej automatyzacji
---
## CSS Selektory - podstawy
### Podstawowe selektory:
```html
<div class="container">
    <p id="title">Tytuł</p>
    <input type="text" name="username">
</div>
```

- `#title` - po ID (najszybsze)
- `.container` - po klasie (często używane)
- `input` - po nazwie tagu (zbyt ogólne)
- `[name="username"]` - po atrybucie (dokładne)
---

### Zaawansowane selektory CSS:
```html
<div class="form">
    <div class="input-group">
        <label>Email:</label>
        <input type="email" class="form-control">
        <span class="error">Błąd</span>
    </div>
</div>
```

- Kombinatory:
  - `div > input` - bezpośredni potomek
  - `div input` - dowolny potomek
  - `label + input` - następny element
  - `label ~ input` - kolejny element tego samego rodzica
---
## XPath - struktura i funkcje
### Podstawowa składnia:
```html
<form id="loginForm">
    <div class="form-group">
        <input type="text" name="username">
        <input type="password" name="password">
    </div>
</form>
```

- Ścieżki:
  - `/html/body/form` - ścieżka bezwzględna (unikać!)
  - `//form` - dowolny form na stronie
  - `//input[@type="text"]` - input o zadanym atrybucie
  - `//form[@id="loginForm"]//input` - input wewnątrz forma
---
### Zaawansowane funkcje XPath:
- Operatory:
  - `and`, `or`, `not()` - operatory logiczne
  - `contains()`, `starts-with()` - funkcje tekstowe
  - `last()`, `position()` - funkcje pozycji

```xpath
//button[contains(text(), 'Zaloguj')]
//input[not(@disabled)]
//tr[position() > 1]
```

### Osie XPath:
- `parent::` - rodzic
- `child::` - dzieci
- `following-sibling::` - następne elementy
- `preceding-sibling::` - poprzednie elementy
- `ancestor::` - przodkowie
- `descendant::` - potomkowie
---
## Praktyczne tworzenie selektorów
### Narzędzia Chrome DevTools
1. Otwórz DevTools (F12)
2. Użyj selektora elementów (strzałka)
3. Eksperymentuj w konsoli:
```javascript
// Testowanie CSS Selektorów
$$('.my-class') 
$$('input[name="username"]')

// Testowanie XPath
$x('//input[@name="username"]')
$x('//button[contains(text(), "Login")]')
```
---
### Optymalizacja selektorów:
1. Szukaj unikalnych atrybutów:
   - ID jest najlepsze
   - Łącz atrybuty dla większej precyzji
   - Unikaj indeksów i pozycji

2. Testuj odporność na zmiany:
   - Sprawdź przy różnych stanach strony
   - Weryfikuj przy różnych danych
   - Testuj na różnych rozdzielczościach

3. Debugowanie:
   - Użyj konsoli do szybkich testów
   - Sprawdź, czy selektor jest unikalny
   - Weryfikuj wydajność selektora
---
## Ćwiczenia praktyczne
### Ćwiczenie 1: Analiza struktury
1. Otwórz stronę demo Selenium
2. Znajdź wszystkie pola formularza
3. Napisz dla każdego:
   - Selektor CSS
   - XPath
   - Porównaj ich czytelność
--
### Ćwiczenie 2: Selektory dynamiczne
1. Znajdź elementy generowane dynamicznie
2. Napisz selektory odporne na zmiany
3. Przetestuj przy różnych stanach strony
--
### Ćwiczenie 3: Debugowanie
1. Celowo napisz niepoprawny selektor
2. Użyj DevTools do znalezienia problemu
3. Napraw i zoptymalizuj selektor

---
## Podsumowanie i dobre praktyki
1. Wybór metody:
   - CSS dla prostych przypadków
   - XPath dla złożonych scenariuszy
--
2. Optymalizacja:
   - Używaj ID gdy możliwe
   - Unikaj bezwzględnych ścieżek
   - Testuj na różnych stanach
--
3. Utrzymanie:
   - Dokumentuj skomplikowane selektory
   - Regularnie weryfikuj działanie
   - Aktualizuj przy zmianach w aplikacji