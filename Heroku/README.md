# [Getting Started on Heroku with Node.js](https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up)
[Getting Started with Heroku Portal](https://dashboard.heroku.com/apps)
### Procedure with Notes
 - Installed Heroku CLI(Toolbox)
 - `heroku login`
 - `git clone https://github.com/heroku/node-js-getting-started.git`
 - `cd node-js-getting-started`
 - `heroku create`
 - `git push heroku master`
    ```bash
    remote: Verifying deploy... done.
    To https://git.heroku.com/ancient-retreat-91601.git
    ```
 - `heroku ps:scale web=1`
    ```bash
    Scaling dynos... done, now running web at 1:Free
    ```
 - `heroku open` -- This failed so I had to open the launched url in browser.
 - `heroku logs --tail` -- Streams the logs... probably in a log file somewhere. Noticed a variable called 'dyno'.
 - Looking at [Procfile](https://devcenter.heroku.com/articles/getting-started-with-nodejs#define-a-procfile), which explicitly declares what commands to execute to start app. Reminds me of the config file for TravisCI, travis.yml.
 - `heroku ps:scale web=0` -- The 'dyno' is compared to a lightweight container that runs the command in the Procfile. Web dynos serve requests. Can run `heroku ps` to see how many 'dynos' are running.
 - `npm install`
 - `heroku local web` -- changed to port 5005 because 5000 was not rendering oddly... `heroku local` uses the code I pushed to it.
 - 
 - 

### Unknown Terms (Research Notes... ~~May be~~ tangents) 
- [**PostScript/Type 1:**](https://en.wikipedia.org/wiki/PostScript) Page description language by Adobe Systems. (.ps extention) Font format. Alternatives: [TrueType/OpenType](https://www.fonts.com/support/faq/font-formats)
- [**CRLF, LF, CR:**](https://stackoverflow.com/questions/1552749/difference-between-cr-lf-lf-and-cr-line-break-types) Line break types for Windows, Unix and Mac.
- **brownout:** Restriction of service. [Heroku brownout](https://status.heroku.com/incidents/1193)
    > Heroku will be performing a "brownout" of the V2 Legacy API. This is in preparation for the complete shutdown of the V2 Legacy API scheduled for Monday, June 26th, 2017. Please see our API v2 sunset announcement for more information. During this time, requests to the V2 Legacy API will respond with 410 Gone.
- **infastructure:** [Framework.](http://searchdatacenter.techtarget.com/definition/infrastructure) Cloud Infastructure. A software layer, on which you build ontop of. IaaS. Between application layer and physical server. Software on the server?

### Rabbitholes
[Heroku HTTP Routing](https://devcenter.heroku.com/articles/http-routing)
> It declares that this process type will be attached to the HTTP routing stack of Heroku, and receive web traffic when deployed.

[Heroku Procfile](https://devcenter.heroku.com/articles/procfile)
> A Procfile is a mechanism for declaring what commands are run by your application’s dynos on the Heroku platform.

### Un-concreate Personal Observations

