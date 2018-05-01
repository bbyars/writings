The Path Towards Configuration as a Service

https://docs.google.com/document/d/1EetGIJAGRDrlhp6mgP0oMQ7KioHIos625cs-HZGvUWQ/edit#

[One of our goals with the ThoughtWorks Applied Engineering Lab is to understand how structured offerings in the Platform as a Service (PaaS) space enable Continuous Delivery. This is the first in a series of blog articles that will capture some of our findings around managing configuration in a PaaS.] 

With the ever-evolving world of platforms, application configuration has secured a first-class position in the “as-a-service” ecosystem as architects commonly reach for highly consistent, distributed key-value stores to manage configuration. Such services overcome the limitations of managing configuration on a per-node basis across a dynamic platform. However, several organizations we’ve talked to have indicated that it’s not always clear how to integrate configuration services into their Platform as a Service (PaaS). In this article, we’ll examine the world of configuration holistically and explain the forces and constraints that would push you towards one of these services.  Future articles in this series will explore patterns of configuration updates using such a service.
What is Configuration?
“Configuration” is one of the most overloaded terms in the industry, especially for those of us who have worked with COTS products that are “configured” by typing Java code into text boxes on a graphical interface describing a workflow. The variety of ways in which the word is used prevents an easy definition.

As a first pass, we’ll define configuration as non-transactional data external to the source code of the application that changes its behavior. By “non-transactional data,” we’re excluding the core data of the application; however, as we’ll see below, sometimes the lines blur between application data and configuration. This broad definition intentionally includes the following categories, each of which can have a separate life-cycle:


Categories of Configuration


Library configuration
 log4j, Spring, Hibernate, etc.  Commonly stored in XML files alongside the source code.


Reference data
May include postal codes and shipping charges.  Usually lives in lookup tables in the application’s database.
Application runtime configuration
e.g., how many items to display per page, session timeout.  Often starts out in a configuration file.
Feature toggles
Can be used to hide work in progress, to allow operators to turn part of a system off for resiliency under load, or to test out new functionality on a subset of users.
Node configuration
e.g. port mappings and system dependencies.
Runtime configuration
e.g. JVM settings. While traditional application deployment strategies included running multiple runtimes on a single node (and even multiple applications under one runtime), the rise of containers in a PaaS has created a one-runtime-per-node paradigm, which effectively gives runtime and node configuration the same life-cycle. 
Environment configuration
Includes the URLs for integration points and connection strings. In a cloud-based infrastructure where nodes spin up and down at runtime, environment configuration can be highly dynamic. Some of the services we’ll look at in subsequent articles include service discovery as an explicit offering, which supports dynamic discovery of services in an ever-changing environment.


Forming a comprehensive configuration management strategy requires looking at each bit of configuration through several lenses. 

Who changes the configuration (developers, operators, product managers, end users)?
How secure does the configuration need to be?
How frequently does the configuration change? Does it need to change independently of a deployment?
What is the scope of the configuration (per request, per tenant, per application, per instance, per environment, global)? For instance, user configuration on a multi-tenant SaaS offering would need to be per request, as it has to involve the user making the request in the decision, whereas integration URLs would be per environment.
How will the application respond to changes in the configuration? Is restarting the application sufficient (or necessary)?

We’ll examine the various configuration storage strategies against those questions in the next section.
Where Does Configuration Live?
Each bit of configuration needs to live somewhere. The following options are common:
Commit Configuration into the Application’s Source Repository
In many cases, moving configuration as close to the code is the best option. This is particularly true for library configuration. The kind of wiring class dependencies together that Spring made popular should be treated as source code even if it’s done in XML files. It is clearly not expected to change outside of developer control, and changes require the same kind of testing as any other source change.

A more interesting situation occurs with business-facing configuration that changes an algorithm, for instance, by tweaking the amount of discount per customer type. The more mature your organization is in embracing Continuous Delivery, the more Oren Eini’s advice to JFHCI makes sense (JFHCI stands for “Just Hard Code It,” roughly speaking). Some teams find that putting such configuration directly in code improves its testability, maintainability, and understandability. If you can wait for developers to make the change and for a new deployment, then maybe you don’t need configuration at all.

Configuration that lives with the app and follows it on deployment can be read at application startup, which means you don’t have to think as hard about life-cycle management. For instance, you can use singleton controllers, as the configuration passed into their constructors will not change during the lifetime of the process. Some applications are designed to watch for configuration file changes at runtime and respond accordingly, but since you don’t have access to the filesystem in a PaaS, this approach won’t work.

A common approach is to have configuration files per environment, but this starts to make less sense in a PaaS world where environments can be short-lived and ad-hoc. Secure configuration, such as credentials (which often vary per environment), should not be checked into source control, making this approach a poor choice for sensitive data. This is sometimes resolved by first encrypting the data and ensuring that the runtime has access to the encryption key. A variant is to store such configuration in a separate source code repo and lay down the environment-specific credentials in a file during deployment. This increases the security by limiting access to the secure repository but is still limited by expecting a static set of environments. Neither option is a natural fit in a PaaS.
Make Configuration Part of the Environment
Heroku’s influential advice around building twelve factor apps includes storing configuration values as environment variables. This allows a clean separation between configuration changes and application deployments, and is the default approach in many PaaS offerings. This is conceptually identical to passing configuration in on the command line.

One reason Heroku gives for preferring environment variables over files is that it’s harder to accidentally check sensitive data into source control, solving the data-at-rest problem inherent in configuration files. Cloud Foundry exemplifies the pattern by adding secure credentials to the VCAP_SERVICES environment variable when you bind your application to another service. 

However, you have to careful about spawning untrusted child processes, as they will have access to the same environment, and unless you explicitly change the user, will have the same identity privileges. This is a rare occurrence in a PaaS, since no platform will monitor spawned processes out of the box anyway.

Configuration changes stored as part of the environment require an application restart. Because this is an administrative activity, environment variables are generally a poor interface when business people own the configuration.
Use an Application Interface
When a value needs to change at runtime, the easiest way to be sure that the application will respond appropriately is to actually write the code that allows you to change the value through the application itself. This is a very common approach with feature toggles in particular. 

The downside is that it requires an additional interface. An HTTP-based administration page on an application or service will do the trick at the cost of increasing the attack surface area since you need to ensure that only administrators can make changes. Storing the configuration directly in the database generally ensures all nodes get a consistent view of it. However, configuration in the database mixes data types with very different life-cycles together, a pain that’s felt when you want to promote configuration in a test environment to a production environment.

Some organizations rely on a different protocol to clearly separate the administrative interface from the user interface, JMX being a popular choice on the JVM. Unlike administrative screens that tend to write changes to a database shared by all nodes, JMX changes usually affect only the running process. This incurs location challenges on a PaaS, as automation will have to update the JMX values on each node, and the dynamic nature of a cloud infrastructure makes it harder to know which nodes to update, leading to potential consistency problems.
Use a Centralized Configuration Service
While the operating system primitives of configuration files and environment variables do scale, operational management of configuration on a per-node basis does not. Ever since Google published a paper describing what they called a “distributed lock service” that they built for internal use, large-scale distributed systems have looked to key-value data stores to manage configuration at scale. Since configuration management is not a high-write activity, such stores have focused on providing highly consistent views of configuration across multiple data centers. They are a natural fit for the cloud-based architectures that take advantage of a PaaS.

Using a configuration service neatly separates the management of the configuration from the use of it. Administrators can change the data in the configuration service rather than the application, which allows centralization of security and operational considerations such as auditing, authentication, and authorization. 

Elasticity is an important driver towards a centralized configuration service since it provides a consistent view of configuration even as new nodes spin up. Some service infrastructure tools -- Consul, for example -- combine configuration capability with service discovery, maintaining health checks to ensure the connection information is always in sync with the actual running services.

A centralized service gives the application flexibility in determining how to respond to changes, though it may require a process alongside the application that listens for changes, an approach that brings some complexity in the typical PaaS container setup. Restarting the application is always an option. For instance, Consul adds an agent process alongside the application and restarts it as configuration changes, passing in the updated configuration as environment variables. If needed, an application can respond at runtime, an approach that Spring Cloud Config assumes. Future articles will explore these solutions.
Summarizing Configuration Storage Strategies
There is no one-size-fits-all approach to managing configuration, and an application will often take advantage of multiple approaches for different bits of data. The table below summarizes how the four storage strategies we just examined support the five questions we should ask about every configuration value.

					  Configuration Storage Strategy



Application Source Repo
Environment
Application Interface
Configuration Service
Change Owner
Developers
Operators
Operators,
Product Managers, End Users
Operators, Product Managers
Secure Data
Not Supported
Supported
Supported
Supported
Change Frequency
Per Deployment
On Demand
On Demand
On Demand
Configuration Scope
Per Application
Per Environment
Per Environment
Any
Application Response
Restart Required
Restart Required
Runtime
Runtime
Centralized Configuration in a PaaS
Centralized configuration services are now a default in microservices architectures, which require flexible runtime environments. While the environment configuration option promoted in twelve factor applications remains good advice, it does not solve the problems of centrally managing configuration and allowing runtime changes.

More and more companies are choosing to run their applications in a structured PaaS to gain the advantages of cloud infrastructure while simplifying its operational management. However, those simplifying assumptions a PaaS brings with it can cause some challenges, and we’ve seen some organizations struggle with how their PaaS-hosted app can take full advantage of configuration services.  In the upcoming articles, we’ll  examine different approaches to updating a running application with configuration changes.
