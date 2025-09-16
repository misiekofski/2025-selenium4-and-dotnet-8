# Page Object Model (POM)
---
## Czym jest POM?
- Wzorzec projektowy dla automatyzacji testów
- Enkapsuluje elementy strony i akcje
- Poprawia czytelność i łatwość utrzymania

---
## Struktura POM
- Klasy stron dla każdej podstrony
- Metody dla akcji (np. logowanie, wyszukiwanie)

```csharp
public class LoginPage {
    private IWebDriver driver;
    public LoginPage(IWebDriver driver) {
        this.driver = driver;
    }
    public void LoginAs(string username, string password) {
        driver.FindElement(By.Id("username")).SendKeys(username);
        driver.FindElement(By.Id("password")).SendKeys(password);
        driver.FindElement(By.Id("loginBtn")).Click();
    }
}
```
--
### Ćwiczenie
- Utwórz obiekt strony dla wyszukiwarki z metodami wpisywania zapytania i zatwierdzania.
---
## Użycie POM w testach
- Tworzenie obiektów stron w klasach testowych
- Wywoływanie metod strony do akcji

```csharp
[Test]
public void LoginTest() {
    var loginPage = new LoginPage(driver);
    loginPage.LoginAs("user", "pass");
}
```
--
### Ćwiczenie
Utwórzmy PageObjectModel dla stron:
- [https://www.saucedemo.com/](https://www.saucedemo.com/)
- [https://www.saucedemo.com/inventory.html](https://www.saucedemo.com/inventory.html)
