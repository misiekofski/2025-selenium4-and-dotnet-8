# Unit Testing with NUnit/xUnit
---
## Why Unit Test?
- Catch bugs early
- Ensure code quality
- Enable refactoring

> Note: Discuss benefits of automated testing.
---
## Setting Up a Test Project
- Use Visual Studio or CLI
- Add NUnit/xUnit via NuGet

```csharp
// CLI example
// dotnet new nunit -n MyTests
// dotnet add package NUnit
```
--
### Exercise
- Create a new test project using CLI or Visual Studio.
---
## Writing Basic Tests
- Test methods marked with `[Test]` (NUnit) or `[Fact]` (xUnit)
- Use assertions to check results

```csharp
using NUnit.Framework;

[TestFixture]
public class CalculatorTests {
    [Test]
    public void Add_ReturnsSum() {
        int result = 2 + 3;
        Assert.AreEqual(5, result);
    }
}
```
--
### Exercise
- Write a test for a method that multiplies two numbers.
---
## Common Assertions
- `Assert.AreEqual(expected, actual)`
- `Assert.IsTrue(condition)`
- `Assert.IsNull(object)`

```csharp
Assert.IsTrue(5 > 3);
Assert.IsNull(null);
```
--
### Exercise
- Try different assertions in your tests.
---
## Test Lifecycle
- Setup/Teardown methods: `[SetUp]`, `[TearDown]`

```csharp
[TestFixture]
public class SampleTests {
    [SetUp]
    public void Init() {
        // Runs before each test
    }
    [TearDown]
    public void Cleanup() {
        // Runs after each test
    }
}
```
--
### Exercise
- Add setup/teardown to your test class.

> Note: Encourage students to run tests and interpret results.