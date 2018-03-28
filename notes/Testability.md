Lot about loose coupling:
- avoid binary dependencies - team coupling
- avoid expensive middleware, decentralize
- build monitoring in, use synthetic transactions in prod
- protect the database
     - the schema is the service contract, not the data schema.
     - anything that causes extra mapping from app to db is waste
- 

Coupling issues:
- binary dependencies = team coupling (frameworks, libraries)
- middleware = team coupling (Tibco)
- WSDL, WADL, XSDs, strict schema validation, exporting domain model over the wire
     - Talk about CDCs
- Decentralize test ownership (“service virtualization”)

Testability:
- JFHCI - configuration is code, but makes testing hard
- Feature toggling
- Subcutaneous support with separated API

Remove friction from testing:
- Environments
- Embedded Jetty


Environments foundation
direction of the request is the direction of the test

Always start from dev workstation and work towards production not from production and working backwards
- TBS framework not supporting command line options for perf testing, not making it easy to experiment with testing
- monitoring
- open source make it easy to test like it’s in prod
- isolated dbs
/
Make it simple:
- evolutionary db schema design
REST
- browser, easy to teach semantics to QAs, pretty printing
- CDCs
Text
composability beats contextuality
