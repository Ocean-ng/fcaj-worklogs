---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Workshop Report: “GenAI-powered App-DB Modernization Workshop”

### 1. Event Overview & Objectives

* **Date & Time:** 09:00 – 12:30, 23/09/2026
* **Location:** AWS Vietnam Office – Level 26, Bitexco Financial Tower, District 1, Ho Chi Minh City
* **Core Objectives:**
  - Share architectural best practices for modernizing legacy applications and databases on AWS.
  - Introduce **Domain-Driven Design (DDD)** and **Event-Driven Architecture (EDA)** patterns.
  - Provide decision criteria for selecting optimal AWS compute and purpose-built database services.
  - Demonstrate how **Amazon Q Developer** accelerates the secure software development lifecycle (SDLC).

### 2. Speakers

* **Jignesh Shah** — Director, Open Source Databases, AWS
* **Erica Liu** — Sr. GTM Specialist, Application Modernization, AWS
* **Fabrianne Effendi** — Associate Specialist Solutions Architect, Serverless, AWS

### 3. Key Technical Highlights

#### Limitations of Legacy Monolithic Architectures
* Long release cycles and large fault domains where a single component failure impacts the entire system.
* Inefficient resource scaling and higher operational overhead.
* Broad security blast radius due to shared database schemas and overly permissive service credentials.

#### Transitioning to Microservices & Event-Driven Architecture
* Decoupling workloads into independent services communicating asynchronously across three foundational pillars:
  - **Queue Management (Amazon SQS):** Buffering requests and smoothing traffic spikes for downstream consumers.
  - **Event Routing & Pub/Sub (Amazon EventBridge / SNS):** Enabling loose coupling and extensible event fan-out.
  - **Caching Strategy (Amazon ElastiCache):** Reducing database read latency and improving throughput.

#### Domain-Driven Design (DDD) in Practice
* Four-step Event Storming methodology: Identify Domain Events → Arrange chronologically → Map Actors and Commands → Define **Bounded Contexts**.
* Establishes a shared **Ubiquitous Language** between engineering and business stakeholders before implementation.

#### Compute Evolution & Amazon Q Developer
* Tracing the **Shared Responsibility Model** across Amazon EC2 → Amazon ECS → AWS Fargate → **AWS Lambda**.
* Leveraging **Amazon Q Developer** for automated code security scanning, runtime upgrades (Java/.NET modernization), and infrastructure code generation.

### 4. Key Takeaways & Application to My Internship

* **Adopting Event-Driven Serverless Patterns:** Gained clarity on when to adopt **AWS Lambda**, **API Gateway**, and **Amazon EventBridge** for cost-effective scalability—directly informing my **Proposal** architecture and hands-on practice in **Week 7** and **Week 10**.
* **Scoping Security to Bounded Contexts:** Aligning individual IAM Execution Roles with specific microservice boundaries minimizes the blast radius under the Principle of Least Privilege.
* **AI-Assisted Cloud Engineering:** Learned how to utilize AI coding assistants responsibly to validate IAM JSON policies and CloudFormation templates.
