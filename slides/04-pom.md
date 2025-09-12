# Page Object Model (POM)
---
## What is POM?
- Design pattern for test automation
- Encapsulates page elements and actions
- Improves maintainability and readability

> Note: Stress the importance of clean test architecture.
---
## POM Structure
- Page classes for each web page
- Methods for actions (e.g., Login, Search)

```csharp
public class LoginPage {
    private IWebDriver driver;
    public LoginPage(IWebDriver driver) {
        this.driver = driver;
    }
    public void EnterUsername(string username) {
        driver.FindElement(By.Id("username")).SendKeys(username);
    }
    public void EnterPassword(string password) {
        driver.FindElement(By.Id("password")).SendKeys(password);
    }
    public void ClickLogin() {
        driver.FindElement(By.Id("loginBtn")).Click();
    }
}
```
--
### Exercise
- Create a page object for a search page with methods to enter a query and submit.
---
## Using POM in Tests
- Instantiate page objects in test classes
- Call page methods for actions

```csharp
[Test]
public void LoginTest() {
    var loginPage = new LoginPage(driver);
    loginPage.EnterUsername("user");
    loginPage.EnterPassword("pass");
    loginPage.ClickLogin();
}
```
--
### Exercise
- Refactor an existing test to use POM.

> Note: Encourage students to separate test logic from page details.