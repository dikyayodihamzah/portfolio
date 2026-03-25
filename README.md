<div align="center">

# Diky Afamby Yodihamzah

### Backend Lead · Software Engineer

[![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)](https://go.dev)
[![Rust](https://img.shields.io/badge/Rust-000000?style=flat&logo=rust&logoColor=white)](https://www.rust-lang.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![GitHub followers](https://img.shields.io/github/followers/dikyayodihamzah?style=flat&logo=github&label=Follow)](https://github.com/dikyayodihamzah)

> Building high-performance, distributed systems that scale.

</div>

---

## About Me

I'm a **Backend Lead** with deep expertise in distributed systems, microservices architecture, and high-throughput data pipelines. I specialize in Go, and I've led the architecture and delivery of enterprise-grade platforms — from real-time fleet monitoring across mining sites to AI-powered evaluation systems.

Beyond shipping production systems, I design and review technical challenge tests for Backend Engineers (Mid–Senior level), covering API design, system architecture, security, performance, and clean code practices.

- Based in **Indonesia**
- Currently at **Synapsis** — building enterprise Superapps
- Passionate about **clean architecture**, **event-driven systems**, and **developer tooling**

---

## Tech Stack

**Languages**

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat&logo=go&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000000?style=flat&logo=rust&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)

**Frameworks & Libraries**

![Fiber](https://img.shields.io/badge/Fiber-00ACD7?style=flat&logo=go&logoColor=white)
![Axum](https://img.shields.io/badge/Axum-000000?style=flat&logo=rust&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white)
![gRPC](https://img.shields.io/badge/gRPC-244C5A?style=flat&logo=grpc&logoColor=white)

**Messaging & Streaming**

![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=flat&logo=apachekafka&logoColor=white)
![MQTT](https://img.shields.io/badge/MQTT-660066?style=flat&logo=mqtt&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=flat&logo=socket.io&logoColor=white)

**Databases**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![InfluxDB](https://img.shields.io/badge/InfluxDB-22ADF6?style=flat&logo=influxdb&logoColor=white)

**Infrastructure & DevOps**

![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![HashiCorp Vault](https://img.shields.io/badge/Vault-FFEC6E?style=flat&logo=vault&logoColor=black)
![MinIO](https://img.shields.io/badge/MinIO-C72E49?style=flat&logo=minio&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat&logo=firebase&logoColor=black)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat&logo=prometheus&logoColor=white)

---

## Work Experience

### Backend Engineer Lead — Synapsis *(2023 – Present)*

Leading backend architecture across multiple enterprise product lines. Responsible for system design decisions, code quality standards, cross-team technical alignment, and mentoring engineers across mid-to-senior levels.

#### Products & Platforms Built

**Fleet Management System (FMS)** — Mining & Construction Fleet Ops

A comprehensive microservices platform for real-time fleet monitoring across mining and construction sites. Serves Fleet Operations, Production, Equipment Maintenance, and Site Management teams.

- **11 microservices**: auth, equipment, project, user, monitoring, notification, DMS, logs, scheduling, and more
- **Tech**: Go · Fiber · PostgreSQL · Redis · InfluxDB · Kafka · MQTT · gRPC · Firebase · HashiCorp Vault · MinIO · WebSocket · Docker
- **Highlights**: Real-time GPS/IoT data ingestion via MQTT; time-series performance metrics via InfluxDB; event-driven notifications via Kafka; PDF report generation; multi-site, multi-tenant architecture



**Employee Self-Service (ESS)** — HR Platform

A full-featured HR platform exposing rich APIs for workforce management.

- **Modules**: Auth · User Management · Department · Roles · Roster · Time-off · Travel Allowance · Medical Check-up · Medical Plafond · Project Configuration · System Settings
- **Tech**: Go · Kafka · PostgreSQL · Redis · gRPC · Protobuf · Docker
- **Highlights**: Refactored to a clean monorepo architecture; event-driven inter-service communication via Kafka; SSO integration



**QHSE (Quality, Health, Safety & Environment)**

Safety management platform for industrial and enterprise environments.

- **Services**: Assessment Bank · HSE Assessment · Assessment Execution · Training Management · DB Migrations
- **Tech**: Go · PostgreSQL · Redis · Kafka · Docker



**CONNEX** — IoT Connectivity Platform

A large-scale IoT and connectivity platform with event-driven architecture.

- **20+ services**: Auth · OAuth · Permissions · Profiles · Projects · Groups · Nodes · Dashboard · Data (MongoDB + PostgreSQL) · Notifications · Field Service · Historical Data · Actuators
- **Tech**: Go · Fiber · PostgreSQL · MongoDB · Kafka · Event-driven · Docker



**SSO (Single Sign-On)**

Centralized authentication and access control gateway for all Synapsis Superapps.

- Handles user creation, role updates, app access permissions, and event-driven sync via Kafka consumers
- **Tech**: Go · Kafka · PostgreSQL · Redis · JWT · gRPC



**001M Superapps**

Multi-module enterprise Superapps platform.

- **Services**: Job Management · Safety Form · Shipment Tracking
- **Tech**: Go · PostgreSQL · Kafka · Docker



**NEARON** — Next-Generation IoT Connectivity Platform

The successor to CONNEX, rebuilt from the ground up with a significantly improved monorepo architecture and cleaner engineering foundations.

- **15 services**: Auth · User · Project & Node Management · Monitoring · Notification · Scheduler · System Settings · Logs · MQTT Auth · Audio · FFmpeg · Tuya · License Management · Legacies
- **Tech**: Go · Fiber · PostgreSQL · MongoDB · Redis · Kafka · MQTT · gRPC · Firebase · HashiCorp Vault · MinIO · Prometheus · Uber Zap · Docker
- **Improved over CONNEX**: Structured shared `pkg` layer (cache, config, exception, grpc, helper, middleware, model, query, transaction, utils); circuit breaker (gobreaker); Prometheus metrics; structured logging with Uber Zap; Telegram bot notifications; Tuya smart device integration; MQTT auth service; comprehensive mock-based test suite

**License Management System** — Licensing for CONNEX & NEARON

Standalone service managing software licenses across the CONNEX and NEARON platforms.

- Controls license issuance, validation, and lifecycle for platform deployments
- **Tech**: Go · Fiber · MongoDB · Kafka · JWT · Docker



#### Internal Libraries & Tooling


| Library                    | Description                                                                                          | Tech                                    |
| -------------------------- | ---------------------------------------------------------------------------------------------------- | --------------------------------------- |
| **sdk-be**                 | Internal backend SDK — Kafka consumer/producer, gRPC client/server, JWT, HashiCorp Vault, env config | Go                                      |
| **rust-zenoh-boilerplate** | Production-grade Rust backend boilerplate with Zenoh pub/sub for vehicle sensor data                 | Rust · Axum · SeaORM · Zenoh · Protobuf |
| **environment-vault**      | Secrets management tooling integrated with HashiCorp Vault                                           | Go                                      |


#### Technical Leadership

- Designed and maintained **assessment criteria** for Backend Engineer hiring (Mid & Senior levels)
- Reviewed and scored candidates across: API Design · System Design · Code Structure · ERD/DB Modeling · Security · Performance · Docker · Testing · Documentation
- Conducted technical benchmarking via **load testing** and **Kafka consumer integration testing**
- Established internal **engineering standards** and architectural documentation

---

## Open Source & Personal Projects

### [cv-evaluator](https://github.com/dikyayodihamzah/cv-evaluator) · Go · ⭐ 2

> AI-powered CV evaluation API using LLM chaining and RAG.

- Accepts CV files in TXT, PDF, DOCX formats
- Uses **OpenAI GPT-4** for structured candidate assessment and embeddings
- Implements **RAG** with real vector embeddings and cosine similarity
- **Circuit breaker** pattern, exponential backoff retry, graceful degradation
- Async job processing with status tracking
- Storage via **MinIO**; PDF/DOCX extraction pipeline
- **Tech**: Go · Fiber · OpenAI · MinIO · RAG · Circuit Breaker · Docker

---

### [realtime-doc-collaboration](https://github.com/dikyayodihamzah/realtime-doc-collaboration) · Go

> Real-time collaborative document editing backend — think Google Docs, built from scratch.

- Multi-user concurrent editing via **WebSockets**
- Conflict handling and real-time synchronization
- Lightweight and containerized
- **Tech**: Go · gorilla/websocket · Docker

---

### [library-management-system-api](https://github.com/dikyayodihamzah/library-management-system-api) · Go

> Clean RESTful API for university library management.

- Full CRUD for books, users, and borrowing records
- Clean architecture with proper layering
- **Tech**: Go · PostgreSQL · Docker

---

### [library-management](https://github.com/dikyayodihamzah/library-management) · TypeScript

> Full-stack university library management system with admin panel.

- Server-side rendering with **Next.js 15**
- Auth, book catalog, borrow workflows, rate limiting
- **Tech**: Next.js · TypeScript · PostgreSQL (NeonDB) · Drizzle ORM · Upstash Redis · Upstash Workflow · Tailwind CSS · Radix UI

---

### [bookings](https://github.com/dikyayodihamzah/bookings) · Go

> Full-stack web app for hotel/property bookings — Go HTML templates and server-side rendering.

- Session management, CSRF protection
- **Tech**: Go 1.20 · chi router · SCS sessions · nosurf

---

### [whatsapp-blast](https://github.com/dikyayodihamzah/whatsapp-blast) · Go

> WhatsApp bulk messaging tool for notification delivery.

---

### [Load-Test](https://github.com/dikyayodihamzah/Load-Test) · JavaScript

> Load testing scripts and configurations for API performance benchmarking.

---

### [relawan-map](https://github.com/dikyayodihamzah/relawan-map) · TypeScript

> Interactive map application for volunteer/activist network visualization.

---

### [connex-bot](https://github.com/dikyayodihamzah/connex-bot) · Go

> Automation bot for the CONNEX IoT platform.

---

## Architecture Principles

Things I care deeply about when building systems:

- **Clean Architecture** — separating domain, application, infrastructure, and presentation layers
- **Event-Driven Design** — decoupled services communicating via Kafka or message queues
- **Observability** — structured logging, tracing, and metrics from day one
- **Security by Default** — secrets in Vault, input validation, secure headers, least-privilege access
- **Performance Awareness** — indexed queries, async processing, caching strategies, load testing before shipping
- **Developer Experience** — clean READMEs, reproducible Docker setups, consistent API conventions

---

## Contact

- **GitHub**: [github.com/dikyayodihamzah](https://github.com/dikyayodihamzah)
- **Email**: [dikyayodihamzah@gmail.com](mailto:dikyayodihamzah@gmail.com)

---



*"Build things that last. Document things that matter. Ship things that work."*

