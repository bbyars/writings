
# Strategies

* Obvious one of add by addition
* Upcast the incoming request into the new format
    * shellTransform went from a string to an array. If you see an incoming string, 
        transform to an array with one element.
    * Stack multiple in order (shellTransform / behaviors array) to "stack" upcasts on top of each other    
* Downcast the interface to accept old format
    * Response injection changed from parameter explosion to a single object parameter; 
    (request, response, logger, state, done) => (config), where the config object contains 
    old parameters as fields. For backwards compatibility, add all old request fields to config as well.
* Configuration switch
    * Newer protocol implementations will be out of process to mountebank. Pre-existing implementations 
    are in-process by default but using a config file can be converted to out of process
* Parallel implementation
    * Useful for bugs or mistakes. For example, it was too hard fixing shell quoting for complex 
        scenarios where mountebank shells out for transformation, so I switched to environment variables. 
        For backwards compatibility, I left in the old shell interface, including leaving the bug in place
* Hidden functionality
    * Again useful for bugs or mistakes. Leave in place, but remove docs. Did this for a way of resetting proxies
* Future compatibility
    * There's a few simple tips around improving your odds of avoiding backwards compatible changes 
    (like avoiding returning raw JSON arrays, which prevent you from later adding paging, etc).
*  What about the need for real breaking changes
    * Not happy that I decided to return requests with the delete, etc
        Breaking that default improves the interface for newbies but risks breaking old timers
        Middle ground is add query param to fix behavior. Maybe rename endpoints for new behavior. 
* Dealing with Hyrum's law
    * Don't. Stake your claim
    * 


English language compatibility evolution:
* Begs the question
* Fulsome
