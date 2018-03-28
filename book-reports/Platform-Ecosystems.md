by Amrit Tiwana

Products that became platforms from 1990 to 2004 enjoyed a 500% increase in innovation, most of which came from outside developers

Platform Drivers:
* Deepening Specialization
  * In software products, # LoC estimated to double every 2 years
  * Increasingly difficult for one company to specialize in all domains
* Packetization - the ability to digitize something previously not digitized
  * McDonald's realized drive through order was nothing more than a voice based interaction
  * Order taker now distributed from store location
  
  
Platform Properties
* Multi-sidedness
* Network effects - the degree to which every additional users of a platform or app makes it more valuable to every other user
  * Can be same-side or cross side, positive or negative
  
  
Principles:
* Red Queen effect - have to run faster just to stay in place
* Chicken or egg - how to get started
* Emergence

All known coordination mechanisms that have served firms well in the industrial age - 
authority, hierarchies, multinationalization, performance metrics, ownership, contracting - are unscalable
to networks of firms as potentially large as platform ecosystems. *Coordination in platforms is achieved instead
by their architecture* - a concept largely absent in business strategy. Architecture thus must earn a place 
in biz strategy for platform markets.

Value Props
* Massively distributed innovation
* Risk transfer
* Capturing the long tail
  * Allows capturing the long tail of innovation that would otherwise be economically unfeasible
  * App developers might find the niche markets lucrative enough to pursue
* Competitive sustainability

Governance control mechanisms:
* Gatekeeping (iOS)
* Process
* Metrics
  * Rarely effective in platforms. App developers set most criteria for their apps and market determines winners
* Relational (Linux)

Metrics:

| Metric | When | Type | Definition | 
| ---    | ---  | ---  | ---------- | 
|Resilience|Short Term |Operational|Capacity of subsystem to function acceptably in the event of a failure|
|Scalability|Short Term |Operational|Degree to which functional performance and financial viability is size agnostic|
|Composability|Short Term|Strategic|Ease with which changes can be made within a subsystem without compromising reintegration|
|Stickiness|Mid Term|Operational|"Eyeball time" between a subsystem and its primary users|
|Platform synergy|Mid Term|Strategic|Degree to which an app is designed specifically for a particular platfrom|
|Plasticity|Mid Term|Strategic|Degree to which a subsystem can deliver functionality that it was not originally designed to deliver|
|Envelopment|Long Term|Operational|Swallowing by a subystem of the functionality of a solution in an adjacent market with overlapping users|
|Durability|Long Term|Strategic|A subsystem's endurance in a competitive marketplace|
|Mutation|Long Term|Strategic|Unanticipated creation of a spinoff subsystem that inherits some of the properties of the parent system but with a different purpose|

Examples:
* Resiliency
    * MTTR for failure caused outside subsystem
* Scalability
    * Increase in latency/responsiveness/errors per additional 1000 users
    * Direction of shift in financial breakeven point per 1,000 fewer users
* Composability
    * Integration effort (person-hours) per internal change
* Stickiness
    * Change in hours per end-user session over time
    * Change in averaged end-user sessions per week over time
    * Change in API calls made by app on average as platform ages
* Platform synergy
    * Change in # functions called by app to APIs unique to platform
* Plasticity
    * Avg count major features added to subsystem per release over its lifetime
* Envelopment
    * Count of successful envelopment moves
    * Count of envelopment attacks rebuffed
    * % new subsystem adopters using enveloped functionality
* Durability
    * Change in % of initial adopters who remain active users
    * Change in platforms % of apps released that are subsequently updated at least 1/year
* Mutation
    * number of unrelated derivative platforms relative to rival platforms
    * % of carryover users at outset of derivative subsystem
    * Growth of an app into a platform
    
    
## Platform Modular Operators

Think of them as the alphabet or baby steps to describe evolution

* SPLIT - subdivide a monoilthic system (only way a monolithic system can be modularized)
* SUBTRACT - Removing an app or the platform from the ecosystem
* SUBSTITUTE - substitute one component with another
* AUGMENT - adds new functionality to ecosystem without requiring change elsewhere
  * INVERT - subsume into platform capabilities widely shared by many apps in the ecosystem, key mechanism by which redundant implementaitons of common functions get consolidated, but can wipe out business of app developers specializing in that niche
  * ENVELOP - Add new module to ecosystem that replicates functionality of adjacent solution whose user base overlaps with your platform
* MUTATE - Make copy of original ecosystem to create derivative system intended for use in a different application domain
  * PORT - (applies primarily to apps) Replicate functionality to allow it to function on a different platform
  
  
