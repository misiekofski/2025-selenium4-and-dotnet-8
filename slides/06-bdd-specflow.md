# BDD z Reqnroll
---
## Czym jest BDD?
- Behavior Driven Development (Rozwój sterowany zachowaniem)
- Współpraca programistów, testerów i biznesu
- Scenariusze testowe w języku naturalnym

--
## Przed BDD
![Przed BDD](./img/bdd-1.png "Przed BDD")
--
## BDD
![W trakcie BDD](./img/bdd-2.png "BDD 2")
--
## BDD
![W trakcie BDD](./img/bdd-3.png "BDD 2")
--
## BDD
![W trakcie BDD](./img/bdd-4.png "BDD 2")

---
## Reqnroll - przegląd
- Framework BDD dla C#
- Składnia Gherkin (`Given`, `When`, `Then`)
- Integracja z Visual Studio

[Reqnroll](https://reqnroll.net/)

```gherkin
Feature: Login
    Scenario: Successful login
        Given user is on login page
        When user enters valid credentials
        Then user is logged in
```
--
### Ćwiczenie
- Napisz plik feature dla przelewu bankowego
---
## Definicje kroków
- Mapowanie kroków Gherkin na metody C#

```csharp
[Given("user is on login page")]
public void GivenUserIsOnLoginPage() {
    driver.Navigate().GoToUrl("https://example.com/login");
}
```
--
### Ćwiczenie
- Zaimplementuj definicje kroków dla wyszukiwania.
---
## Integracja z Selenium
- Użycie Selenium w definicjach kroków

```csharp
[When("user enters valid credentials")]
public void WhenUserEntersValidCredentials() {
    driver.FindElement(By.Id("username")).SendKeys("user");
    driver.FindElement(By.Id("password")).SendKeys("pass");
    driver.FindElement(By.Id("loginBtn")).Click();
}
```
--
### Ćwiczenie
- Zautomatyzuj scenariusz wyszukiwania z użyciem SpecFlow i Selenium.