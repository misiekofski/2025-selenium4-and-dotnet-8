# Wprowadzenie do Selenium WebDriver
---
## Czym jest Selenium?
- Otwarty, darmowy system do automatyzacji przeglądarki
- Wspiera wiele języków (C#, Java, Python)
- Automatyzuje testowanie aplikacji webowych

> Notatka: Selenium to standard w automatyzacji testów web.
---
## Instalacja Selenium w C#
1. Utwórz nowy projekt testowy (NUnit/xUnit)
2. Zainstaluj wymagane paczki NuGet:

```powershell
dotnet add package Selenium.WebDriver
dotnet add package Selenium.Support
dotnet add package Selenium.WebDriver.ChromeDriver
```

> Notatka: ChromeDriver zostanie automatycznie pobrany i skonfigurowany.
--
### Ćwiczenie
- Utwórz nowy projekt testowy
- Zainstaluj wymagane paczki
- Uruchom prosty test otwierający przeglądarkę
---
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
## Automatyzacja formularza demo
- Użyjemy oficjalnej strony demo Selenium
- Pokażemy różne typy interakcji z elementami

```csharp
[TestFixture]
public class WebFormTests
{
    private IWebDriver driver;
    private const string Url = "https://www.selenium.dev/selenium/web/web-form.html";

    [SetUp]
    public void Setup()
    {
        driver = new ChromeDriver();
        driver.Navigate().GoToUrl(Url);
    }

    [TearDown]
    public void Teardown()
    {
        driver?.Quit();
    }

    [Test]
    public void TestWebForm()
    {
        // Pole tekstowe
        var textInput = driver.FindElement(By.Name("my-text"));
        textInput.SendKeys("Selenium C#");

        // Pole hasła
        var passwordInput = driver.FindElement(By.Name("my-password"));
        passwordInput.SendKeys("password123");

        // Select (dropdown)
        var dropdown = driver.FindElement(By.Name("my-select"));
        var selectElement = new SelectElement(dropdown);
        selectElement.SelectByText("Two");

        // Checkbox
        var checkbox = driver.FindElement(By.Name("my-check"));
        if (!checkbox.Selected)
        {
            checkbox.Click();
        }

        // Przycisk Submit
        var submitButton = driver.FindElement(By.CssSelector("button[type='submit']"));
        submitButton.Click();

        // Weryfikacja
        var message = driver.FindElement(By.Id("message"));
        Assert.That(message.Text, Is.EqualTo("Received!"));
    }
}
```
--
### Ćwiczenie
- Otwórz stronę formularza demo
- Wypełnij wszystkie pola
- Zweryfikuj wysłanie formularza
