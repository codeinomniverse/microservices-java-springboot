🚀 Microservices E-Commerce Application

A backend-focused E-Commerce Microservices Application built using Java, Spring Boot and Spring Cloud. The application is divided into independent services for better scalability, maintainability and independent deployment.

🏗️ Architecture

                         ┌─────────────────────┐
                         │      Frontend       │
                         │   HTML/CSS/JS       │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    API Gateway      │
                         │      :8080          │
                         └──────────┬──────────┘
                                    │
                 ┌──────────────────┼──────────────────┐
                 │                  │                  │
                 ▼                  ▼                  ▼
        ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
        │ Order Service  │ │Payment Service │ │Inventory       │
        │     :8083      │ │     :8082      │ │Service :8081   │
        └───────┬────────┘ └───────┬────────┘ └───────┬────────┘
                │                  │                  │
                └──────────────────┼──────────────────┘
                                   │
                                   ▼
                         ┌─────────────────────┐
                         │   PostgreSQL /      │
                         │   Neon Database     │
                         └─────────────────────┘
                    ┌─────────────────────┐
                    │   Eureka Server     │
                    │       :8761         │
                    │ Service Discovery   │
                    └─────────────────────┘
                             ▲
                             │
              ┌──────────────┼──────────────┐
              │              │              │
          Order Service  Payment Service  Inventory

🔄 Order Processing Flow

User
 │
 ▼
Frontend
 │
 ▼
API Gateway
 │
 ▼
Order Service
 │
 ├──────────────► Inventory Service
 │                    │
 │                    ▼
 │              Check Stock
 │
 └──────────────► Payment Service
                      │
                      ▼
                Process Payment
                      │
                      ▼
               Order Confirmation

🧩 Microservices

1. Eureka Server — Port 8761

Acts as the Service Discovery Server.

It maintains a registry of all available microservices so that services can discover and communicate with each other without relying on hard-coded service URLs.

2. API Gateway — Port 8080

Acts as the single entry point for the application.

Responsibilities:

* Request routing
* Communication with backend services
* Centralized entry point for frontend requests
* Hides individual service endpoints from the client

Example routes:

/api/orders/**      → Order Service
/api/payments/**    → Payment Service
/api/inventory/**   → Inventory Service

3. Order Service — Port 8083

Responsible for handling customer orders.

Main responsibilities:

* Create orders
* Process order requests
* Communicate with Inventory Service
* Communicate with Payment Service

4. Payment Service — Port 8082

Responsible for payment-related operations.

It handles payment processing and returns the payment status to the order flow.

5. Inventory Service — Port 8081

Responsible for product/inventory-related operations.

Main responsibilities:

* Product information
* Product availability
* Inventory-related operations

🛠️ Tech Stack

Technology	Purpose
Java	Core programming language
Spring Boot	Microservice development
Spring Cloud	Microservices infrastructure
Spring Cloud Eureka	Service Discovery
Spring Cloud Gateway	API Gateway
Spring Data JPA	Database interaction
Hibernate	ORM
PostgreSQL	Relational Database
Neon	Cloud-hosted PostgreSQL
Maven	Dependency Management
Postman	API Testing
HTML/CSS/JavaScript	Frontend

🗄️ Database

The application uses PostgreSQL as the relational database.

The database is hosted using Neon PostgreSQL.

Spring Data JPA and Hibernate are used for communicating with the database.

Spring Boot
     │
     ▼
Spring Data JPA
     │
     ▼
Hibernate
     │
     ▼
PostgreSQL
     │
     ▼
Neon Cloud

🔗 Service Communication

The services communicate through the microservices architecture.

Frontend
   │
   ▼
API Gateway
   │
   ├──► Order Service
   │
   ├──► Payment Service
   │
   └──► Inventory Service
All services
      │
      ▼
Eureka Server
(Service Discovery)

🎯 Why Microservices?

The application uses microservices instead of a single monolithic application because each business functionality can be developed and maintained independently.

Benefits

* Independent service deployment
* Better scalability
* Easier maintenance
* Fault isolation
* Independent development of business modules
* Service discovery through Eureka
* Centralized routing through API Gateway

🧪 API Testing

APIs can be tested using Postman.

Example:

Frontend
   ↓
API Gateway :8080
   ↓
/api/orders/**
/api/payments/**
/api/inventory/**

💡 Key Learning

Through this project, I worked with:

* Microservices architecture
* Spring Boot
* Spring Cloud
* Eureka Service Discovery
* API Gateway
* REST APIs
* PostgreSQL
* JPA/Hibernate
* Inter-service communication
* API testing using Postman

👨‍💻 Project Summary

This project demonstrates how an E-Commerce application can be designed using Spring Boot Microservices, where Order, Payment and Inventory functionalities are separated into independent services.

The API Gateway provides a single entry point for clients, while Eureka Server handles service discovery. PostgreSQL is used for persistent data storage.

📌 Project Structure

microservices-java-springboot
│
├── microServices-backend
│   ├── eureka-server
│   ├── api-gateway
│   ├── order-service
│   ├── payment-service
│   └── inventory-service
│
└── microServices-frontend

⭐ Author

Rahul Kumar

Java | Spring Boot | Microservices | Full Stack Development