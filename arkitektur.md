# Arkitektur

en grov nivå av text som sammanfattar arkitekturen för vårt system

## Presentatation layer
* Admin web
* Customer web
* Customer app

## Device layer
* Scooters

## Communication layer
* REST API
* Socket

## Business layer
* Modules...

## Persistance layer
* Modules
* Cache

## Database layer
* Database


## Brainstorm
* Layers and the contents of the layers
* Communication between layers
* The layered pattern
* Microservices pattern - what we wanted at first, and why we landed in a mix betwen layered and micro
* 

The *Spark* system is designed with a layered architecture [1] as the main source of inspiration, with some influence from microservices pattern [1]. The idea is to separate the system in different layers, where each layer represents a role. This creates a well defined separation of concerns for the different modules of each layer, and the requests flows through the layers in a predictable manner.

The *presentation layer* consists of three clients that customers, admin and service team can use to interact with the system. Conceptually this is were the system is presented to its audience. The scooters are placed in a separate *device layer*, and has a role that is similar to the clients, but lacks the presentation aspect. The *communication layer* represents the hub where the clients communicate with the server. A *REST API* is used to handle the majority of request types, and *WebSocket* is used to handle realtime updates of individual scooters. *Business logic* is separated in a bunch of different *models*, that handles all kinds of orchestration and calculations, and represent the *business layer*. Models that handles temporary caching or persistance to a database goes into the *persistance layer*. Finally the *database layer* is where all data is actually persisted in a database.

Initially we were planning to use the *microservices architecture*, where the whole system would be devided into small isolated pieces. Later we decided to lean more toward a layered architecture for the core of the system, by letting the server be unified, while keeping clients and database isolated. The reason to unify the server, rather than deviding it into small service components, was that it seemed unnecessary complex for our use case. It seemed more appealing to let the REST API have direct access to all the business models.



## REF

[2] https://www.oreilly.com/content/how-to-design-a-restful-api-architecture-from-a-human-language-spec/ - 2025-11-18