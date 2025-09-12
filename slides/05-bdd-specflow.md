# BDD with SpecFlow
---
## What is BDD?
- Behavior Driven Development
- Collaboration between devs, testers, and business
- Uses natural language for test scenarios

> Note: Show how BDD bridges communication gaps.
---
## SpecFlow Overview
- C# BDD framework
- Uses Gherkin syntax (`Given`, `When`, `Then`)
- Integrates with Selenium

```gherkin
Feature: Login
  Scenario: Successful login
    Given user is on login page
    When user enters valid credentials
    Then user is logged in
```
--
### Exercise
- Write a feature file for searching a product.
---
## Step Definitions
- Map Gherkin steps to C# methods

```csharp
[Given("user is on login page")]
public void GivenUserIsOnLoginPage() {
    driver.Navigate().GoToUrl("https://example.com/login");
}
```
--
### Exercise
- Implement step definitions for your search feature.
---
## Integrating with Selenium
- Use Selenium in step definitions

```csharp
[When("user enters valid credentials")]
public void WhenUserEntersValidCredentials() {
    driver.FindElement(By.Id("username")).SendKeys("user");
    driver.FindElement(By.Id("password")).SendKeys("pass");
    driver.FindElement(By.Id("loginBtn")).Click();
}
```
--
### Exercise
- Automate a search scenario using SpecFlow and Selenium.

> Note: Discuss how BDD improves test coverage and collaboration.