# Projects Deep-Dive

A detailed breakdown of technical projects — architecture decisions, patterns used, and key learnings.

---

## Enterprise Work Projects

### Fleet Management System (FMS)

**Context**: Real-time fleet and equipment monitoring for mining/construction operations across multiple sites.

**Architecture**: Microservices monorepo with 11 independent Go services communicating over gRPC (sync) and Kafka (async).

| Service | Responsibility |
|---|---|
| `auth` | JWT-based authentication, RBAC, multi-tenant access |
| `equipment` | Fleet catalog, equipment specs, lifecycle tracking |
| `project` | Production planning and project management |
| `user` | User management, multi-site profiles |
| `monitoring` | Real-time equipment metrics via InfluxDB |
| `notification` | Multi-channel alert delivery (email, push, Kafka) |
| `notification-scheduler` | Scheduled notification rules via gocron |
| `logs` | Centralized audit logging |
| `dms-device` | Device management, GPS tracking |
| `dms-enercentrik` | Energy/fuel monitoring integration |
| `edd-firebase` | Firebase push notification delivery |

**Key Design Decisions**:
- **MQTT** for IoT device data ingestion (low-latency, lightweight protocol)
- **InfluxDB** for time-series metrics (equipment performance KPIs)
- **Kafka** for async inter-service events (event sourcing patterns)
- **HashiCorp Vault** for secrets management (no secrets in environment files)
- **MinIO** for binary storage (PDF reports, attachments)
- **WebSocket** for real-time dashboard updates
- **PostgreSQL + pgx** for transactional data with connection pooling

---

### Employee Self-Service (ESS)

**Context**: Comprehensive HR platform for employee lifecycle management.

**Architecture**: Clean monorepo, refactored from a distributed multi-repo setup.

**API Surface**: 14+ API collections covering the full HR domain:
- Authentication & session management
- User profiles and data management
- Department and role management
- Roster and scheduling
- Time-off requests, revisions, and settings
- Travel allowance processing
- Medical check-up and plafond management
- Project and configuration management
- System-wide settings

**Refactoring Work**: Led a major refactor from the original `monorepo-ess` to `monorepo-ess-refactored` — restructuring the codebase around domain-driven boundaries, introducing a shared pkg layer, and standardizing Kafka event contracts.

---

### QHSE (Quality, Health, Safety & Environment)

**Context**: Safety and compliance management for industrial operations.

**Services**:
- `assessment-bank-service` — question bank management for safety assessments
- `assessment-bank-service-hse` — HSE-specific assessment questions
- `assessment-service` — assessment execution, scoring, and reporting
- `training-service` — safety training scheduling, attendance, and certification tracking

---

### CONNEX Platform

**Context**: Large-scale IoT connectivity platform with event-driven microservices.

**Highlights**:
- Dual storage strategy: PostgreSQL for relational data, MongoDB for unstructured/high-volume IoT payloads
- OAuth 2.0 implementation for third-party integrations
- Public-facing data APIs separate from internal data services
- Actuator services for device command/control

---

### SSO (Single Sign-On)

**Context**: Centralized identity and access management gateway for all Synapsis platforms.

**Kafka Consumer Architecture**:
- `UserConsumer` — handles user CRUD events, level changes, rehiring, role updates
- `AccessConsumer` — manages app access permissions across LMS, 001M, TCS, MEDIC, SCM
- `LogConsumer` — processes system audit log events
- `LeaveConsumer` — syncs time-off and leave quota events from ESS

This event-driven design ensures SSO stays synchronized with other services without tight coupling.

---

## Open Source Libraries

### goasync — Thread-safe Async Library for Go

**Problem**: Go's goroutines are powerful but lack structured async primitives for awaiting results with cancellation.

**Solution**: A typed, composable async task library.

```go
// Spawn a task
task := goasync.Spawn(func(ctx context.Context) ([]any, error) {
    // ... long-running work
    return []any{result}, nil
})

// Await with context (supports cancellation/timeout)
result, err := task.Await(context.Background())

// Await multiple tasks concurrently
results, err := goasync.TryJoin(ctx, task1, task2, task3)

// Abort a task
task.Abort()
```

**Features**: `Spawn`, `Await`, `Abort`, `TryJoin`, timeout-aware execution, context propagation.

---

### sdk-be — Internal Go Backend SDK

A shared SDK used across all Synapsis backend services, providing standardized implementations for:

| Module | Description |
|---|---|
| `kafkasdk` | Kafka consumer/producer wrappers with retry and DLQ support |
| `grpcsdk` | gRPC client/server with interceptors, health checks |
| `jwt` | JWT generation, validation, and claims management |
| `env` / `getenv` | Environment variable loading with type coercion |
| `grpc` | Shared gRPC utilities |
| `constant` | Shared error codes, response shapes |
| `context` | Request context propagation utilities |
| `dates` | Timezone-aware date utilities |
| `integration` | Third-party integration helpers |

---

### rust-zenoh-boilerplate — Rust + Zenoh Vehicle Sensor Backend

**Purpose**: Production-grade boilerplate for vehicle sensor data management using the Zenoh protocol.

**Architecture**: Clean layered architecture in Rust:
```
Presentation Layer (Axum HTTP)
        ↓
Application Layer (Business Logic)
        ↓
Domain Layer (Entities)
        ↓
Infrastructure Layer (PostgreSQL via SeaORM, Zenoh)
```

**Key Features**:
- **Zenoh pub/sub** for ultra-low-latency sensor data streaming
- **Protobuf** serialization for binary efficiency over Zenoh
- **SeaORM** with async PostgreSQL for persistent storage
- **Heartbeat & reconciliation** mechanisms for network resilience
- Full test suite with unit and integration tests
- Docker Compose setup for local development

---

## Personal Projects

### cv-evaluator — AI-Powered CV Assessment API

**Architecture**: Request → Upload → Async Job Queue → LLM Pipeline → Result Store

**AI Pipeline**:
1. Extract text from PDF/DOCX
2. Generate embeddings (OpenAI) for RAG context retrieval
3. Cosine similarity search against job description embeddings
4. GPT-4 structured evaluation with consistent scoring rubric
5. Circuit breaker wraps all LLM calls — graceful fallback on OpenAI failures

**Resilience Patterns**:
- Circuit breaker (open/half-open/closed states)
- Exponential backoff with jitter on retry
- Async job processing — client polls `/result/{id}`

---

### realtime-doc-collaboration

**Problem**: Demonstrate concurrent, real-time editing with conflict handling — from scratch.

**Design**:
- Each document has a WebSocket hub managing connected clients
- Edits broadcast to all other clients in the hub
- Concurrency handled with Go mutexes on the hub's client map
- Stateless design — horizontal scaling possible with external state store

---

### library-management (Full-stack Next.js)

**Stack**: Next.js 15 App Router · TypeScript · NeonDB (Postgres serverless) · Drizzle ORM · Upstash Redis · Upstash Workflow · Tailwind CSS · Radix UI

**Features**:
- SSR-first with React Server Components
- Rate limiting via Upstash Redis
- Background workflows via Upstash Workflow (email notifications, reminders)
- Admin panel with book catalog management
- Borrow/return tracking with due date enforcement

---

## Engineering Standards & Hiring

As Backend Lead, I designed the technical assessment framework for Backend Engineer candidates:

| Criterion | Weight | What's Evaluated |
|---|---|---|
| API Design | 3 | RESTful conventions, naming, status codes, versioning |
| DB Modeling (ERD) | 3 | Schema, relationships, normalization, indexing |
| Code Structure | 3 | Modularity, separation of concerns, clean architecture |
| System Design | 2 | Service breakdown, data flow, scalability |
| Requirement Analysis | 2 | Scope clarity, understanding, improvement identification |
| Error Handling & Logging | 2 | Structured errors, traceability |
| Security Practices | 2 | Input validation, auth, secret handling |
| Performance Awareness | 2 | Caching, async, DB optimization |
| Docker & Setup | 2 | Reproducibility, env isolation, CI-readiness |
| Testing | 1 | Unit tests, mocking, edge cases |
| README & Docs | 1 | Setup instructions, system overview, rationale |

Reviewed submissions from multiple engineers across both **Middle** and **Senior** Backend tracks.
