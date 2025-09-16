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
## Selenium Actions API
- Actions pozwala na wykonywanie złożonych interakcji z przeglądarką
- Symuluje zachowania użytkownika jak scroll, drag&drop, hover

```csharp
var actions = new Actions(driver);
actions.Click(element).Perform();
actions.DoubleClick(element).Perform();
actions.ContextClick(element).Perform(); // prawy przycisk myszy
```
---
## Infinite Scroll - automatyzacja
- Wiele nowoczesnych stron używa infinite scroll
- Należy symulować przewijanie i czekać na załadowanie nowych elementów

```csharp
[Test]
public void ShouldBeAbleToScrollUntilTenthParagraph()
{
    var url = "https://the-internet.herokuapp.com/infinite_scroll";
    using (var driver = new ChromeDriver())
    {
        driver.Navigate().GoToUrl(url);
        var actions = new Actions(driver);
        
        for (int i = 0; i < 10; i++)
        {
            actions.SendKeys(Keys.PageDown).Perform();
            Thread.Sleep(500); // Czekaj na załadowanie nowych paragrafów
        }
        
        var paragraphs = driver.FindElements(By.ClassName("jscroll-added"));
        Assert.IsTrue(paragraphs.Count >= 10);
    }
}
```
--
### Inne sposoby scrollowania
```csharp
// Scroll do konkretnego elementu
((IJavaScriptExecutor)driver).ExecuteScript("arguments[0].scrollIntoView(true);", element);

// Scroll do końca strony
((IJavaScriptExecutor)driver).ExecuteScript("window.scrollTo(0, document.body.scrollHeight);");

// Scroll o określoną wartość
actions.MoveToElement(element).SendKeys(Keys.PageDown).Perform();
```
---
## Drag and Drop
- Przydatne w testach interfejsów z przeciągnij i upuść

```csharp
[Test]
public void TestDragAndDrop()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/drag_and_drop");
    
    var source = driver.FindElement(By.Id("column-a"));
    var target = driver.FindElement(By.Id("column-b"));
    
    var actions = new Actions(driver);
    actions.DragAndDrop(source, target).Perform();
    
    // Weryfikacja
    Assert.AreEqual("B", source.Text);
}
```
--
### Ćwiczenie
- Przetestuj drag and drop na stronie demo
- Dodaj weryfikację pozycji elementów
---
## Hover i kontekstowe menu
- Symulacja najechania myszą i menu kontekstowego

```csharp
[Test]
public void TestHoverActions()
{
    driver.Navigate().GoToUrl("https://the-internet.herokuapp.com/hovers");
    
    var avatar = driver.FindElement(By.XPath("(//img)[1]"));
    var actions = new Actions(driver);
    
    // Hover nad elementem
    actions.MoveToElement(avatar).Perform();
    
    // Sprawdź czy pojawił się tooltip
    var tooltip = driver.FindElement(By.XPath("//h5[text()='name: user1']"));
    Assert.IsTrue(tooltip.Displayed);
}
```

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