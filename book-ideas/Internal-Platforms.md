Internal Platforms



The Unix way:
Tools, not applications
The ability to recompose tools in ways the creators never imagined
Outsourced and accelerated innovation



Questions to explore with Brandon
How do we slice a platform if building it for the first time?
We tried the “thin wedge” approach: start with a couple areas of business pull and build just enough for them, but with a clear eye to the future. The vision is needed because you’ll never justify the expense of a platform on the back of one or two projects
Can also do the “extract” approach - don’t build a platform, recognize the inefficiency after the fact, and extract a platform
USAA, and probably others, have also tried a more org-based approach. I hesitate to call it the “field of dreams” approach because that’s too derogatory, and there are times where I think this may be the right way to go. In USAA’s case, they created a payments platform based on deep knowledge of how functionality is used across the org and a tech-based vision of future business opportunities.
How do we slice a platform if replacing existing platform?
How should organizations approach legacy replacement? 
Strangulation?
A good option, but very rarely finished. You start by showing the path to building new capabilities that become incrementally cheaper, and IME, new capabilities usually drown out the actual sunsetting effort in demand intake. The risk is that you can end up with something even more complex than what you started with, because you have to understand the old, the new, and the “temporary scaffolding” between them. I think Gap has a lot of this dysfunction.
Bridging architecture?
Would need an explanation of what you mean to comment...
Patterns?
Build new platform greenfield and incent customers to use it. Vision Critical tried this with their flagship app, allowing external customers to continue to use their old moneymaker but building a compelling competing product and hoping they’ll switch (I think in the end they had to add lots of integrations). USAA is trying this with their platform -- the old is too monolithic and there’s no obvious path to get to good tech in any reasonable timeframe, so they’re building a greenfield platform on new tech. The old platform had its hooks in everything which made incremental migration difficult. The new is modular and you can use whatever components you want. You’ll probably have to rewrite your services to use it, but that’s still compelling for large parts of the org who are trying to modernize
Versioning. This is similar to above but the switching costs are often cheaper. A new version can be, under the hood, a new greenfield product, but with some effort made to maintain some degree of interface compatibility with the old product(s). Customers will expect to have to make some changes to adopt the new version, so there is incentive on the producer to make it compelling to change. Different customers migrate on different timescales
Fiat - management forces people to use the new (and funds accordingly). I’ve read that both Google and eBay are on the 5th complete rewrite, top to bottom, of their tech stacks, and heard anecdotally that Google has traditionally mandated usage of new platform over legacy. They also have more money than God, but it seems reasonable to me that this may sometimes be your best option, esp. when you’re in a Bad Spot.
Branch by abstraction - you might consider this a strategy within the Strangler approach, but worth calling out. Paul Hammant named the approach to juxtapose with the common developer experience of branching within source code, which maybe doesn’t speak to non-techies as well. The idea is that, in step 1, you create a new interface on top of the old capabilities and convert all clients to the new interface. At this point, the interface still routes to the original “platform” code. Step 2 is to create a competing back end and route some of the interface calls to it, maybe for new functionality, or for functionality you’re looking to remove from the old platform. Lather, rinse, repeat, until all of the capabilities have migrated from old -> new. Step N is to remove the interface entirely; it’s just waste when you’re done. Of course, as with all strangler migrations, nobody actually does that. They get bored with it long before that point.
Vendors?
Assuming you mean COTS/SaaS products, I think the key would be to abstract the capabilities, not the product. Don’t create a “Peoplesoft API.” PeopleSoft already does that. Instead create an “HR API” or something like that. You’ll still need to change it and customers when you switch back ends, but it’s better than nothing.
How do we slice an existing portfolio with tech considerations?
What’s our advice for handling existing tech? New tech? Emerging tech?
I like Wardley maps for helping to think through this. A key idea is that the more commoditized the tech is (e.g. infrastructure), the less you want to own it, so look for SaaS offerings and offer up as platform capabilities. The more emerging tech is, the more you’ll need to innovate, so form teams owning more of the problem set (probably avoiding converting it into platform capabilities). In the middle, you’ll need to balance innovation and optimization, so you can separate out platform capabilities for acceleration and scale, as the interaction patterns between teams are a bit better understood and stabler.
I think this is also a good mental framework for thinking about hypothesis driven development. The closer you are to the commodity side of the spectrum, the less HDD applies. You can get a lot closer to just “knowing” what the right thing to do is by looking at what the industry is doing. The closer you are to the genesis side of the map, HDD baby!
That said, I think a lot of the product practices you’re preaching still apply to platform products. The only difference is that the customers are developers, user experience = developer experience, and that oftentimes the “marketplace” is internal so the currencies are harder to track.

Potential outline structure
Chapter: Defining portfolio seams
Technology product seams
Architectural seams
Considerations? 
Build for flexible infrastructure
Technology is structured around business
Architectural design changes as new patterns emerge
Chapter: Slicing for platforms?
Slicing (new) platform work
Slicing for legacy platform replacement

--- WIP limit ---

Other questions to explore
How/where do technology choices fit in portfolio decisions?
what is the role of an enterprise architect (other roles?) when the organization is periodically reviewing the LVT goals and bets?
If tech moves slower, what’s our advice for managing the tech portfolio as the LVT changes?
How should an organization think about their technology portfolio? (techradar style??)
What is the role of a technical person (tech lead? Architect? etc) in portfolio creation and evolution. What qualities or behaviors make people successful in this space vs not?

--- (ideas / random thoughts below) ---
Defining technology / architectural seams
How the LVT and technology choices fit together

Principles for technology slicing?
Technology is structured around the business, and not vice versa 
Flexible infrastructure
Rapid build and release
Promote active refactoring
Architectural design changes as new patterns emerge
Proof of concepts are used a way to learn new technologies?
Use system thinking to understand the dependencies and complexity of the architecture. 
Focus on APIs and employ consumer-driven contract testing to have contracts between delivery/platform/ services teams and use it as a catalyst for evolving the architecture.
Build abstractions as needed especially with proprietary applications to make the system more testable, loosely coupled and easier to change. 
Use techniques such as “three strikes and refactor,” emergent design, encapsulation, and abstraction not only to clean the codebase, but to refactor and evolve the architecture.



