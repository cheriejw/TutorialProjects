# MICROSERVICES HOSTED IN DOCKER
*[from Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/tutorials/microservices)*

Goal of this tutorial was to understand more about microservices and familiarize myself with working in Visual Studio and C# code as it will be utilized at my current employment.

### Difficulties
This tutorial required Docker, the link in the tutorial shows you to install DockerCE which requires Hyper-V for Windows, which I do not have seeing I am running on a home machine. So I had to install [Docker ToolBox](https://www.docker.com/products/docker-toolbox) instead with VirtualBox.

I had to change the version in the global.json file from the default
```javascript
{
  "sdk": {
    "version": "1.0.0-rc4-004771"
  }
}
```
to my current dotnet version which was found with the following command
```bash 
$ dotnet --info
The specified SDK version [1.0.0-rc4-004771] from global.json [C:\Users\Cherie Woo\TutorialProjects\CSharp\CSMICROSERVICE\global.json] not found; install specified SDK version

Microsoft .NET Core Shared Framework Host

  Version  : 2.0.0
  Build    : e8b8861ac7faf042c87a5c2f9f2d04c98b69f28d
```
The current version happened to be 2.0.0 so I put that in my global.json. Reading about .NET things are usually backwards compatable so I am hoping it is the case for this too.
note to self: read first. check dates for most current.

Reading more into the tutorial it does have a note that says the following: 
> Note: Starting with .NET Core 2.0, you do not have to run dotnet restore because it is run implicitly as part of dotnet build or dotnet run. It is still a valid command in certain scenarios where doing an explicit restore makes sense, such as continuous integration builds in Visual Studio Team Services.

Which is wonderful they didn't put it sooner, or maybe I should read ahead.

**Actually this dotnet run failed and I looked more into the [generator](https://github.com/OmniSharp/generator-aspnet)... It appears that by default it uses the lts version. The correct command to run for this was: `yo aspnet --version-current`**

This doesn't work either. Because this scaffold is old, unfortunate. Ended up using `dotnet new`. [More on it here.](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-core-2-0/)... [(WeatherMicroservice_dotnetnew)](https://github.com/cheriejw/TutorialProjects/tree/master/CSharp/CSMICROSERVICE/WeatherMicroservice_dotnetnew) and because I really wanted to do the tutorial I also... Ended up installing [the .net version](https://github.com/dotnet/core/blob/master/release-notes/download-archives/rc4-download.md) that was available a few days after this tutorial was published. [(WeatherMicroservice)](https://github.com/cheriejw/TutorialProjects/tree/master/CSharp/CSMICROSERVICE/WeatherMicroservice)

### Unknown Terms (Research Notes)
*(Definitions from research are only as accurate as I understand them to be, some copy-pasta and references; Please correct me if I am wrong.)*
- **Protobuf:** 

### Rabbitholes
- [Monolithic vs. Microservices:](https://articles.microservices.com/monolithic-vs-microservices-architecture-5c4848858f59)
    > "...it is important to understand Monolithic architecture since it is the basis for microservices architecture where each service by itself is implemented according to monolithic architecture."

- https://insidethecpu.com/2015/05/22/microservices-with-c-and-rabbitmq/
