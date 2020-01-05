Just thoughts about what it should include not even an actual design paper. (Just use another current soln? Maybe but this project is just for fun).

### Problem
Rather than writing ACL mechanism to every project have a generic one to handle 90% of the cases with ease. 

### What should it handle?
Takes a request (http? tcp?) and validates the user with provided auth mechanism. Extracts the roles and return access error if user has no access or not valid. This brings a lot of questions though.

* It should be a proxy application separated from the main one to isolate the process. Other option is making it a library for every language and integrate it to your application (similar to Casbin? https://github.com/casbin/casbin).
    * If we are already running nginx or similar ones it will be proxying the request twice. Maybe write an extension to ngixn or caddy with less features?
    * If it is the one the accepts the requests needs to be a complete (full support for protocols) and performant one. Doesn't seem like a reasonable task to deal with. 
    * Having it as a library for frameworks or programming languages might work. Or at least it should be point of start.
    * Result: These are two different parts and start to first one with writing a middleware for ACL task.

* What kind of mechanism it should support?
    * Most generic one, role based access with extra access and deny to specific users. 
    * Ip based access
    * ? resource id based access

* Where do we store it?
    * Config file with listening for file changes for group access.
    * Database storage on separate models.
    * Redis for storing user based access-deny sets.



