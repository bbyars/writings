Design for replaceability
Granularity of services
* Principles of breakdowns
    * Services should mirror organizational boundaries - If different business units touch different parts of a logical entity, separate services should manage those different parts. This is most apparent in the product/menu set of services. It's perfectly acceptable for there to be "aggregator services" (like backends-for-frontends) that combine multiple services to get a more holistic view. Importantly, services should not mirror backend systems, unless those backend systems also follow organizational boundaries. Think of this from a support standpoint - if I have a problem with a promotion, I should have to go to one team (or maybe one tech team and one business team) to resolve the issue. If I have to go to more than that, the service boundary is inadequate.
    * Group related concepts in one service boundary - Similarly, if one business unit manages multiple related concepts, they belong in the same service
    * Group concepts based on rate of change - A single mobile BFF makes sense because it's rate of change is equivalent to the mobile applications. Multiple product services may make sense if the consumer or backoffice requirements move at different speeds.
    * Align services on bounded contexts to separate similar concepts - Different business units often use the same word to mean subtly different things. For example, to the Food Safety team, a "product" is a collection of nutritional information. To Marketing, a "product" is a salable menu item, complete with images and copy text. Bounded contexts are linguistic boundaries, inside of which the same word (e.g. "product") has a consistent meaning, but outside of which it may adopt a different meaning. Bounded context definitions are captures in italics within each service.
    * Augment downstream concepts - Downstream services can augment concepts no differently than downstream business processes can augment them. It's perfectly acceptable, for example, for the marketing National Menu to augment product information based on the PLU it gets upstream.
    * Use the language of the business - The APIs should map to the language the business uses as much as possible (Domain Driven Design's "Ubiquitous Language"). Often times there is tension to use the language of backend systems.
* BFFs
    * channel services for different consumers
    * ownership model vs data center model
    * can be very presentational - distributed view model
    * released at cadence of channel, not core api (usually faster)
* Domain modeling
    * Types of endpoints
Name	Example	Description
List resources	/orders	These represent a collection of resources. They should be plural nouns with no identifier in the URL path. List resources can be filtered, sorted, etc using query parameters. Any search that can return more than 1 result should be represented as query parameters on a list resource.
Singular resources	/orders/12345	
These represent a single instance of a resource in a collection. They should be completely and uniquely identified on the URL path. The key can be a made up composite key where we have no valid shadow key.
Nested resources	/profiles/123/paymentMethods	
These represent separately addressable resources under a parent singular resource. They are occasionally useful to extract out when you want an independent workflow around the child resource. Try to avoid nesting more than 2 levels; it hurts composability of the APIs
Reified resources	/registrationRequest	Reification is the act of naming an abstract concept, which is sometimes useful in RESTful modeling. Reified resources generally represent the intent of a change, as opposed to a simple CRUD operation. As such, they tend to avoid PUTs in favor of immutable resources modeling some user action.
Non-resourceful endpoints	/paymentMethods/search	There may be considerations that force us into an intentionally non-resourceful endpoint. For example, you may decide to support searching by credit cards as a POST instead of a GET because we want to keep the credit card number off of the URL. In this case, we are clearly and intentionally breaking the Uniform Interface architectural constraint of REST. To clearly indicate this as intentional, we should put a verb on the path to label this as RPC instead of RESTful.

* Analysis
    * Show example user story with Acs
* Documentation
    * Types, principles
    * Spec approaches (incl. spec first)
    * Author in the code, deploy to portal
    * TEST!!! how to test (manual, mountebank, swagger-test)
    * Tools
        * https://swaggerhub.com/?
* Tooling
    * Gateways vs client load balancing
    * anti patterns
* Testing
    * Test data
    * need for environments
    * service virtualization
* Business value
    * Treating as product

![business model canvas](/images/api-business-model-canvas.jpg)

    * Vision statements
* Design affordances
    * style guids
    * REST
    * principles
    * errors
        * Apogee’s advice - add developerMessage and userMessage
    * Affordance is a design property that communicates how something should be used without requiring documentation.
    * Avoid meta-abstractions (e.g. content instead of articles, comments, papers, etc)
    * Avoid deep nesting, ignores other relationships and makes navigating hierarchy harder
    * Projection, pagination (offset, limit), sorting, filtering
    * use verbs for non-resources
    * match camelCase of JSON rather than ruby_style or DotNetStyle or pretty-style
    * Keep URL, query, and body style the same
    * Status codes
        * Yes there are esoteric and specific status codes, and even generic status codes generic for the web but not for APIs. You might think that using a 302 redirect is a clever way of managing versioning in your API, but ask yourself a question - as someone who has written code to consume other people’s APIs, have you ever implemented the code to handle a redirect? Show some empathy for your users.
* NFRs
    * service harness
    * mobile battery = binary protocol?
* Versioning
    * Don’t use dates (Twilio) or fun names (Ubuntu) as it hinders Obviousness
    * Redirects, but how many of you have actually implemented redirects in your clients?
    * Facebook/Google approach of allowing non-versioned requests violates Obviousness. One gives you the newest, one gives you the oldest supported, but neither is obvious from framing up the request
* Analytics
    * Big data events - just publish request/responses (e.g. successful registration = 200 response code)
* Event Driven Architecture

* Context Boundary selection 
    * should it be tightly focused like Walgreens photo print? An ecosystem like AWS?
* Monetization strategy 
    * Extending an existing product like the Walgreens photo print
    * Freemium  like Google maps
    * Twitter famously having to shut down API clients when they started to feel like they were competing with the app
* Staffing for it
    * Day in the life of a product owner
    * The Technical BA / Analyst Developer conundrum
    * What QA looks like
* Technology Strategy
    * Should you provide a client? 
        * Good models: Heroku toolbelt, AWS cli
        * Risks: can lead to tight coupling, can cause developers to put off deeply understanding the thing they're interacting with, can lead the team providing the API to hide biz logic in the client
    * Security
        * cors keys encryption (at rest, in transit) 
        * oAUTH, SAML, IdP blah blah ...
        * Download the brain of Cade Cairns
        * Download the brain of Daniel Somerfield
    * API Design .......... (see your thread here, others...)
* Program mgmt
    * Sequence APIs before channels
    * Otherwise always creates rework and misalignment

Your differentiator isn’t going to come from the  next feature or app you get out. It’s going to come from your ability to move faster than your competitors.

Bibliography:
https://pages.apigee.com/rs/apigee/images/api-design-ebook-2012-03.pdf

api gateways
-run-time vs client-side? (could be library)
-team models
-distributed vs monolithic
- you should never NOT proxy - lose all sorts of levers to add monitoring, traceability, etc (even netflix uses it for arch discovery)
  - interception points are needed to evolve 
- can’t inject unnecessary latency
- whatever is good for public apis is good for internal apis
- Sonic: 
As a DAPI app progresses through the pipeline, it should be deploying its swagger file into our API Gateway for each profile it deploys to. E.g.: when a new version of customer-api goes to QA, the swagger.json file that describes the contract for that version should be published into the QA Api Gateway

ACs:
* If a deployment of an app to a space is successful, a deployment of that app's swagger.json into the correspondent API Gateway should follow

NOTES:
    * Deploying a new swagger contract into the API Gateway seems to wipe clean any information that was there before the deployment, so every deploy has to be COMPLETE and completely scripted

https://www.youtube.com/watch?v=7PCPJILgfUs&feature=youtu.be&list=PLEx5khR4g7PJwebFxZrJmgqw_7Dy4nAmq
- APIs are your form of communication between developers
- APIs intended for developers, not computers

SLO’s and monitoring, Google’s error budget

talk about layering apis, ala telus, usage -> cri -> ocssa, with ocssa acting as “gateway” to SAP-CC (rating engine), but cri making it look more like previous rating engine (amdocs)


compromises on REST
- use /profiles/me for security
- avoid CC searches using URLs

Tools:
- ESBs -> API gateways
- lessons are the same: a proxy is good, logic in the middle is bad
- use for ddos, rate limiting, identification / authentication (not authz)

Legacy patterns
- Use shadow id to avoid exposing unnecessary data to consumers
 - SWA example: pricing services required dates, route, fare type. Just encode in id and let consumer pass id
  - TELUS example: get appointments requires service type (internet HS, internet LS, tv, etc), not relevant to consumer. Embed in shadow id


From here by Pamela Fox, here are the questions devs have:
* Do I want to use it?
    * Show others who use it
    * Documentation
    * Interactive explorer
    * Licensing
    * Transparent pricing
    * Stability
    * Case studies
* How do I sign up?
    * Best answer: no need to, no API key
    * Automated key signup with usage dashboard
* How do I get started?
    * Downloads for every environment
    * Client libraries for every language
    * Hello world example
* How do I use it?
    * How do I learn to use it?
        * Documentation: comprehensive, running code, navigable, searchable (including on google)
    * Do I enjoy using it?
        * API design: familiarity, compatibility, simplicity, debuggability
* How do I get help?
    * Forum
    * Issue tracker

 

Testing
* Diff spec with prod to detect breaking changes
