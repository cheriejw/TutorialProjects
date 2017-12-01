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
 - Edited the index.js file with a new installation of `cool-ascii-faces`. note: Demo code was optimized and the node tutorial was not. Cool to see the code optimizations.
 - `heroku local` -- still displayed "Listening on port 5000 when I changed the hard coded 5000 to 5005 and it ran when I used `node index` meaning that when I run locally with heroku it sets the `process.env.PORT` variable as 5000, but node does not. So I commented that out since for some odd reason port 5000 wasn't working on my machine. (Blank page even when not running `heroku local`, some process probably is using it... Also found you get "ERR_CONNECTION_REFUSED" when no one is listening to the port and on port 6000 gives ERR_UNSAFE_PORT)
 - `git add`, `git commit -m "Demo"`, `git push heroku master`, `heroku open cool` -- There was an issue and it told me to read the logs, but I knew this was because I took out the PORT = process.env.PORT and hardcoded it to 5005. This must be a security thing for heroku where their server only allowed me to listen on that process.env.PORT port that they set. `ᕙ༼ຈل͜ຈ༽ᕗ` Appropriate emoji returned.

### Unknown Terms (Research Notes... ~~May be~~ tangents) 
- [**PostScript/Type 1:**](https://en.wikipedia.org/wiki/PostScript) Page description language by Adobe Systems. (.ps extention) Font format. Alternatives: [TrueType/OpenType](https://www.fonts.com/support/faq/font-formats)
- [**CRLF, LF, CR:**](https://stackoverflow.com/questions/1552749/difference-between-cr-lf-lf-and-cr-line-break-types) Line break types for Windows, Unix and Mac.
- **brownout:** Restriction of service. [Heroku brownout](https://status.heroku.com/incidents/1193)
    > Heroku will be performing a "brownout" of the V2 Legacy API. This is in preparation for the complete shutdown of the V2 Legacy API scheduled for Monday, June 26th, 2017. Please see our API v2 sunset announcement for more information. During this time, requests to the V2 Legacy API will respond with 410 Gone.
- **infastructure:** [Framework.](http://searchdatacenter.techtarget.com/definition/infrastructure) Cloud Infastructure. A software layer, on which you build ontop of. IaaS. Between application layer and physical server. Software on the server?
- [Heroku Procfile](https://devcenter.heroku.com/articles/procfile)
    > A Procfile is a mechanism for declaring what commands are run by your application’s dynos on the Heroku platform.

### Rabbitholes
- [Heroku HTTP Routing](https://devcenter.heroku.com/articles/http-routing)
    > It declares that this process type will be attached to the HTTP routing stack of Heroku, and receive web traffic when deployed.
- **Chrome Unsafe Ports:** Tried to use port 6000 and found it threw and odd error. [List of unsafe ports](https://superuser.com/questions/188058/which-ports-are-considered-unsafe-on-chrome), and the [reason](https://jazzy.id.au/2012/08/23/why_does_chrome_consider_some_ports_unsafe.html).
    > Open proxies are considered quite dangerous. No piece of software should allow itself to be used as an open proxy. It's not so much about Chrome preventing malicious activity, as it is about Chrome ensuring that it is not a hole in an otherwise secured network. The problem here is the design of HTML/HTTP, where browsers are so obliging in opening arbitrary connections to anything and sending data on behalf of an attacker who is not even on the same network. That is a fundamental security issue that should be addressed.

### Un-concreate Personal Observations

