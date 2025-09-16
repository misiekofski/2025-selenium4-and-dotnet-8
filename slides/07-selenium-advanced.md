# Zaawansowane funkcje Selenium
---
## Wprowadzenie
- Selenium oferuje wiele zaawansowanych możliwości dla profesjonalnych testów automatycznych.
- Poznaj wybrane funkcje, które usprawnią Twoje testy.
---
## Robienie screenshotów
- Możesz zapisać zrzut ekranu strony lub elementu.

```csharp
((ITakesScreenshot)driver).GetScreenshot().SaveAsFile("screenshot.png");
```
- Przydatne do debugowania i raportowania błędów.
--
### Ćwiczenie
- Dodaj zrzut ekranu po nieudanym teście logowania.
---
## Zewnętrzna konfiguracja testów
- Używaj plików konfiguracyjnych (np. JSON, XML, appsettings) do parametrów testów.
- Pozwala łatwo zmieniać adresy URL, dane logowania, timeouty bez modyfikacji kodu.

```csharp
var config = JsonConvert.DeserializeObject<Config>(File.ReadAllText("config.json"));
driver.Navigate().GoToUrl(config.BaseUrl);
```
--
### Ćwiczenie
- Stwórz plik konfiguracyjny z danymi testowymi i użyj go w teście.
---
## LoadableComponent
- Wzorzec do obsługi stron, które ładują się asynchronicznie.
- Pozwala sprawdzić, czy strona jest gotowa do interakcji.

```csharp
public class HomePage : LoadableComponent<HomePage> {
    protected override void Load() {
        driver.Navigate().GoToUrl("https://example.com");
    }
    protected override bool IsLoaded() {
        return driver.Title.Contains("Home");
    }
}
```
---
## Selenium 4.7+ BIDI i DevTools
- Nowe API pozwala na komunikację z przeglądarką przez BiDi (Bidirectional Protocol).
- Możesz np. przechwytywać logi, sieć, performance, mockować odpowiedzi.

```csharp
var devTools = ((IDevTools)driver).GetDevToolsSession();
devTools.Network.Enable();
devTools.Network.SetBlockedURLs(new List<string>{"*.ads.com"});
```
- Umożliwia zaawansowane testy i debugowanie.
--
## Ćwiczenie
Przeanalizuj framework testowy z BDD + TestSettings.
[Github](https://github.com/misiekofski/dotNetSeleniumTestingFramework/)
[ZIP](./downloads/dotNetSeleniumTestingFramework-main.zip)