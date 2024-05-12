# Playing Cards Game

> Playing Cards Game: This application simulates a card game between two computer players.

---


<details>
  <summary><strong>Table of Contents</strong></summary>

- [Playing Cards Game](#playing-cards-game)
  - [Overview](#overview)
    - [Requirements](#requirements)
  - [Technologies](#technologies)
  - [Architecture](#architecture)
      - [Domain Layer](#domain-layer)
      - [Application Layer](#application-layer)
      - [Infrastructure Layer](#infrastructure-layer)
      - [Api Layer](#api-layer)
  - [Usage](#usage)
    - [Unit Testing](#unit-testing)
  - [Roadmap](#roadmap)

</details>

---


## Overview

This application simulates a card game between two computer players, with the potential to be adapted for human player participation in the future.

For now, no user interface is required, so the host/user interface will be a Console application type. In the future, this can be replaced by an API project.


### Requirements

To be updated!



## Technologies

- .NET 8
- C#



## Architecture

Given the application's requirements and scope, a monolithic architecture is more suitable than a microservices-based architecture.

This application is built on Clean Architecture, prioritizing a loosely coupled implementation of use cases. Use cases serve as the central organizing structure, independent of frameworks and technology specifics.

There are four logical layers of the architecture: 

#### Domain Layer

The Domain Layer implements the core, use-case independent business logic of the domain or system. It primarily consists of domain entities and should remain independent of external libraries and frameworks. The Domain project serves as the core and backbone project, with all other projects depending on it.

Domain layer contains:

- Entities
- Enums
- Constants
- Value Objects
- Domain Events

Note: Entities are for future implementation only to store Match and Players details in database. Created `Match` and `Player` entity for reference only.

#### Application Layer

The Application Layer implements the use cases of the application, based on the domain. A use case represents a user interaction on the User Interface (UI). This layer houses all application logic, including the application Use Cases which orchestrate the high-level business rules. It is dependent on the domain layer but has no dependencies on any other layer or project. This layer defines interfaces that are implemented by external layers. The package exposes Boundary Interfaces (also known as Contracts, Ports, or Interfaces), which are utilized by the User Interface.

Application layer contains:

- Abstractions/Contracts/Interfaces
- Models (DTOs)
- Application Services/Handlers
- Commands and Queries
- Exceptions
- Mappers
- Validators

Note: Currently, most of the functionalities are not yet implemented. However, these components will become essential in real-life scenarios when data needs to be retrieved from and stored in a database.

#### Infrastructure Layer

The Infrastructure Layer is responsible for implementing the Contracts (Interfaces/Adapters) defined within the Application Layer and supports other layers by implementing abstractions and integrations to 3rd-party libraries and systems. It houses most of the application’s dependencies on external resources, such as file systems, web services, third-party APIs, and so on.

Infrastructure layer contains:

- Identity Services
- File/Queue/Message Services
- Third-party Services

**Persistence Layer**

This layer part of Infrastructure layer that handles database concerns and other data access operations. It contains implementations of the interfaces (e.g. Repositories) that defined in the Application project.

Note: Currently, most of the functionalities are not yet implemented. However, these components will become essential in real-life scenarios when data needs to be retrieved from and stored in a database.

#### Api Layer

API Layer manages the presentation concerns. It is responsible for rendering JSON data to UI apps and serves as the application entry point. While it depends on both the Application and Infrastructure layers, its dependency on Infrastructure is primarily to support dependency injection. This layer receives HTTP Requests from users, and Presenters convert the application outputs into ViewModels that are rendered as HTTP Responses.

User Interface layer contains:

- Controllers
- View Models
- Middlewares
- Filters/Attributes
- Utilities


Note: In this application, no user interface is required, so the host/user interface will be a Console application type. This project serves as the entry point of the application and is used to execute the application.



## Usage

- Clone the repository.

```sh
git clone https://github.com/b-patel/PlayingCardsGame.git
```


**How to run**

- Open solution in Visual Studio.
- Set `PlayingCardsGame.Host` as a startup project to run the application.



### Unit Testing

Library used

- xUnit
- NSubstitute


- Run `PlayingCardsGame.Test`




## Roadmap

- Human Player based (instead of computer players).
- Save Players' Details in Database.
- Save Played Games in Database.
- History of Games and Players.
- API Driven.
- Make Event-Driven and Domain-Driven (e.g. Publish events on Game completion).
- Add ORM, Dependency Injection/IoC, validations, logging, etc. 
- Use third-party libraries such as EF Core, MediatR, FluentValidation, Serilog, Swashbuckle, etc.
- Add Additional test cases.
