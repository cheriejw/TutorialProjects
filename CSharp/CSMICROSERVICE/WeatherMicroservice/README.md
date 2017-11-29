After running `dotnet run` after the `dotnet build` and `dotnet restore`, I could visit http://localhost:5000 to see my expected 'hello world' scaffold app.

Speaking of the Startup.cs file and the project.json file (obj/project.assets.json) :
> The ConfigureServices method describes the services that are necessary for this application. You're building a lean microservice, so it doesn't need to configure any dependencies. **The Configure method configures the handlers for incoming HTTP Requests.**

Went into extension nullable methods which reminded me of using the [Convert.toString() vs string.toString()](https://stackoverflow.com/questions/2828154/difference-between-convert-tostring-and-tostring) I encountered today.

I had `dotnet run` serving localhost at port 5000 and tried to stop it and rebuild, it continued to run in the background and I had to go to Task Manager to close proceess: 'dotnet'. *Rebuild was required to test the new changes after completing the parsing step.*

I got an odd error: `Failed to create prime the NuGet cache. new failed with: -2147352571`, that upon Googling lead me to [this](https://github.com/dotnet/cli/issues/7812), global.json file may be unnecessary. Error was not stopping me from running application in anycase.

Running with no query does not crash app because of the nullable likely. In convergence application at work, we used an IHttpContext to "program network communications".

Found the bug again where after hitting Ctrl+C process was still running in background.

Had to run `dotnet restore` again after adding the nuget package for json package parsing, then `dotnet build`.
> Starting with .NET Core 2.0, you don't have to run dotnet restore because it's run implicitly as part of dotnet build or dotnet run


### Unknown Terms (Research Notes)
**Convert.toString() vs .toString() :**
> "In most cases Convert will call ToString on the value but in the general case of calling it on an object Convert actually defers to IConvertible if it is implemented.  This is important because IConvertible does not generally map to ToString.  ToString is generally used for a quick and friendly string representation of an object but IConvertible is designed for conversion so the output can vary.
> Additionally Convert generally calls the ToString overload of the primitives that pass the format provider.  This means that, in some cases, the returned value of Convert will be culture-specific whereas the parameterless ToString() version may not." 

[**Interpolated Strings :**](http://geekswithblogs.net/BlackRabbitCoder/archive/2015/03/26/c.net-little-wonders-string-interpolation-in-c-6.aspx) An cleaner way to create strings. [MSDN here.](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/interpolated-strings)

**Telemetry :** Telemetry is an automated communications process by which measurements and other data are collected at remote or inaccessible points and transmitted to receiving equipment for monitoring.

### Rabbitholes
- [Generic Interfaces](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-interfaces)

### Un-concreate Personal Observations
- A microservice is an API?

### Work experiences in same timeline
- Enum Types, casting to int returns value.