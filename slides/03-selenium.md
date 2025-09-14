# Wprowadzenie do Selenium WebDriver
---
## Czym jest Selenium?
- Otwarty, darmowy system do automatyzacji przeglądarki
- Wspiera wiele języków (C#, Java, Python)
- Automatyzuje testowanie aplikacji webowych

> Notatka: Podkreśl popularność Selenium w automatyzacji.
---
## Instalacja Selenium w C#
- Zainstaluj Selenium WebDriver przez NuGet
- Dodaj sterownik przeglądarki (np. ChromeDriver)

```csharp
// Menedżer pakietów NuGet
// Install-Package Selenium.WebDriver
// Pobierz ChromeDriver i dodaj do PATH
```
--
### Ćwiczenie
- Skonfiguruj prosty projekt Selenium w Visual Studio.
---
## Lokalizowanie elementów
- Po ID, Name, Class, XPath, CSS Selector

```csharp
IWebElement searchBox = driver.FindElement(By.Name("q"));
```
--
### Ćwiczenie
- Zlokalizuj i wypisz tekst przycisku na stronie.
---
## Podstawowa automatyzacja przeglądarki
- Otwieranie przeglądarki, nawigacja, interakcje

```csharp
using OpenQA.Selenium;
using OpenQA.Selenium.Chrome;

class SeleniumDemo {
    static void Main() {
        IWebDriver driver = new ChromeDriver();
        driver.Navigate().GoToUrl("https://www.google.com");
        driver.Quit();
    }
}
```
--
### Ćwiczenie
- Napisz kod otwierający stronę, wpisujący tekst i klikający przycisk.

> Notatka: Omów dobre praktyki zamykania przeglądarki.