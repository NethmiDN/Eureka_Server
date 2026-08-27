# Eureka Server

This project is a Spring Boot application that runs a Netflix Eureka service registry. It is used to register and discover microservices in a distributed system.

## Overview

Eureka Server acts as the central discovery service for your application ecosystem. Other services can register themselves with the server and query it to discover available instances.

This project is configured as a standalone registry and does not register itself with another Eureka instance.

## Technologies

- Java 21
- Spring Boot 3.4.0
- Spring Cloud 2024.0.0
- Netflix Eureka Server
- Maven

## Project Structure

- `src/main/java/com/example/eureka_server/EurekaServerApplication.java` - Spring Boot entry point
- `src/main/resources/application.yml` - Server configuration
- `src/test/java/com/example/eureka_server/EurekaServerApplicationTests.java` - Basic application test

## Configuration

The application listens on port `8761` and exposes the Eureka dashboard at:

- http://localhost:8761

Key settings in `application.yml`:

- `server.port: 8761`
- `eureka.client.register-with-eureka: false`
- `eureka.client.fetch-registry: false`

These settings make this instance a standalone Eureka server instead of a client of another registry.

## Prerequisites

- JDK 21 or later
- Maven 3.9+ (or use the bundled Maven wrapper)

## Run the application

Using Maven Wrapper:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

Or using Maven directly:

```bash
mvn spring-boot:run
```

## Access the Eureka dashboard

Open the following URL in a browser:

```text
http://localhost:8761
```

You will see the Eureka dashboard with registry information and service status.

## Build the project

```bash
./mvnw clean package
```

## Notes

This server is intended to be used as a discovery service for other Spring Boot microservices. Once your client services are configured to point to this Eureka instance, they can register themselves and discover one another automatically.
