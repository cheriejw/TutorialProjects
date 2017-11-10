# C# WEB API 2 TUTORIAL
*[from Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api)*

Goal of this tutorial was to understand more about APIs (Application Programming Interface) and familiarize myself with working in Visual Studio and C# code as it will be utilized at my current employment.

### Procedure with Notes
- Opened VS and created a new empty ASP.NET Web Application under Visual C# > Web with folders and core references for Web API.
    *Compared to a new empty ASP.NET Web Application without the WebAPI folders and core references, this contained an additional 4 folders (App_Data, App_Start, Controllers, Models) and a "Global.asax" file. Under Resources folder added: System.Web.Http, System.Web.Http.Webhost, System.Net.HttpFormatting, System.Net.Http and Newtonsoft.Json. In App_Start there was a WebApiConfig.cs file with Register method that appeared to be a Router configuration with default "api/{controller}/{id}" template.*

- Added a (Model) Class in the Models folder.
    *The class was a namespace which was <ApplicationName>.Models. (All code seem to be wrapped in namespace) I placed a class in the namespace. The class contained 4 properties (AutoProperties). This file appears to be a blueprint object.*

- Added an Empty Web API Controller in the Controllers folder. Named it "ProductsController". 
    *Tutorial said to copy and paste code. The code was again inside a nested namespace and contained one class that inherits from (:) an ApiController class. Class consisted of two methods and a field. The field in the view used the model we created earlier to be the object where the data is stored (in an application this is where the database/external data source would be put into, but we hard coded values). One of the methods would return an IEnumerable<Product> with all the products and the other would return an IHttpActionResult of the product object of given id.*

- Added a simple UI (HTML page to the project) to interact with the API.
    *This part was just copy and pasted and they did explain more in the tutorial but I was not particularly interested in what the front-end was doing to render data but rather how it was getting the results. How did the API know that when I hit api/products I was refering to which of the two methods? [It was all in the default WebApiConfig.cs file.](https://docs.microsoft.com/en-us/aspnet/web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api) It appears that they just matched the id to the action (what they call the methods in the controller) parameter to determine which to use, however you could also match it in the api/{controller}/{action}/{id} fashion as well to be more specific.*
    >After some playing around I found that you must name it <controllername>Controller and in the WebApiConfig it will pick up <controllername> as part of the route. That is how the controller name was set. There should be a way around this, seems strickt for a programming language... (but wait... its a framework? <.NET>)
    > Just to confirm my theory that it matched {id} to the action parameter, I made both actions in the controller have an int parameter, sure enough I got this exception message: Multiple actions were found that match the request: GetAllProducts on type TestWebApplication.Controllers.ProductzController GetProduct on type TestWebApplication.Controllers.ProductzController. I also got the same error changing int to string on one of them. So they only counted number of parameters it appears. 
    > Changing the WebApiConfig file to api/{controller}/{action}/{id} did automatically take the methods in the controller as an action name.


- Checkout browser's developer tools to view HTTP traffic.
    *This part wasn't mandatory, but good to help understand a bit more if you havent already. Could see the request and response headers to see what was sent and what was recieved, did not go into this too much. Also noted that it is browser functionality to serialize data to json? Recommended Fiddler for debugging, another day.*

*The file structure/organization and naming conventions are all just seem to be strong recommendations. Interesting to see all of the recommended optional coding styles, though I don't fully understand the reasoning for all of it yet due to lack of experience*

### Unknown Terms (Research Notes)
*(Definitions from research are only as accurate as I understand them to be, some copy-pasta and references; Please correct me if I am wrong.)*
- **(Global) ASAX file:** ASAX (Active Server Page) files are specific to .NET framework. [Global.asax](https://msdn.microsoft.com/en-us/library/1xaas8a2(v=vs.71).aspx) acts as an optional event handler for "application-level" events from ASP.Next or HttpModules (1 request to your application = 1 HTTP module call). Derived from HttpApplication base class. Not available externally.

- **Namespace:** Named space where your application resides. Purpose is to provide C# compiler with context for named information in program file. Namespaces are in References as well as your source folders. They can be accessed with "using" keyword or typing the name.path. Nested namespaces are also a thing usually with companies with product series, I used nested namespace in the tutorial.
    ```c
    namespace TestWebApplication.Models
    ```
    
- **Properties and Fields:** [Properties expose fields.](https://stackoverflow.com/questions/295104/what-is-the-difference-between-a-field-and-a-property-in-c) Used AutoProperties in Model class (started at C# 3.0) which generates private field for you. Fields stores the actual data. [Properties](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/using-properties) have get and set and sometimes can do calculations or become [method-like](https://msdn.microsoft.com/en-us/library/ms229054(v=vs.100).aspx). Property can only have 2 code blocks at a maximum, get and/or set. Properties are not variables.

- **(Web Debugging) Proxy:** This is what Fiddler is. A [proxy (server)](http://whatismyipaddress.com/proxy-server) is just something that acts like a middleman/broker. So before the traffic comes in, it will go to the proxy first, or before it leaves, it will go through the proxy first.

### Rabbitholes
- [Contollers and Conventions:](https://www.red-gate.com/simple-talk/dotnet/asp-net/asp-net-mvc-controllers-and-conventions/)
    > For each request that hits the site, ASP.NET MVC figures out the name of the controller class that will handle the request and manages to create a new instance of that class.

### Un-concreate Personal Observations
- Building the solution outputted a dll file and API was not running. Running would also run the index.html file. At work the APIs were services running. Maybe from the other layers pulling in the dll files and calling it creating an instance of it? (Lack of better wording for now.) *How do I run just the API server so I could make calls to it? Is the dll file the contents of the API?*
    > Went to work the next day and ask a little about what an API would refer to as "application-level" someone mentioned the [OSI model](https://en.wikipedia.org/wiki/OSI_model) which made sense to me. Also the answer was because I had no server. At work there was the IIS serving the dll making it the API I knew of. I did not have any servers serving my API in this tutorial, but when I ran it with the index, I guess it took the methods from the dll file?


