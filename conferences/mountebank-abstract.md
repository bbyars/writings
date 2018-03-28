Modern distributed architectures require a different approach to testing. Balancing the need for confidence with the need for release independence requires us to take a distributed approach with our test pyramid as well as our service architecture. We'll explore a microservices test strategy using mountebank, a cross-protocol service virtualization tool.


Decades after the invention of the electric dynamo, most factories still relied on steam. Electricity allowed distributing power in smaller quantities throughout, radically changing factory design, but breaking the comfort level with monolithic steam power distribution took time.

Though the change curve is accelerated these days, the same pattern is being repeated with microservices. Organizations look to transform by reaping the architectural benefits of distribution, only to discover that those benefits require changes to the organizational processes themselves. Implementing microservices without changing your test strategy — even those strategies that emphasize automation — often lead to a lack of release independence between services. The result is a distributed monolith with all the runtime complexity of monoliths and all the organizational coupling of monoliths.

Service virtualization provides a distributing stubbing approach that supports determinism while promoting release independence. It can be used for black box service-level testing and for robust performance testing. In this talk you’ll learn how to use mountebank, an open source service virtualization tool, to build a comprehensive test strategy that can support independent service releases while maintaining a high degree of test confidence.

We’ll explore a continuous delivery pipeline that:
* Shows the similarity between in-process stubbing and service virtualization
* Shows advanced record/replay capabilities
* Examines complex behavior, like stubbing OAuth flows
* Shows how service virtualization fits in the context of contract testing and performance testing
