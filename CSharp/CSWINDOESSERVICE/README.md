[Walkthrough: Creating a Windows Service Application in the Component Designer](https://docs.microsoft.com/en-us/dotnet/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer)

MyNewService.cs vs MyNewService.designer.cs

>A service application is designed to be long-running, so it usually polls or monitors something in the system. The monitoring is set up in the OnStart method. However, OnStart doesn’t actually do the monitoring. The OnStart method must return to the operating system after the service's operation has begun. It must not loop forever or block.

