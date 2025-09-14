# Waity w Selenium i C#
---
## Cykl życia elementów w DOM
- Elementy na stronie mogą pojawiać się, znikać lub zmieniać się dynamicznie.
- Testy automatyczne muszą uwzględniać opóźnienia ładowania i asynchroniczne zmiany.
- Stosowanie "waitów" pozwala na stabilne i niezawodne testy.
---
## Rodzaje waitów w Selenium
- Selenium oferuje kilka mechanizmów oczekiwania na elementy:
---
### Implicit Wait
- Ustawiany globalnie dla WebDriver.
- Powoduje, że driver czeka określony czas na pojawienie się elementu.

```csharp
// Ustawienie implicit wait na 10 sekund
WebDriver driver = new ChromeDriver();
driver.Manage().Timeouts().ImplicitWait = TimeSpan.FromSeconds(10);
```
- Uwaga: Może prowadzić do nieoczekiwanych opóźnień w całym teście.
---
### Explicit Wait
- Czeka na spełnienie konkretnego warunku dla danego elementu.
- Najczęściej używany z WebDriverWait i ExpectedConditions.

```csharp
WebDriverWait wait = new WebDriverWait(driver, TimeSpan.FromSeconds(10));
IWebElement element = wait.Until(drv => drv.FindElement(By.Id("loginBtn")));
```
- Pozwala na precyzyjne sterowanie oczekiwaniem.
---
### Fluent Wait
- Rozszerzenie explicit wait z dodatkowymi opcjami:
  - Częstotliwość sprawdzania
  - Ignorowanie wyjątków

```csharp
DefaultWait<IWebDriver> fluentWait = new DefaultWait<IWebDriver>(driver) {
    Timeout = TimeSpan.FromSeconds(15),
    PollingInterval = TimeSpan.FromMilliseconds(500),
    IgnoreExceptionTypes = { typeof(NoSuchElementException) }
};
IWebElement element = fluentWait.Until(drv => drv.FindElement(By.Id("loginBtn")));
```
---
## Kiedy stosować poszczególne waity?
- Implicit Wait: dla prostych, statycznych stron.
- Explicit/Fluent Wait: dla dynamicznych aplikacji, AJAX, SPA.
- Unikaj mieszania implicit i explicit wait w jednym teście!
---
## Ćwiczenie
- Przetestuj różne waity na stronie z dynamicznie pojawiającym się elementem.
- Zmierz czas działania testu dla różnych typów waitów.
---
## Podsumowanie
- Waity są kluczowe dla stabilności testów Selenium.
- Wybieraj odpowiedni typ oczekiwania do charakteru strony i testu.