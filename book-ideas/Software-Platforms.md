Put together sales pitch
We have ability to associate TW brand with emerging trend (software platforms)


Software Platforms

# Section 1: A platform operating model

## Digital Transformation

Principles of Digital Transformation
* Persistent teams
* Incremental funding
* Customer focused instead of functionally focused
* Learn through doing
* Adapt with data
* Strong ownership with architecture / team alignment
    * Organize around the outputs of software delivery
* Backlog ownership
* Digital Platforms


Traditional cost-cutting approaches are like derivatives; transformation like integrals
 Focus on velocity vs. acceleration

Sourcing strategy = hard to do with knowledge outsourced

Metrics and signals
"Jeff Bezos believes that most initiatives take five to seven years to pay dividends for Amazon—but positive changes in customer behavior and team problem solving provide early signs that initiatives are on the right track"
- https://hbr.org/2018/05/agile-at-scale

## Product model

Direct technical integration leads to spaghetti
Same with extreme coordination
POs as the "API interface" into teams

## Platform as supporting infrastructure

Netflix "paved road"

coefficient of friction multiplied across portfolio
also tackling the long tail of risk

The traditional approach to IT relied on "integration" for runtime service fulfillment and "tickets" for 
 construction time service fulfillment.
Platforms change both of those.
Integration should be a bad word.

## Comparing to Platform Businesses

Connecting producers to consumers
Are internal platforms multi-sided?
* If you stretch the idea, you could say the platform connects shared services and app developers, shared services including:
    * Security
    * System administrators
    * Infrastructure
    * Database
* Internal platforms support a scalable shared services model through platform ecosystems, exposing consumer needs

In a platform world, "if you have an opinion, then you need software developers"

Platforms are a means of centralizing expertise, while decentralizing innovation to the customer or user
from https://www.thoughtworks.com/insights/blog/platform-tech-strategy-three-layers

Delivery acceleration comes from network effects?

|          | Shared Service Side | App Dev Side |
| -------- | ------------------- | ------------ |
| Positive | Removes manual workflow bottlenecks | Creates demand justifying investment on platform |
| Negative | Overly controlling workflow? | Diversity of needs overwhelms capacity  |


Chicken and egg problem
* Have the power of fiat within an org
* We tried the “thin wedge” approach: start with a couple areas of business pull and build just enough for them, but with a clear eye to the future. The vision is needed because you’ll never justify the expense of a platform on the back of one or two projects
* Can also do the “extract” approach - don’t build a platform, recognize the inefficiency after the fact, and extract a platform
* USAA, and probably others, have also tried a more org-based approach. I hesitate to call it the “field of dreams” approach because that’s too derogatory, and there are times where I think this may be the right way to go. In USAA’s case, they created a payments platform based on deep knowledge of how functionality is used across the org and a tech-based vision of future business opportunities.

The Unix way:
Tools, not applications
The ability to recompose tools in ways the creators never imagined
Outsourced and accelerated innovation

Twitter's economic argument: http://www.gigamonkeys.com/flowers/
Effectively, building the ability to accelerate over time

## Engineering Culture

Acceleration needs more than just tools, comes from behaviors, incentives, and structure.

Autonomy:
* Self-service
* Self-direction
* Self-resolution

Aim for distributed autonomy. Product thinking is the mechanism
- Product autonomy = the power of prioritization
    - Conflict resolution options:
        - Traditional escalation
        - Donate capacity
        - Own it yourself
        - Find another producer
    - Allow duplication (Bezos "2 is better than 0")
    - Ryan's "Zamboni" metaphor: let the ice get scratched up, then clean it up afterwards
    - Backlog coupling has at least an order of magnitude effect on productivity and degrades over time
- Architectural autonomy = the power of release independence
    - Engineering for autonomy
    - 2 paths towards shredding shared services:
        - self-service platforms
        - moving some capabilities directly in the team (e.g. db migrations)

Composability - should be able to use services independently

Treating internal development teams as customers
How SAFe / portfolio management approaches interfere with a product engineering culture
- Trade off improved alignment for reduced autonomy

Aim for externalizability (Yegge's rant)
 https://techcrunch.com/2017/05/14/why-amazon-is-eating-the-world/
 
 The ecosystem-based view of value creation is in stark contrast to the traditional resource-based view of value creation,
 where control of resources was an important source of competitive advantage. (from Platform Scale)
 
 "Riot Games, the developer of the wildly successful multiplayer online battle arena League of Legends, is redesigning the interfaces between agile teams and support-and-control functions that operate conventionally, such as facilities, finance, and HR. Brandon Hsiung, the product lead for this ongoing initiative, says it involves at least two key steps. One is shifting the functions’ definition of their customers. “Their customers are not their functional bosses, or the CEO, or even the board of directors,” he explains. “Their customers are the development teams they serve, who ultimately serve our players.” The company instituted Net Promoter surveys to collect feedback on whether those customers would recommend the functions to others and made it plain that dissatisfied customers could sometimes hire outside providers. “It’s the last thing we want to happen, but we want to make sure our functions develop world-class capabilities that could compete in a free market,” Hsiung says."
 - https://hbr.org/2018/05/agile-at-scale

### Alignment techniques

okrs as an example of cascading goals
military: commander's intent vs mission tactics

talk about 3 gaps from the art of action:
- Plans -> Outcomes (Knowledge)
- Plans -> Actions (Alignment)
- Actions -> Outcomes (Effects)

Make it easier to solve with smaller batches

# Section 2: A software platform architecture

## Mental model

![mental model](/images/Platform-org-mental-model.jpg)

## Delivery Infrastructure

## Democratized Data

## Advanced analytics

Uber's Michelangelo
AWS

## Business Capabilities

### Dealing with legacy

Approaching legacy strangulation
* Strangulation? - A good option, but very rarely finished. You start by showing the path to building new capabilities that become incrementally cheaper, and IME, new capabilities usually drown out the actual sunsetting effort in demand intake. The risk is that you can end up with something even more complex than what you started with, because you have to understand the old, the new, and the “temporary scaffolding” between them. I think Gap has a lot of this dysfunction.
* Build new platform greenfield and incent customers to use it. Vision Critical tried this with their flagship app, allowing external customers to continue to use their old moneymaker but building a compelling competing product and hoping they’ll switch (I think in the end they had to add lots of integrations). USAA is trying this with their platform -- the old is too monolithic and there’s no obvious path to get to good tech in any reasonable timeframe, so they’re building a greenfield platform on new tech. The old platform had its hooks in everything which made incremental migration difficult. The new is modular and you can use whatever components you want. You’ll probably have to rewrite your services to use it, but that’s still compelling for large parts of the org who are trying to modernize
* Versioning. This is similar to above but the switching costs are often cheaper. A new version can be, under the hood, a new greenfield product, but with some effort made to maintain some degree of interface compatibility with the old product(s). Customers will expect to have to make some changes to adopt the new version, so there is incentive on the producer to make it compelling to change. Different customers migrate on different timescales
* Fiat - management forces people to use the new (and funds accordingly). I’ve read that both Google and eBay are on the 5th complete rewrite, top to bottom, of their tech stacks, and heard anecdotally that Google has traditionally mandated usage of new platform over legacy. They also have more money than God, but it seems reasonable to me that this may sometimes be your best option, esp. when you’re in a Bad Spot.
* Branch by abstraction - you might consider this a strategy within the Strangler approach, but worth calling out. Paul Hammant named the approach to juxtapose with the common developer experience of branching within source code, which maybe doesn’t speak to non-techies as well. The idea is that, in step 1, you create a new interface on top of the old capabilities and convert all clients to the new interface. At this point, the interface still routes to the original “platform” code. Step 2 is to create a competing back end and route some of the interface calls to it, maybe for new functionality, or for functionality you’re looking to remove from the old platform. Lather, rinse, repeat, until all of the capabilities have migrated from old -> new. Step N is to remove the interface entirely; it’s just waste when you’re done. Of course, as with all strangler migrations, nobody actually does that. They get bored with it long before that point.

Zhamak's recommendations (https://martinfowler.com/articles/break-monolith-into-microservices.html)
- 1st risk: operational maturity. Start with a couple edge services to address
- 2nd risk: splitting the monolith. 

Paula:
- Legacy Code:  Any code without tests
- Legacy Architecture: Any architecture that has not evolved
- Legacy Systems: Any COTS or custom systems that are not supported
- Legacy Processes: Any processes that are not measured and improved
- Legacy Thinking: Belief that existing code, architecture or processes are too complex to understand, and can never be changed

#5 is by far the most challenging legacy issue
But, remember: Most ‘legacy’ is what currently runs the business and drives revenue.


## Future Areas

### Experimentation platform

https://blog.acolyer.org/2017/09/29/the-evolution-of-continuous-experimentation-in-software-product-development/

### Front end delivery

FB mobile platform
Experiences to channel matrix:

![mapping experiences to channles](/images/Platform-org-mental-model.jpg)

Allows different ways of drawing teams. Channel teams become service delivery platforms
- Web can support microsites building reverse proxy / session infra
- mobile is monolithic deploy
- mobile CD / release infra

### Innovation

Using Wardley maps to decide team boundaries
- Stable = more granular boundaries for scale
- Cutting edge = own more of the stack for speed


## Random

Products all the way down

When not product
Support ticket with other team
Other team has to manage capacity
Requirements handed down tagged by a funding bucket

2 types of autonomy:
Product autonomy - the power of prioritization
Architectural autonomy - the power of release independence

Products:
Impenetrable boundary
PMs have two things: stakeholders and the power of prioritization
Requirements managed for maximum market effect
Leaders can bootstrap products when market too inefficient to do it (e.g. platforms)
Horse trading to manage most conflicts
Roadmaps based on customer feedback
Treat as if external customer
Products are owned. Aim for self-service but ownership is really the key

Capability = what
Product = how, self-service access to capability

Product mgmt:
Understanding what’s available in the ecosystem is a product mgmt capability, not an architectural capability
Understanding how to scale, tension between solving one customer’s need vs how to scale

Org has to align to physical assets of software delivery
Trying to ignore that fact is like trying to ignore the laws of physics

Channels as service delivery mechanisms
https://www.quora.com/How-is-the-mobile-team-at-Facebook-structured



https://techcrunch.com/2017/05/14/why-amazon-is-eating-the-world/

Ownership matters
Internal open source
AirBnb and Google support changing any code anywhere, but treated as open source with owners of the code having to approve the PR

Why organizing around “outcomes” fails
Collisions, build failures, defects, release management, quality and architecture curation

Outcomes focus
Communication matters: http://www.businessinsider.com/tesla-elon-musk-how-to-communicate-2017-8




