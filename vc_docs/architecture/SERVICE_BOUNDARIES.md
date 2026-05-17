# SERVICE_BOUNDARIES.md

# Purpose

This document defines explicit ownership boundaries and responsibility separation across all major services within the AI-powered IELTS CBT Simulator.

The primary goals are to:
- prevent architecture drift,
- avoid duplicated business logic,
- preserve modular scalability,
- improve AI-assisted development consistency,
- and maintain deterministic-first evaluation architecture.

This document acts as:
- a service ownership contract,
- a backend responsibility map,
- and a modularity enforcement framework.

---

# Architectural Philosophy

The platform follows several service boundary principles:

## Single Responsibility Principle

Each service should own:
- one clear responsibility,
- one logical domain,
- and one primary processing concern.

Services should avoid overlapping responsibilities.

---

## Deterministic-First Architecture

Deterministic systems should control:
- validation,
- metrics,
- constraints,
- and final score aggregation.

LLM services should assist interpretation but should not control the evaluation pipeline.

---

## Orchestrated Processing

All evaluation flows must pass through:
- centralized orchestration,
- controlled sequencing,
- and explicit pipeline management.

Services should not independently coordinate evaluation logic.

---

## Explicit Boundaries

Every service must clearly define:
- owned responsibilities,
- forbidden responsibilities,
- accepted inputs,
- and expected outputs.

---

# High-Level Service Hierarchy

```text
Frontend Application
        ↓
API Layer
        ↓
Evaluation Orchestrator
        ↓
-------------------------------------
| Metrics Engine                    |
| Rule Engine                       |
| Gemini Evaluation Service         |
| Aggregation Engine                |
| Persistence Services              |
-------------------------------------
```

---

# Frontend Application

## Responsibilities

The frontend owns:
- UI rendering,
- user interactions,
- timers,
- navigation,
- loading states,
- session UX,
- and result visualization.

---

## Frontend MAY:
- validate simple UI constraints,
- manage temporary local state,
- render evaluation outputs,
- and handle optimistic UI states.

---

## Frontend MUST NOT:
- calculate IELTS scores,
- apply evaluation rules,
- run aggregation logic,
- store secret prompts,
- or independently evaluate submissions.

---

## Frontend Philosophy

The frontend should remain:
- lightweight,
- predictable,
- and presentation-focused.

Business logic must remain server-side.

---

# API Layer

## Responsibilities

The API layer owns:
- request validation,
- authentication enforcement,
- routing,
- response normalization,
- and orchestration entry points.

---

## API Layer MAY:
- validate payload structures,
- normalize request formats,
- and manage access control.

---

## API Layer MUST NOT:
- implement scoring logic,
- calculate evaluation metrics,
- or perform aggregation logic.

---

## API Philosophy

API routes should act as:
- controlled gateways,
not:
- business logic containers.

---

# Evaluation Orchestrator

## Responsibilities

The Evaluation Orchestrator owns:
- pipeline sequencing,
- evaluation coordination,
- service execution order,
- retry logic,
- and evaluation lifecycle management.

---

## Orchestrator MAY:
- coordinate services,
- enforce execution order,
- manage evaluation states,
- and trigger persistence operations.

---

## Orchestrator MUST NOT:
- directly implement metrics logic,
- directly implement aggregation rules,
- or directly perform qualitative evaluation.

---

## Orchestrator Philosophy

The orchestrator acts as:
- a workflow controller,
not:
- a scoring engine.

---

# Metrics Engine

## Responsibilities

The Metrics Engine owns deterministic linguistic analysis.

---

# Writing Metrics Ownership

## Examples
- word count
- lexical diversity
- repetition analysis
- sentence complexity
- grammar density
- paragraph structure

---

# Speaking Metrics Ownership

## Examples
- speaking duration
- words per minute
- filler detection
- pause estimation
- repetition analysis

---

## Metrics Engine MAY:
- generate measurable linguistic indicators,
- provide structured analysis summaries,
- and expose reusable evaluation metrics.

---

## Metrics Engine MUST NOT:
- determine final IELTS bands,
- apply scoring constraints,
- or independently interpret writing quality.

---

## Metrics Philosophy

Metrics should remain:
- deterministic,
- reproducible,
- and explainable.

---

# Rule Engine

## Responsibilities

The Rule Engine owns:
- evaluation constraints,
- scoring ceilings,
- and realism enforcement.

---

## Rule Examples

### Word Count Constraints
### Grammar Ceilings
### Repetition Penalties
### Development Quality Constraints

---

## Rule Engine MAY:
- modify scoring eligibility,
- apply penalties,
- and enforce evaluation consistency.

---

## Rule Engine MUST NOT:
- generate qualitative feedback,
- perform language interpretation,
- or independently evaluate argument quality.

---

## Rule Philosophy

Rules exist to:
- reduce score inflation,
- increase realism,
- and mimic professional examiner behavior.

---

# Gemini Evaluation Service

## Responsibilities

The Gemini Evaluation Service owns:
- qualitative interpretation,
- coherence analysis,
- lexical flexibility interpretation,
- and fluency impression analysis.

---

# Writing Responsibilities

## Examples
- argument quality analysis
- task achievement analysis
- coherence interpretation
- lexical sophistication interpretation

---

# Speaking Responsibilities

## Examples
- fluency impression
- pronunciation impression
- spoken coherence analysis
- lexical flexibility interpretation

---

## Gemini MAY:
- provide structured qualitative analysis,
- identify weaknesses,
- generate evidence-based feedback,
- and explain language quality issues.

---

## Gemini MUST NOT:
- determine final IELTS bands independently,
- bypass rule constraints,
- directly aggregate scores,
- or persist data independently.

---

## Gemini Philosophy

Gemini acts as:
- a simulated examiner assistant,
not:
- the authoritative scoring authority.

---

# Aggregation Engine

## Responsibilities

The Aggregation Engine owns:
- final score calculation,
- score normalization,
- constraint application,
- and calibrated IELTS band generation.

---

## Aggregation Engine MAY:
- combine metrics and AI outputs,
- apply weighting systems,
- enforce score ceilings,
- and generate final component bands.

---

## Aggregation Engine MUST NOT:
- generate qualitative explanations,
- perform raw language analysis,
- or directly process frontend requests.

---

## Aggregation Philosophy

The Aggregation Engine acts as:
- the final scoring authority.

All evaluation systems ultimately flow through this layer.

---

# Persistence Layer

## Responsibilities

The persistence layer owns:
- long-term storage,
- session persistence,
- evaluation history,
- analytics storage,
- and asset references.

---

# Firestore Responsibilities

Firestore stores:
- users
- sessions
- evaluations
- analytics metadata
- progress history

---

# Firebase Storage Responsibilities

Firebase Storage stores:
- speaking audio files
- binary assets

---

## Persistence Layer MUST NOT:
- contain evaluation logic,
- contain scoring logic,
- or independently mutate evaluation pipelines.

---

# Inter-Service Communication Rules

## Allowed Communication Pattern

```text
Frontend
  ↓
API Layer
  ↓
Orchestrator
  ↓
Services
```

---

## Forbidden Communication Patterns

### Frontend → Gemini directly
### Frontend → Aggregation Engine directly
### Metrics Engine → Firestore directly
### Gemini → Aggregation directly without orchestrator
### Services bypassing orchestrator sequencing

---

# Dependency Rules

## Allowed Dependencies

### Orchestrator
May depend on:
- Metrics Engine
- Rule Engine
- Gemini Service
- Aggregation Engine
- Persistence Services

---

## Metrics Engine
Should remain independent.

Metrics logic should not depend on:
- Gemini outputs
- frontend state
- persistence systems

---

## Aggregation Engine
May consume:
- metrics outputs
- Gemini outputs
- rule outputs

But should not directly depend on:
- frontend logic
- UI state
- persistence implementation details

---

# Data Ownership Philosophy

Each service should:
- own its processing domain,
- expose structured outputs,
- and avoid mutating external service states.

Shared mutable state should be minimized.

---

# Async Processing Boundaries

Async workflows should remain:
- isolated,
- retry-safe,
- and orchestration-controlled.

Services should not independently spawn uncontrolled processing chains.

---

# AI-Assisted Development Guidelines

The architecture is intentionally modular to support:
- spec-driven development,
- isolated code generation,
- predictable AI outputs,
- and maintainable scaling.

Each service should be generated and implemented independently whenever possible.

---

# Scalability Philosophy

The architecture should support future expansion without requiring:
- major rewrites,
- evaluation redesign,
- or service ownership restructuring.

Future scalability may include:
- queue systems,
- distributed evaluation,
- multi-model evaluation,
- realtime interactions,
- and adaptive tutoring systems.

---

# Guiding Principle

> "Every service should know exactly what it owns, what it does not own, and where its responsibility ends."

Architectural ambiguity should always be treated as a system risk.