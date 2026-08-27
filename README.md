# Eureka Server - Service Registry & Discovery

A foundational platform component built with Spring Cloud Netflix Eureka Server, acting as the dynamic phonebook and service registry for microservices across the enterprise cloud architecture.

---

## Student & Project Information

| Field | Details |
| :--- | :--- |
| Student Name | Nethmi Nanayakkara |
| Student ID | 241722047 |
| GCP Project ID | `nethmi-project` |
| Module | ITS 2130 - Enterprise Cloud Architecture |
| Component Role | Dynamic Service Registry & Discovery |

---

## Overview & Architecture

Eureka Server removes the need to hardcode hostnames, IP addresses, and ports between microservices. When backend services such as User Service, Event Service, Media Service, and API Gateway start up, they register themselves with Eureka and send periodic heartbeats so the registry can keep track of healthy instances.

### Key Cloud & Platform Capabilities

- Dynamic service registration for new and autoscaled instances launched in Google Compute Engine Managed Instance Groups.
- Client-side load balancing integration using logical service IDs such as `lb://SERVICE-NAME`.
- Heartbeat and self-preservation support to monitor node health and evict unresponsive instances.
- Web dashboard for viewing active service instances, hostnames, and UP status in real time.

---

## Technology Stack

- Java 21
- Spring Boot 3.4.0
- Spring Cloud Netflix Eureka Server
- Maven

---

## Registry & Diagnostic Endpoints

| Method | Endpoint | Description | Response |
| :--- | :--- | :--- | :--- |
| GET | `/` | Eureka Web Management Dashboard | `200 OK` (HTML web interface) |
| GET | `/eureka/apps` | Fetch all registered instances | `200 OK` (XML / JSON application registry tree) |
| GET | `/eureka/apps/{appID}` | Fetch specific service instance details | `200 OK` (instance metadata) |
| GET | `/actuator/health` | Service health status check | `{"status":"UP"}` |

---

## Local Setup & Development

### Prerequisites

- JDK 21+
- Apache Maven 3.8+

### Clone the Repository

```bash
git clone https://github.com/NethmiDN/Eureka_Server.git
cd Eureka_Server
```

### Run the Application

Using Maven Wrapper on macOS/Linux:

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

### Build the Project

```bash
./mvnw clean package
```

On Windows:

```bash
mvnw.cmd clean package
```

### Access the Eureka Dashboard

Open the dashboard in a browser:

```text
http://localhost:8761
```

The dashboard shows registered services, instance metadata, and runtime status.

---

## Configuration Notes

The application is configured to run as a standalone Eureka server on port `8761`.

Key settings in [application.yml](src/main/resources/application.yml):

- `server.port: 8761`
- `spring.application.name: eureka-server`
- `eureka.client.register-with-eureka: false`
- `eureka.client.fetch-registry: false`
- `eureka.instance.hostname: localhost`

These settings ensure the server does not register itself as a Eureka client and instead acts as the central registry for other microservices.

---

## Project Structure

- [src/main/java/com/example/eureka_server/EurekaServerApplication.java](src/main/java/com/example/eureka_server/EurekaServerApplication.java) - Spring Boot entry point
- [src/main/resources/application.yml](src/main/resources/application.yml) - Eureka server configuration
- [src/test/java/com/example/eureka_server/EurekaServerApplicationTests.java](src/test/java/com/example/eureka_server/EurekaServerApplicationTests.java) - Basic application test

---

## Purpose

This service is intended to support Spring Boot microservices in an enterprise cloud environment by providing dynamic discovery, resilience, and centralized visibility into registered services.
