# Software Architecture Patterns by Mark Richards

[Link to the article](https://www.oreilly.com/content/software-architecture-patterns/#sapr_0202_img)

## Layered Architecture

* Presentation, Business, Persistance, Database
* Closed layers
    * Isolation - a request moves through each layer
* Service layer - example of an open layer
* Good for general purpose apps
* Sinkhole anti-pattern - passing through layers without processing
* Monolith application - one big unit
* Pros: Testability, Development
* Cons: Agility, Deployment, Performance, Scalability.



## Event-Driven Architecture

* Distributed & asynchronous 

#### Mediator topology

* Event queues
* Event mediator
    * Orchestrate the steps
    * Convert *initial event* to *processing events*
* Event channels
* Event processors
    * Components with business logic
        * Self-contained, independent, decoupled
* Used for more complex event handling

#### Broker topology

* Broker component
    * Contains event channels
* Event processor
    * Components with business logic
    * Each component listens to a specific event, does its process, and sends a new event
* Used for less complex event handling
* Pros: Agility, Deployment, Performance, Scalability
* Cons: Testability, Development



## Microkernel Architecture

* Core system
    * Some general business logic
    * Plug-in registry
* Plug-in modules
    * Specialized  business logic
    * Independent (in most cases)
    * Sometimes used with an adapter
* Examples
    * Operating systems, browsers, apps with plug-ins
* Good for product-based applications
* Pros: Agility, Deployment, Testability, Performance, 
* Cons: Scalability, Development



## Microservices Architecture 

* Separately deployed units (service components) of varying granularity
    * Decoupled
* Challenges
    * Right level of granularity
        * API should preferably not orchestrate server components
        * Service components should preferably not inter-communicate
        * Small utils could be repeated in different service components to avoid coupling

#### API REST-based topology

* Client and service component communicate via REST API
* Good for webapps that expose small individual services

#### REST-based topology

* Client and service component communicate via user interface
* Service components tend to be larger
* Good for medium size business apps

#### Centralized messaging topology

* Client and service component communicate via user interface + lightweight message broker
* Good for larger business apps

* Pros: Agility, Deployment, Testability, Scalability, Development
* Cons: Performance



## Space-Based Architecture

* Processing unit(s)
    * Application components (my be a subset)
    * In memory data grid
    * replication engine
    * optional asynchronous persistent store
* Virtualized middleware
    * Messaging grid
        * Requests -> processing unit
    * Data grid
        * Super fast async data replication between processing units
    * Processing grid (if process units are of different types)
        * Orchestrate request -> multiple process units of different types
    * Deployment manager
        * Dynamic startup/shutdown of process units depending on work load
* Good for webapps with variable work load
* Pros: Agility, Deployment, Scalability
* Cons: Testability, Development