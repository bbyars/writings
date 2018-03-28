QA Value:
- Preventing bugs (traditional QA)
- Detecting bugs (traditional monitoring)
- Remediating bugs (traditional support)

QA strategy incorporates all 3
- look at logs, alerts, graphs, trends to improve quality of product

Security:
- Bring visibility to team, show them how their app is being attacked
- Business brings risk profile
- Segment risk by infra / functionality (tokenization, dev networks)
    - benefits of micro services involves segmenting risk

Devops
- Commoditize the release process
- Standard work, continually increase the signals you pay attention to as sensitivity to error improves
- This is production (in the manufacturing sense) and should be treated as such

Development
- This is design and should be organized around learning and rapid feedback

Broader than customer facing dev
- SAP, POS, enterprise

3 types of teams:
1. agile teams - you know the problem, and mostly know the solution
2. innovation teams - you know the problem and need to discover the solution
3. entrepreneurial teams - you know you have a problem but need to crystallize it (lots of ambiguity)


Types of caching:
- App cache
- Network cache (proxy)
- Single server cache (files on disk)
- Global Server cache (memcached)

Cost of motivation: 
https://blog.kainexus.com/continuous-improvement/culture-of-continuous-improvement/the-economic-cost-of-a-negative-company-culture

Risk:
Insurance tables for smokers

https://hackernoon.com/wtf-is-a-strategy-bcaa3fda9a31

This is the concise overview I mentioned  of how vision, strategy, roadmaps and execution all fit together

Great read!

Much longer read, but I also got a lot out of Warfighting (the Marine's manual, which has a lot to teach us about agile). The concepts are very similar:
* Mission -> The objective of being in a certain theater of war
* Strategy -> "Commander's intent", what the higher ups are trying to accomplish (e.g. control the bridge to prevent the enemy from escaping across the river). Combined with "Main effort" - the unit that we prioritize support for.
* Roadmap -> "operations" -> commander-provided theory of how the unit will accomplish the mission
* Execution -> "Mission tactics" -> what the subordinates actually do when they're being shot at. Near absolute autonomy so long as it aligns with commander's intent.

Security
https://www.youtube.com/watch?v=apma_C24W58&feature=youtu.be
Need 200 firewalls to keep up with latency of a switch
Firewalls no longer useful outside of separating internet from your network
The security boundary is not the service
Every single service should imagine its on the public internet
Layer 3 and 4 no longer appropriate for thinking about security, needs to be layer 7
every service should be authz and authn

Org:
The electric dynamo took 50 years before it increased productivity: http://www.bbc.co.uk/programmes/p057xsl0

Product / Service orientation:
* https://techcrunch.com/2017/05/14/why-amazon-is-eating-the-world/
* Pitfalls of vertical integration: initial cost-savings through insourcing, but market inefficiencies with captive customer and no competition erode those over time
* Amazon converting contact center as external service (Amazon Connect) - if failure externally, indicates the internal operation is inefficient
    * Converted survey-based feedback loop into revenue-based feedback loop
* Fulfillment by Amazon can even ship orders not sold on Amazon; exposes internal warehouse ops as product
    * 3rd party seller services totaled $6.4B in Q1 2017, 25% of revenue
    * Taken largest cost center (fulfillment and shipping) and externalized it, preventing bloat
    * Enormous bootstrap costs, leaders had to create when internal market too inefficient, operated at loss for long time
* Productized tech (AWS), Fulfillment (FBA), COGS, shipping
* Key advantage they have over everyone else is that they are forced to use their own services; nowhere for poor performance to hide
* Found a way to beat the Innovator’s Dilemma
