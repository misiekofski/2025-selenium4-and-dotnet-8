# Testy jednostkowe - NUnit
---
## Dlaczego testy jednostkowe?
- Wczesne wykrywanie błędów
- Zapewnienie jakości kodu
- Umożliwienie refaktoryzacji

> Notatka: Omów korzyści z automatyzacji testów.
---
## Tworzenie projektu testowego
- Użyj Visual Studio lub CLI
- Dodaj NUnit/xUnit przez NuGet

```csharp
// Przykład CLI
// dotnet new nunit -n MyTests
// dotnet add package NUnit
```
--
### Ćwiczenie
- Utwórz nowy projekt testowy za pomocą CLI lub Visual Studio.
---
## Pisanie podstawowych testów
- Metody testowe oznaczane `[Test]` (NUnit) lub `[Fact]` (xUnit)
- Używaj asercji do sprawdzania wyników

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
### Ćwiczenie
- Napisz test dla metody mnożącej dwie liczby.
---
## Najczęstsze asercje
- `Assert.AreEqual(expected, actual)`
- `Assert.IsTrue(condition)`
- `Assert.IsNull(object)`

```csharp
Assert.IsTrue(5 > 3);
Assert.IsNull(null);
```
--
### Ćwiczenie
- Wypróbuj różne asercje w swoich testach.
---
## Cykl życia testów
- Metody przygotowania/zakończenia: `[SetUp]`, `[TearDown]`

```csharp
[TestFixture]
public class SampleTests {
    [SetUp]
    public void Init() {
        // Wykonuje się przed każdym testem
    }
    [TearDown]
    public void Cleanup() {
        // Wykonuje się po każdym teście
    }
}
```
--
### Ćwiczenie
- Dodaj metody setup/teardown do swojej klasy testowej.

> Notatka: Zachęć uczestników do uruchamiania testów i interpretacji wyników.