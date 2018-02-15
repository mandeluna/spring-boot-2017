# spring-boot-2017
Notes from Pivotal Spring Boot conference in Santa Clara

December 7, 2017 11:28 AM

Domain Driven Design
* Domain Driven Design: Tackling Complexity in the Heart of Software, Eric Evans, 1994
* Domain-Driven Design Distilled, Vaughn Vernon

Rohit Kelapure, David Turanski (Pivotal), Rohit Sood (Liberty Mutual)

* Using DDD concepts to break down monoliths into microservices
* Part 1: DDD, CQRS, Event Sourcing (David Turanski)
    * Entities (e.g. Shipment), value objects (e.g. Address) & services
    * Bounded Context: e.g. share some parts of the model between Sales and Support contexts (defined by organizational boundaries)
    * Event-driven Architecture: domain events can populate multiple aggregates within multiple bounded contexts
    * Different contexts have different interpretations of the same domain object
    * Commands trigger events
    * Idempotency of messges
    * CQRS: Command Query Responsibility Segregation
        * Command model -> Generated Events -> Event Store
        * Domain events -> Event Processor -> materialized view
        * If you are doing event sourcing you’re also going to want to do CQRS in most cases
* Part 2:  (Rohit Kelapure)
    * Event Storming -
    * Business Domain Model derived from Business Events
    * Deconstructing a Monolith (8 step process)
        * Define Objectives and Key Results (OKRs)
        * C4 diagrams to identify a vertical slice of components that realize teh flow of events 
        * SNAP analysis
    * Selection of a vertical slice: pick a core domain
        * SNAP - used to carve out a microservice in 15 minutes (or 4-6 hours)
        * Deeper process modeling 2-3 days
    * C4 Architecture Diagrams
        * C1. System Components
        * C2. Container Diagram
    * Decomposition Strategy -
        * Bounded Contexts
        * Value Streams
        * Failure Domains
        * Anti-Corruption Layers
        * Single Responsibility Principle
        * Kitchen Sink
    * Strategies
        * Reduce temporal coupling
        * Strive for autonomy with messaging
            * coupling, eventual consistency, idempotency, duplicate messages (Outbox pattern)
    * Martin Fowler; Event Driven Architecture (youtube http://www.youtube.com/watch?v=STKCRSUsyP0)
        * Event Notification
        * Event Carried State Transfer
        * Event Sourcing
    * Life beyond Distributed Transactions
        * We can’t use distributed transactions so we need to use workflow
    * Event Sourcing is a big undertaking
* Part 3: Real World Experiences (Liberty Mutual)
    * https://philippe.kruchten.com (Technical debt)
    * Conway’s Law: system structure is a copy of an organization’s communication structure
        * 3-tired architecture reflects siloed development teams
    * MVP-3: Separate UI from Database by deploying individual services, still accessing monolithic DB
    * MVP-4: PCF Modernization: Cloud native API based Microservices Architecture
        * Large reduction in number of entitiies (30+ to 6)
    * How do you get to code?
        * Bounded Contexts are never right the first time
        * Domain Driven Design to API-First
