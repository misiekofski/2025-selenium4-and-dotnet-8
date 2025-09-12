# Introduction to Selenium WebDriver
---
## What is Selenium?
- Open-source browser automation tool
- Supports multiple languages (C#, Java, Python)
- Automates web applications for testing

> Note: Highlight Selenium's popularity in automation.
---
## Setting Up Selenium in C#
- Install Selenium WebDriver via NuGet
- Add browser driver (e.g., ChromeDriver)

```csharp
// NuGet Package Manager
// Install-Package Selenium.WebDriver
// Download ChromeDriver and add to PATH
```
--
### Exercise
- Set up a simple Selenium project in Visual Studio.
---
## Locating Elements
- By ID, Name, Class, XPath, CSS Selector

```csharp
IWebElement searchBox = driver.FindElement(By.Name("q"));
```
--
### Exercise
- Locate and print the text of a button on a web page.
---
## Basic Browser Automation
- Open browser, navigate, interact

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
### Exercise
- Write code to open a page, enter text, and click a button.

> Note: Discuss best practices for browser cleanup.