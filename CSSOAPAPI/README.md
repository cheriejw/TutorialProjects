# C# WEB API 2 TUTORIAL
*[from Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api)*

Goal of this tutorial was to understand more about APIs and familiarize myself with working in VisualStudio and C# code as it will be utilized at my current employment.

### Procedure with Notes
- Opened VS and created a new empty ASP.NET Web Application under Visual C# > Web with folders and core references for WebAPI.
    *Compared to a new empty ASP.NET Web Application without the WebAPI folders and core references, this contained an additional 4 folders (App_Data, App_Start, Controllers, Models) and a "Global.asax" file. Under Resources folder added: System.Web.Http, System.Web.Http.Webhost, System.Net.HttpFormatting, System.Net.Http and Newtonsoft.Json. In App_Start there was a WebApiConfig.cs file with Register method that appeared to be a Router configuration with default "api/{controller}/{action}" template.*

- Added a (Model) Class in the Models folder.
    *The class was a namespace which was <ApplicationName>.Models. (All code seem to be wrapped in namespace) I placed a class in the namespace. The class contained 4 properties (AutoProperties). This file appears to be a blueprint object.*

- Added an Empty Web API Controller in the Controllers folder. Named it "ProductsController". 
    *Tutorial said to copy and paste code. The code was again inside a nested namespace and contained one class that inherits from (:) an ApiController class.*

*The file structure/organization and naming conventions are all just seem to be strong recommendations. Interesting to see all of the recommended optional coding styles, though I don't fully understand the reasoning for all of it yet due to lack of experience*

### Unknown Terms (Research Notes)
*(Definitions from research are only as accurate as I understand them to be, some copy-pasta and references; Please correct me if I am wrong.)*
- **(Global) ASAX file:** ASAX (Active Server Page) files are specific to .NET framework. [Global.asax](https://msdn.microsoft.com/en-us/library/1xaas8a2(v=vs.71).aspx) acts as an optional event handler for "application-level" events from ASP.Next or HttpModules (1 request to your application = 1 HTTP module call). Derived from HttpApplication base class. Not available externally.

- **Namespace:** Named space where your application resides. Purpose is to provide C# compiler with context for named information in program file. Namespaces are in References as well as your source folders. They can be accessed with "using" keyword or typing the name.path. Nested namespaces are also a thing usually with companies with product series, I used nested namespace in the tutorial.
    ```c
    namespace TestWebApplication.Models
    ```
    
- **Properties and Fields:** [Properties expose fields.](https://stackoverflow.com/questions/295104/what-is-the-difference-between-a-field-and-a-property-in-c) Used AutoProperties in Model class (started at C# 3.0) which generates private field for you. Fields stores the actual data. [Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/using-properties) have get and set and sometimes can do calculations or become [method-like](https://msdn.microsoft.com/en-us/library/ms229054(v=vs.100).aspx). Property can only have 2 code blocks at a maximum, get and/or set. Properties are not variables.

### Rabbitholes
- [Contollers and Conventions:](https://www.red-gate.com/simple-talk/dotnet/asp-net/asp-net-mvc-controllers-and-conventions/)
    > For each request that hits the site, ASP.NET MVC figures out the name of the controller class that will handle the request and manages to create a new instance of that class.

### Personal Observations of the Puzzle Pieces
- Building the solution outputted a dll file and API server was not running. Running would also run the index.html file. At work the APIs were services running. Maybe from the other layers pulling in the dll files and calling it creating an instance of it? (Lack of better wording for now.) *How do I run just the API server so I could make calls to it? Is the dll file the contents of the API?*
