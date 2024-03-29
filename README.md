# Software Architecture <!-- omit in toc -->

## Contents <!-- omit in toc -->

- [1. Evolution of Software Architectures](#1-evolution-of-software-architectures)
  - [1.1. Monolithic to Serverless](#11-monolithic-to-serverless)
  - [1.2. Architecture Design Vertical Considerations](#12-architecture-design-vertical-considerations)
- [2. Way to Design Software Architecture](#2-way-to-design-software-architecture)
- [3. Common Software Architecture Design Problems](#3-common-software-architecture-design-problems)
  - [3.1. Increased Traffic, Handle More Request](#31-increased-traffic-handle-more-request)
  - [3.2. Break Down Application into Microservices](#32-break-down-application-into-microservices)
  - [3.3. Direct Client-to-Service Communication](#33-direct-client-to-service-communication)
  - [3.4. Inter-service communication makes](#34-inter-service-communication-makes)
  - [3.5. Chat with Support Agent](#35-chat-with-support-agent)
  - [3.6. Service-to-Service Communications Chain Queries](#36-service-to-service-communications-chain-queries)
  - [3.7. Long Running Operations Can't Handle with Sync Communication](#37-long-running-operations-cant-handle-with-sync-communication)
  - [3.8. Database Bottlenecks when Scaling, Different Data Requirements For Microservices](#38-database-bottlenecks-when-scaling-different-data-requirements-for-microservices)
  - [3.9. Cross-Service Queries and Write Commands on Distributed Scaled Databases](#39-cross-service-queries-and-write-commands-on-distributed-scaled-databases)
  - [3.10. Manage Consistency Across Microservices in Distributed Transactions](#310-manage-consistency-across-microservices-in-distributed-transactions)
  - [3.11. Handle Millions of Events Across Microservices](#311-handle-millions-of-events-across-microservices)
  - [3.12. Database operations are expensive, low performance](#312-database-operations-are-expensive-low-performance)
  - [3.13. Deploy Microservices at Anytime with Zero-downtime and flexible scale](#313-deploy-microservices-at-anytime-with-zero-downtime-and-flexible-scale)
- [4. Choosing the Right Architecture for your Application](#4-choosing-the-right-architecture-for-your-application)
  - [4.1. Design for Business Requirements](#41-design-for-business-requirements)
  - [4.2. -Ilities](#42--ilities)

# 1. Evolution of Software Architectures

- Over the years, software development moved away from traditional **monolithic** architectures because of the complexities with tight coupled and interconnected code.
  - As a result, **microservices** are adopted many projects with using cloud native approaches that enable distributed computing through multiple smaller services.

![Evolution of Software Architectures](/Images/EvolutionArchitectures.png)

## 1.1. Monolithic to Serverless

![Monolithic to ToServerless](/Images/MonolithicToServerless.png)

## 1.2. Architecture Design Vertical Considerations

![Architecture Design Vertical Considerations](Images/ArchitectureDesignVerticalConsiderations.png)

# 2. Way to Design Software Architecture

![Way to Design Software Architecture](/Images/WayDesignSoftwareArchitecture.png)

# 3. Common Software Architecture Design Problems

## 3.1. Increased Traffic, Handle More Request

- **Problems**
  - Our E-Commerce Business is growing.
  - Need to handle greater amount of request per second.
  - Provide acceptable latency for users.
- **Solutions**
  - Scalabilitiy.
  - Vertical and Horizontal Scaling.
  - Scale Up and Scale Out.
  - Load Balancer.

## 3.2. Break Down Application into Microservices

- **Problems**
  - Our E-Commerce Business is growing.
  - Teams wants to agile and add new features immediately to compete the market.
  - Required Independent Scale and Deployments.
  - We should clearly identify microservices which parts could be independent scale and deploy.
- **Solutions**
  - Microservices Decomposition Patterns.

## 3.3. Direct Client-to-Service Communication

- **Problems**
  - Direct Client-to-Service Communication.
  - Cause to chatty calls from client to service.
  - Hard to manage invocations from client app.
- **Solutions**
  - Well-defined API Design.
  - Microservices Communication Patterns.

## 3.4. Inter-service communication makes

- **Problems**
  - Network performance issues on inter-service communication.
  - Backend Communication performance requirements.
  - Real-time communication requirements.
  - Streaming requirements.
- **Example Use Case**
  - Add Item into Shopping Cart that need to calculate with up-to-date discounts.
- **Solutions**
  - gRPCAPIs scalable and fast APIs.
  - Able to develop with different technologies with RPC framework.

## 3.5. Chat with Support Agent

- **Problems**
  - Business teams request to answer Customer queries by chatting with Support Agents.
  - Real-time communication requirements.
  - Sending/receiving messages in Chat window.
- **Example Use Case**
  - E-commerce Online Agent help customer preferences as per product features on website.
- **Solutions**
  - WebSocket APIs: Build real-time two-way communication applications.

## 3.6. Service-to-Service Communications Chain Queries

- **Problems**
  - HTTP calls to multiple microservices.
  - Chain Queries.
  - Visit more than a few microservices.
  - Increased latency.
- **Solutions**
  - Aggregate query operations.
  - Service Aggregator Pattern.

## 3.7. Long Running Operations Can't Handle with Sync Communication

- **Problems**
  - HTTP calls to multiple microservices.
  - Chain Queries.
  - Visit more than a few microservices.
  - Increased latency with Highly Coupling Services.
  - Performance, scalability, and availability problems.
- **Best Practices**
  - Minimize the communication between the internal microservices.
  - Make microservices communication in Asynchronous way as soon as possible.
- **Solutions**
  - Asynchronous Message-Based Communications.
  - Working with events.

## 3.8. Database Bottlenecks when Scaling, Different Data Requirements For Microservices

- **Problems**
  - Database are stateful service.
  - Scaling stateful services are not easy.
  - Vertical scaling has limits need to scale Horizontally.
  - Different Data Requirements For Microservices.
- **Solutions**
  - Scale Stateful Application Horizontal Scaling.
  - Service and Data Partitioning along Business Boundaries - Shards/Pods.
  - Use NoSQL Database to gain partitioning.
  - Identify Database Requirements following best practices.
- **Question**
  - How to Choose a Database for Microservices?

## 3.9. Cross-Service Queries and Write Commands on Distributed Scaled Databases

- **Considerations**
  - Cross-services queries that retrieve data from several microservices?
  - Separate read and write operations at scale?
- **Problems**
  - Cross-Service Queries with Complex JOIN operations.
  - Read and write operations at scale.
  - Distributed Transaction Management.
- **Solutions**
  - Microservices Data Query Pattern and Best Practices.
  - Materialized View Pattern.
  - CQRS Design Pattern.
  - Event Sourcing Pattern.

## 3.10. Manage Consistency Across Microservices in Distributed Transactions

- **Considerations**
  - Distributed Transactions that required to visit several microservices ?
  - Consistency across multiple microservices ?
  - Rollback transaction and run compensating steps ?
- **Problems**
  - Distributed Transaction Management
  - Rollback Transaction on Distributed Environment
  - Run Compensate Steps if one of service fail
- **Solutions**
  - Microservices Distributed Transaction Management Pattern and Best Practices
  - Saga Pattern for Distributed Transactions
  - Transactional Outbox Pattern
  - Compensating Transaction pattern
  - CDC - Change Data Capture

## 3.11. Handle Millions of Events Across Microservices

- **Considerations**
  - What if we have thousands of microservices that need to communicates with millions of events?
  - If multiple subsystems must process the same events.
  - Required Real-time processing with minimum latency.
  - Required complex event processing, like pattern matching.
  - Required process high volume and high velocity of data, i.e. IoT apps.
- **Problems**
  - Decoupled communications for thousands of microservices.
  - Real-time processing.
  - Handle High volume events.
- **Solutions**
  - Event-driven architecture for microservices.

## 3.12. Database operations are expensive, low performance

- **Considerations**
  - Event-driven architecture comes with latency when publishing and subscribing events from the Event Hub.
  - Sync REST APIs communication make expensive calls to a database that reduce performance.
  - How can we make more faster that increase performance of communications in Microservices Architecture?
- **Problems**
  - Slowliness and Low Performance Communication.
  - Latency when publishing and subscribing events.
  - Rest APIs make Database calls that are expensive, low performance.
- **Solutions**
  - Distributed cache.
  - Storing frequently accessed data in a distributed cache.

## 3.13. Deploy Microservices at Anytime with Zero-downtime and flexible scale

- **Problems**
  - Business teams wants to add new features immediately.
  - Innovate and experiment with new features.
  - Deploy features immediately, not waiting for deployment dates.
  - Flexible scale for market peek times.
- **Considerations**
  - Ensure continuity of service and minimize disruption.
  - Allow for continuous delivery.
  - Support high-traffic environments.
- **Solutions**
  - Containers and Orchestrators.
  - Deployment strategies; blue-green deployment, rolling.
    deployment, and canary deployment.
  - Kubernetes Patterns; Sidecar Patterns, Service Mesh Pattern.
  - DevOps and CI/CD Pipelines and Infrastructure as code (IaC).

# 4. Choosing the Right Architecture for your Application

- Every Architecture has Pros and Cons
  - Understand that **every architecture** has **benefits** and also **drawbacks**.
  - Consider every architecture style as a SA (Software Architecture).
  - What is the Right Architecture for your Application?
    - **It Depends..**
- Monolithic Architecture and Microservice Architecture are **architectural patterns**.
- No architecture pattern **is better than other**.
- Design your system with focusing on **context** and **non-functional requirements** (-ilities)
- **WRONG:** Microservices > Monolithic

## 4.1. Design for Business Requirements

- Every **design decision** must be **justified** by a **business requirement**.
- **To avoid over-engineering** the application architectures, keep to drive design for business requirement.
- Engineers are **tend to be over-engineering** with latest architecture styles, use latest tools.
- It **becomes** an **experimental application** that use all latest fancy tools and architectures.
- We should clearly **define functional** and **nonfunctional** requirements.
- **Define** our **limits**, **constraints** and **assumptions** of the application and define business objectives clearly.
- **Start** and **Grow Application** with **Metrics**
  - How many Concurrent Users that our application handle ?
  - What is the target of expected Requests/second Latency ?
  - What level of application outage is acceptable?
- **Business requirements drive** these **design considerations**.

## 4.2. -Ilities

- Scalability
- Availability
- Reliability
- Maintainability
- Usability
- Eficiency
- Security
- Flexibility
- Performance
