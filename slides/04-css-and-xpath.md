# CSS Selectory i XPath w Selenium
---
## Wprowadzenie
- CSS Selectory i XPath to dwa najpopularniejsze sposoby lokalizowania elementów na stronie.
- Pozwalają na precyzyjne wskazanie elementu w strukturze HTML.

> Notatka: Zrozumienie selektorów to podstawa skutecznej automatyzacji.
---
## Budowa CSS Selectora
- Selektor CSS opisuje ścieżkę do elementu na podstawie klas, ID, atrybutów i hierarchii.

### Przykłady:
```html
<input id="login" class="form-input" type="text" name="username">
<button class="btn primary" type="submit">Zaloguj</button>
```
- Po ID: `#login`
- Po klasie: `.form-input`
- Po atrybucie: `input[name='username']`
- Po klasie i typie: `button.btn.primary[type='submit']`
- Zagnieżdżenie: `form .btn`
---
## Budowa XPath
- XPath opisuje ścieżkę do elementu w strukturze XML/HTML.
- Może być absolutny lub względny.

### Przykłady:
```html
<div>
  <form>
    <input id="login" type="text" name="username">
    <button type="submit">Zaloguj</button>
  </form>
</div>
```
- Po ID: `//input[@id='login']`
- Po nazwie: `//input[@name='username']`
- Po typie: `//button[@type='submit']`
- Po tekście: `//button[text()='Zaloguj']`
- Zagnieżdżenie: `//form//button`
---
## Tworzenie własnych selektorów
- Analizuj strukturę HTML w narzędziach developerskich przeglądarki (F12).
- Szukaj unikalnych atrybutów (`id`, `name`, `class`).
- Łącz selektory dla większej precyzji.
- Unikaj zbyt ogólnych ścieżek (np. długich XPath od `<html>`).
---
## Kopiowanie selektorów w przeglądarce
- W Chrome/Edge/Firefox kliknij prawym na element → "Kopiuj" → "Kopiuj XPath" lub "Kopiuj selektor CSS".
- Uwaga: Automatycznie wygenerowane selektory mogą być zbyt szczegółowe lub podatne na zmiany strony.
- Najlepiej używać ich jako punktu wyjścia i modyfikować według potrzeb.
---
## Ćwiczenie
- Otwórz dowolną stronę, znajdź pole logowania i przycisk submit.
- Skopiuj XPath i CSS Selector tych elementów.
- Spróbuj napisać własne, krótsze selektory.
---
## Podsumowanie
- CSS Selectory są szybsze i prostsze, XPath daje większą elastyczność.
- Wybieraj selektory, które są stabilne i odporne na zmiany strony.

> Notatka: Zachęć kursantów do eksperymentowania z selektorami w narzędziach developerskich.