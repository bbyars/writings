Software Platforms

## Comparing to Platform Businesses

Are internal platforms multi-sided?
* If you stretch the idea, you could say the platform connects shared services and app developers, shared services including:
    * Security
    * System administrators
    * Infrastructure
    * Database
* Internal platforms support a scalable shared services model through platform ecosystems, exposing consumer needs

Platforms driven through packetization and deepening specialization, just as platform businesses are
* Packetization of business process encoded in APIs

"If you have an opinion, then you need software developers"

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

Approaching legacy strangulation
* Strangulation? - A good option, but very rarely finished. You start by showing the path to building new capabilities that become incrementally cheaper, and IME, new capabilities usually drown out the actual sunsetting effort in demand intake. The risk is that you can end up with something even more complex than what you started with, because you have to understand the old, the new, and the “temporary scaffolding” between them. I think Gap has a lot of this dysfunction.
* Build new platform greenfield and incent customers to use it. Vision Critical tried this with their flagship app, allowing external customers to continue to use their old moneymaker but building a compelling competing product and hoping they’ll switch (I think in the end they had to add lots of integrations). USAA is trying this with their platform -- the old is too monolithic and there’s no obvious path to get to good tech in any reasonable timeframe, so they’re building a greenfield platform on new tech. The old platform had its hooks in everything which made incremental migration difficult. The new is modular and you can use whatever components you want. You’ll probably have to rewrite your services to use it, but that’s still compelling for large parts of the org who are trying to modernize
* Versioning. This is similar to above but the switching costs are often cheaper. A new version can be, under the hood, a new greenfield product, but with some effort made to maintain some degree of interface compatibility with the old product(s). Customers will expect to have to make some changes to adopt the new version, so there is incentive on the producer to make it compelling to change. Different customers migrate on different timescales
* Fiat - management forces people to use the new (and funds accordingly). I’ve read that both Google and eBay are on the 5th complete rewrite, top to bottom, of their tech stacks, and heard anecdotally that Google has traditionally mandated usage of new platform over legacy. They also have more money than God, but it seems reasonable to me that this may sometimes be your best option, esp. when you’re in a Bad Spot.
* Branch by abstraction - you might consider this a strategy within the Strangler approach, but worth calling out. Paul Hammant named the approach to juxtapose with the common developer experience of branching within source code, which maybe doesn’t speak to non-techies as well. The idea is that, in step 1, you create a new interface on top of the old capabilities and convert all clients to the new interface. At this point, the interface still routes to the original “platform” code. Step 2 is to create a competing back end and route some of the interface calls to it, maybe for new functionality, or for functionality you’re looking to remove from the old platform. Lather, rinse, repeat, until all of the capabilities have migrated from old -> new. Step N is to remove the interface entirely; it’s just waste when you’re done. Of course, as with all strangler migrations, nobody actually does that. They get bored with it long before that point.

## Random Notes

The Unix way:
Tools, not applications
The ability to recompose tools in ways the creators never imagined
Outsourced and accelerated innovation


Platforms are a means of centralizing expertise, while decentralizing innovation to the customer or user
from https://www.thoughtworks.com/insights/blog/platform-tech-strategy-three-layers
