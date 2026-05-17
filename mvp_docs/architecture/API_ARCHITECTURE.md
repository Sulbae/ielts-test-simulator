# API_ARCHITECTURE.md

# Purpose

This document defines the API architecture, request lifecycle strategy, and communication boundaries for the AI-powered IELTS CBT Simulator.

The API layer is designed to:
- support modular evaluation pipelines,
- preserve deterministic-first architecture,
- enable scalable async workflows,
- and improve AI-assisted backend development consistency.

This document acts as:
- the API communication contract,
- the orchestration gateway reference,
- and the backend integration alignment document.

---

# API Philosophy

The API architecture follows several core principles.

---

# Thin API Philosophy

API routes should act as:
- controlled gateways,
not:
- business logic containers.

The API layer should:
- validate,
- normalize,
- authorize,
- and orchestrate requests.

Heavy evaluation logic must remain isolated in dedicated services.

---

# Explicit Endpoint Ownership

Each endpoint should:
- own one domain responsibility,
- expose predictable behavior,
- and avoid hidden side effects.

Endpoints should remain:
- modular,
- feature-scoped,
- and composable.

---

# Async-First Processing

Long-running operations should favor:
- asynchronous workflows,
- status-based polling,
- and retry-safe processing.

This is especially important for:
- speaking evaluation,
- AI orchestration,
- and transcription pipelines.

---

# Deterministic-First Orchestration

The API layer should preserve:
- deterministic validation,
- controlled orchestration,
- and rule-governed evaluation flow.

LLM systems should never bypass orchestration boundaries.

---

# High-Level API Architecture

```text
Frontend (PWA)
      ↓
API Layer
      ↓
--------------------------------
| Session APIs                 |
| Evaluation APIs              |
| Audio APIs                   |
| History APIs                 |
| Auth APIs                    |
--------------------------------
      ↓
Evaluation Orchestrator
      ↓
Evaluation Services
```

---

# API Module Structure

The API architecture is organized into modular feature domains.

---

# Session APIs

## Purpose

Manage:
- test session lifecycle,
- timing state,
- and submission orchestration.

---

## Example Responsibilities

### Create Session
### Start Session
### Submit Session
### Finalize Session

---

## Session API Philosophy

Session APIs own:
- workflow lifecycle,
not:
- evaluation logic.

---

# Evaluation APIs

## Purpose

Coordinate:
- evaluation requests,
- orchestration triggers,
- and evaluation retrieval.

---

## Example Responsibilities

### Trigger Writing Evaluation
### Trigger Speaking Evaluation
### Retrieve Evaluation Results
### Retrieve Evaluation Breakdown

---

## Evaluation API Philosophy

Evaluation APIs should:
- initiate orchestrated pipelines,
not:
- perform scoring directly.

---

# Audio APIs

## Purpose

Manage:
- speaking audio uploads,
- storage references,
- and transcription workflows.

---

## Example Responsibilities

### Generate Upload URL
### Finalize Audio Upload
### Start Transcription Pipeline

---

## Audio API Philosophy

Audio APIs should remain:
- async-oriented,
- upload-safe,
- and retry-friendly.

---

# History APIs

## Purpose

Provide:
- user evaluation history,
- session summaries,
- and analytics retrieval.

---

## Example Responsibilities

### Retrieve Past Sessions
### Retrieve Score Trends
### Retrieve Evaluation Metadata

---

## History API Philosophy

History APIs should prioritize:
- efficient reads,
- lightweight responses,
- and pagination readiness.

---

# Authentication APIs

## Purpose

Manage:
- user authentication state,
- token validation,
- and protected route access.

---

## Authentication Philosophy

Authentication systems should remain:
- centralized,
- predictable,
- and lightweight.

---

# Request Lifecycle

All requests should follow a predictable lifecycle.

---

# Standard Request Lifecycle

```text
Client Request
      ↓
Authentication Validation
      ↓
Payload Validation
      ↓
Request Normalization
      ↓
Orchestrator Trigger
      ↓
Service Execution
      ↓
Persistence
      ↓
Response Normalization
      ↓
Client Response
```

---

# Validation Strategy

Validation should occur before orchestration begins.

---

# Validation Responsibilities

The API layer validates:
- payload structure,
- required fields,
- authentication state,
- and request eligibility.

---

# API MUST NOT Validate

The API layer should NOT:
- calculate evaluation scores,
- interpret IELTS quality,
- or apply scoring constraints.

---

# Request Normalization Philosophy

All requests should be normalized into:
- predictable internal formats,
- explicit schemas,
- and stable orchestration payloads.

Normalization reduces:
- orchestration complexity,
- inconsistent service behavior,
- and AI-assisted coding ambiguity.

---

# Async Processing Architecture

Async workflows are preferred for:
- speaking pipelines,
- AI-heavy evaluation,
- and long-running operations.

---

# Async Workflow Pattern

```text
Client Submission
      ↓
Immediate Acknowledgement
      ↓
Background Processing
      ↓
Status Tracking
      ↓
Result Persistence
      ↓
Client Polling / Retrieval
```

---

# Async Status Philosophy

Async systems should expose explicit states.

---

# Example Evaluation States

### initialized
### uploaded
### transcribing
### evaluating
### aggregating
### completed
### failed

---

# Response Normalization

All responses should follow:
- predictable schemas,
- stable naming conventions,
- and frontend-safe structures.

---

# Response Philosophy

Responses should:
- avoid hidden fields,
- avoid unstable structures,
- and remain serialization-safe.

---

# Standard Response Shape

```json
{
  "success": true,
  "data": {},
  "error": null
}
```

---

# Error Handling Philosophy

The system should fail:
- predictably,
- transparently,
- and recoverably.

---

# Error Categories

## Validation Errors
Client-side issues.

---

## Authentication Errors
Unauthorized access attempts.

---

## Processing Errors
Internal evaluation failures.

---

## External Dependency Errors
Gemini API failures, transcription failures, etc.

---

# Error Handling Principles

## Never Lose User Submissions
User work should remain recoverable.

---

## Avoid Silent Failures
Errors should always produce traceable states.

---

## Preserve Retryability
Recoverable operations should support retries.

---

# Authentication Boundaries

Protected APIs should require:
- verified authentication,
- valid session ownership,
- and scoped access control.

---

# Security Philosophy

The API layer must protect:
- evaluation logic,
- secret prompts,
- aggregation systems,
- and sensitive orchestration behavior.

---

# Frontend/API Separation

The frontend should:
- consume normalized APIs,
not:
- directly orchestrate evaluation services.

---

# Evaluation Orchestration Philosophy

All evaluation flows must pass through:
- centralized orchestration,
- controlled sequencing,
- and explicit processing states.

Services should never bypass orchestration layers.

---

# API Scalability Philosophy

The API architecture should support future:
- queue systems,
- streaming evaluation,
- realtime speaking,
- multi-model orchestration,
- and distributed processing.

---

# Scalability Constraints

Avoid:
- giant endpoints,
- mixed responsibilities,
- blocking workflows,
- and frontend-driven orchestration.

---

# AI-Assisted Development Philosophy

The API architecture is intentionally modular to improve:
- isolated endpoint generation,
- predictable AI-generated code,
- and maintainable scaling.

Each endpoint should:
- have explicit ownership,
- explicit input/output contracts,
- and isolated orchestration responsibilities.

---

# Future Expansion Opportunities

Potential future APIs may include:
- adaptive tutoring APIs
- recommendation systems
- realtime conversation APIs
- analytics APIs
- teacher collaboration APIs
- cohort systems

Future systems should preserve:
- orchestration control,
- deterministic-first evaluation,
- and modular boundaries.

---

# Guiding Principle

> "APIs should orchestrate evaluation workflows without becoming the evaluation system itself."

Communication simplicity should never compromise:
- orchestration clarity,
- scalability,
- or evaluation credibility.