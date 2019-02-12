[![Build status](https://ci.appveyor.com/api/projects/status/svujv1049rtf4nb9?svg=true)](https://ci.appveyor.com/project/PragmaticFlowOrg/nbomber-http)
[![NuGet](https://img.shields.io/nuget/v/nbomber.http.svg)](https://www.nuget.org/packages/nbomber.http/)

NBomber plugin for defining HTTP scenarios

### How to install
To install NBomber via NuGet, run this command in NuGet package manager console:
```code
PM> Install-Package NBomber.Http
```

### Documentation
Documentation is located [here](https://nbomber.com).

### Contributing
Would you like to help make NBomber even better? We keep a list of issues that are approachable for newcomers under the [good-first-issue](https://github.com/PragmaticFlow/NBomber.Http/issues?q=is%3Aopen+is%3Aissue+label%3A%22good+first+issue%22) label.

### Examples
```csharp
class Program
{
    static void Main(string[] args)
    {
        var scenario = BuildScenario();
        NBomberRunner.RegisterScenarios(scenario)
                     .RunInConsole();            
    }

    static Scenario BuildScenario()
    {
        var step = HttpStep.CreateRequest("GET", "https://github.com/PragmaticFlow/NBomber")
                           .BuildStep();

        return ScenarioBuilder.CreateScenario("HTTP scenario with 100 concurrent requests", step)
                              .WithConcurrentCopies(50)
                              .WithDuration(TimeSpan.FromSeconds(10));
    }
}
```
