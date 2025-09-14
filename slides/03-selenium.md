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
```
--
### Ćwiczenie
- Skonfiguruj prosty projekt Selenium w Visual Studio.
---
## Lokalizowanie elementów
## Lokalizowanie elementów
- Po ID, Name, Class, XPath, CSS Selector

---
### Wyszukiwanie po ID
- Najczęstszy sposób, gdy element ma unikalny identyfikator.
```csharp
IWebElement element = driver.FindElement(By.Id("loginBtn"));
```
--
### Ćwiczenie
- Znajdź przycisk logowania po ID i wypisz jego tekst.
---
### Wyszukiwanie po Name
- Używane, gdy element ma atrybut `name`.
```csharp
IWebElement element = driver.FindElement(By.Name("username"));
```
--
### Ćwiczenie
- Znajdź pole użytkownika po Name i wpisz tekst.
---
### Wyszukiwanie po XPath
- Pozwala na zaawansowane wyszukiwanie wg struktury DOM.
```csharp
IWebElement element = driver.FindElement(By.XPath("//input[@type='password']"));
```
--
### Ćwiczenie
- Znajdź pole hasła po XPath i wpisz tekst.
---
### Wyszukiwanie po CSS Selector
- Umożliwia wyszukiwanie wg selektorów CSS.
```csharp
IWebElement element = driver.FindElement(By.CssSelector(".form-login .submit-btn"));
```
--
### Ćwiczenie
- Znajdź przycisk submit po CSS Selector i kliknij go.
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