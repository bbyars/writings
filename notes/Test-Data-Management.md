Controversial Opinion:
* TDM tools don’t solve your problem no matter how feature-rich
* That forces us to fundamentally rethink the problem
* Shifting tests to the left removes the need for much of those features
* Test-case set up with appropriate isolation via SV helps
* API-enabled TDM helps in integration
* Simplify your test case to simplify your test data

Goals

* Supports versioning of schemas
* Supports different test missions throughout the lifecycle of delivery, release, and operations
* Supports automated and manual testing strategies
* Supports repeatable and reliable data setup and teardown
* Support different versions of data
 
Test Data Types

Baseline data is developed in support of systems, transactional data is developed in support of testing.
Note: add some definitions

There are two types of data necessary to support a test:
* Baseline or Configuration Data
    * Roles
        * E.g. Administrator, agent, customer…
    * Status Codes
        * E.g. Popup values, error values, prompts, …
    * Business Rules Data
        * E.g. Data used in any business rule evaluation or calculations
    * Domain Specific Data
        * SKU definitions, tax rates, SIC codes…
    * Location Specific Data
        * E.g. Country, state, municipal codes…
* Transactional Data
    * The system under test can function correctly without the data being available
    * Transactions expected to be available before the start of a test case
    * Transactions that have a date or time component
    * Transactions that are related to data in other systems
    * This data conforms the business rules of the system
    * Is valid
    * Is reliable between uses
 
Principles for Test Data Management
 
* Baseline data is created through a repeatable deployment process
* Baseline data is representative of current production values
* Baseline data is versioned along with schema and system changes
* Transactional data is created within the scope of a test cycle
* Transactional data does not contain real customer information
* Transactional data can be verified using the system’s business rules and validations
* Transactional data should be removed after the scope of the test cycle is finished
* Transactional data should be removed if the test fails
 
Support test cycle isolation (tests and system boundaries)
 
Strategies for Creating Test Data

* Systems should have a human readable health and configuration API that verifies the existence and version of baseline data
    * E.g. Health check page, REST API
* Regardless of test type or phase, test cycles have a setup and teardown phase which creates and removes data reliably
    * Automated setup and teardown can and should support manual testing
* Systems have data API’s specifically to support the creation, verification, and removal of transactional data
    * This type of testability should be part of the system scope and objectives
    * It can support date/time dependent setup
* Database refreshes should only be used when a test cycle requires large quantities of data
    * Large scale refreshes should only be used as a last resort
    * Some testing activities, such as performance testing, fit into this category
    * Vendor tools support these types of scenarios but the data maintenance costs should be factored in
* If test data setup is difficult then a review of overall testing strategy should be the first step, not tooling
    * Data setup involving more than one system should be sequenced and bounded
    * Data setup is sequenced through dependency mappings
    * A primary system should be responsible for creation of dependent data
    * Bounded data setup should match the bounded context of the systems being tested
    * Do not setup “end to end” test data without a test mission boundary
    * Circular dependencies of transactional data between systems implies an architecture failure which can’t be solved by test data management
* A separate “smoke test” should be used to verify baseline data setup
    * Avoids false negatives when running transactional based tests


Write article around test data management
Isolation (VC)
Environments
Don't use prod data except for perf
Multi tenancy
Test setup as part of tedt, use apis
