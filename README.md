# AspNetMicroservices
An educational project written as part of an online course [Microservices Architecture and Implementation on .NET 5](https://www.udemy.com/course/microservices-architecture-and-implementation-on-dotnet/)

**General diagram of the project:**

![alt text](https://github.com/onter7/AspNetMicroservices/blob/main/diagram.png?raw=true)

## Description

**Catalog microservice:**
- ASP.NET Core Web API application
- REST API principles, CRUD operations
- MongoDB database connection and containerization
- Repository Pattern Implementation
- Swagger Open API implementation

**Basket microservice:**
- ASP.NET Core Web API application
- REST API principles, CRUD operations
- Redis database connection and containerization
- Consume Discount Grpc Service for inter-service sync communication to calculate product final price
- Publish BasketCheckout Queue with using MassTransit and RabbitMQ

**Discount microservice:**
- ASP.NET Grpc Server application
- Build a highly performant inter-service gRPC Communication with Basket Microservice
- Exposing Grpc Services with creating Protobuf messages
- Using Dapper for micro-ORM implementation to simplify data access and ensure high performance
- PostgreSQL database connection and containerization

**Ordering microservice:**
- Implementing DDD, CQRS, and Clean Architecture
- Developing CQRS with using MediatR, FluentValidation and AutoMapper packages
- Consuming RabbitMQ BasketCheckout event queue with using MassTransit-RabbitMQ Configuration
- SqlServer database connection and containerization
- Using Entity Framework Core ORM and auto migrate to SqlServer when application startup

**API Gateway Ocelot microservice:**
- Implement API Gateways with Ocelot
- Sample microservices/containers to reroute through the API Gateways
- The Gateway aggregation pattern in Shopping.Aggregator

**WebUI ShoppingApp microservice:**
- ASP.NET Core Web Application with Bootstrap 4 and Razor template

**Microservices Communication**
- Sync inter-service gRPC Communication
- Async Microservices Communication with RabbitMQ Message-Broker Service
- Using RabbitMQ Publish/Subscribe Topic Exchange Model
- Using MassTransit for abstraction over RabbitMQ Message-Broker system
- Publishing BasketCheckout event queue from Basket microservices and Subscribing this event from Ordering microservices
- Create RabbitMQ EventBus.Messages library and add references Microservices

**Docker Compose establishment with all microservices on docker**
- Containerization of microservices
- Containerization of databases
- Override Environment variables

## Run the Project
Docker is required to run the project

1. Clone the repository
2. At the root directory which include docker-compose.yml files, run below command:
```
docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d
```
3. Wait for docker compose all microservices. That’s it! (some microservices need extra time to work so please wait if not worked in first shut)
4. You can launch microservices as below urls:
- **Catalog API** -> http://host.docker.internal:8000/swagger/index.html
- **Basket API** -> http://host.docker.internal:8001/swagger/index.html
- **Discount API** -> http://host.docker.internal:8002/swagger/index.html
- **Ordering API** -> http://host.docker.internal:8004/swagger/index.html
- **Shopping.Aggregator** -> http://host.docker.internal:8005/swagger/index.html
- **API Gateway** -> http://host.docker.internal:8010/Catalog
- **Rabbit Management Dashboard** -> http://host.docker.internal:15672 -- guest/guest
- **Portainer** -> http://host.docker.internal:9000 -- admin/admin1234
- **pgAdmin PostgreSQL** -> http://host.docker.internal:5050 -- admin@aspnetrun.com/admin1234
- **Web UI** -> http://host.docker.internal:8006
