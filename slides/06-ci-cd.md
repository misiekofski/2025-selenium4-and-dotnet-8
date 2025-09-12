# CI/CD Integration (Optional)
---
## Why CI/CD?
- Automate build, test, and deployment
- Improve code quality and delivery speed

> Note: Explain the value of pipelines in modern development.
---
## Popular Tools
- GitHub Actions
- Azure DevOps
- Jenkins

---
## Example: GitHub Actions
- Run tests on every push

```yaml
name: .NET Test
on: [push]
jobs:
  build:
    runs-on: windows-latest
    steps:
      - uses: actions/checkout@v2
      - name: Setup .NET
        uses: actions/setup-dotnet@v2
        with:
          dotnet-version: '6.0.x'
      - name: Install dependencies
        run: dotnet restore
      - name: Run tests
        run: dotnet test
```
--
### Exercise
- Set up a simple pipeline for your test project.
---
## Example: Azure DevOps
- YAML pipeline for .NET tests

```yaml
trigger:
- main
pool:
  vmImage: 'windows-latest'
steps:
- task: UseDotNet@2
  inputs:
    packageType: 'sdk'
    version: '6.0.x'
- script: dotnet restore
- script: dotnet test
```
--
### Exercise
- Try running your tests in Azure DevOps.

> Note: Encourage students to explore CI/CD for automation.