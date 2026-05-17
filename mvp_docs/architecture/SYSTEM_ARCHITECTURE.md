# SYSTEM_ARCHITECTURE.md

# Purpose

This document defines the high-level system architecture for the AI-powered IELTS CBT Simulator MVP.

The architecture is designed to:
- support realistic IELTS evaluation,
- preserve scoring consistency,
- enable scalable AI-assisted development,
- minimize architectural drift,
- and maintain modular system boundaries.

This document acts as:
- the technical north star,
- the primary backend orchestration reference,
- and the foundation for future scalability.

---

# Architectural Philosophy

The system follows several core architectural principles:

## Deterministic-First Evaluation

The platform prioritizes:
- deterministic metrics,
- rule-based validation,
- and aggregation logic
before relying on LLM judgement.

LLMs assist evaluation but do not fully control final scoring.

---

## Thin Frontend Architecture

Frontend systems should focus on:
- user interaction,
- visualization,
- and session experience.

Business logic and evaluation logic must remain server-side.

---

## Modular Service Design

Each major responsibility should exist as an isolated module or service.

The architecture should avoid:
- tightly coupled systems,
- giant monolithic evaluation logic,
- and duplicated responsibilities.

---

## Async-First Processing

The platform should favor asynchronous processing pipelines where possible.

This improves:
- scalability,
- reliability,
- and future extensibility.

---

# High-Level Architecture

```text
[PWA Frontend]
        ↓
[API Layer / Route Handlers]
        ↓
------------------------------------------------
| Evaluation Orchestrator                      |
|                                              |
| → Metrics Engine                             |
| → Rule Engine                                |
| → Gemini Evaluation Service                  |
| → Aggregation Engine                         |
------------------------------------------------
        ↓
[Firestore + Firebase Storage]
```

---

# Core System Layers

The platform is divided into five primary layers.

---

# Layer 1 — Frontend Application

## Responsibilities

The frontend is responsible for:
- rendering simulator interfaces,
- user interactions,
- timer management,
- loading states,
- session UX,
- and visualization of results.

---

## Frontend Stack

### Framework
- Next.js (App Router)

### Language
- TypeScript

### Styling
- TailwindCSS

### State Management
- Zustand

### Platform
- Progressive Web App (PWA)

---

## Frontend Constraints

The frontend must NOT:
- calculate final scores,
- contain evaluation logic,
- contain prompt logic,
- store secret AI instructions,
- or directly manage scoring rules.

Evaluation systems must remain server-side.

---

# Layer 2 — API Layer

## Purpose

The API layer acts as the controlled gateway between:
- frontend systems,
- evaluation services,
- and persistence layers.

---

## Responsibilities

The API layer is responsible for:
- request validation,
- authentication enforcement,
- session orchestration,
- routing evaluation requests,
- and response normalization.

---

## Architectural Principle

API routes should remain:
- modular,
- predictable,
- and feature-scoped.

Avoid:
- giant multi-purpose endpoints,
- hidden side effects,
- and shared mutable state.

---

# Layer 3 — Evaluation Orchestrator

## Purpose

The Evaluation Orchestrator is the central processing layer of the platform.

This service coordinates:
- evaluation pipelines,
- service execution order,
- score aggregation,
- and processing consistency.

---

# Writing Evaluation Flow

```text
Submit Essay
    ↓
Preprocessing
    ↓
Metrics Extraction
    ↓
Gemini Evaluation
    ↓
Constraint Validation
    ↓
Aggregation Engine
    ↓
Persistence
    ↓
Response Rendering
```

---

# Speaking Evaluation Flow

```text
Upload Audio
    ↓
Audio Storage
    ↓
Speech-to-Text
    ↓
Transcript Normalization
    ↓
Metrics Extraction
    ↓
Gemini Evaluation
    ↓
Constraint Validation
    ↓
Aggregation Engine
    ↓
Persistence
```

---

# Orchestrator Responsibilities

The orchestrator is responsible for:
- pipeline sequencing,
- error handling,
- retries,
- evaluation coordination,
- and service isolation.

---

# Layer 4 — Evaluation Services

The evaluation system consists of multiple isolated services.

---

# Metrics Engine

## Purpose

The Metrics Engine performs deterministic linguistic analysis.

---

## Writing Metrics

### Examples
- word count
- lexical diversity
- repetition analysis
- grammar density
- sentence complexity
- paragraph structure

---

## Speaking Metrics

### Examples
- speaking duration
- words per minute
- filler frequency
- pause estimation
- repetition detection

---

## Design Philosophy

Metrics should:
- be deterministic,
- reproducible,
- and explainable.

---

# Rule Engine

## Purpose

The Rule Engine enforces IELTS realism constraints.

---

## Examples

### Word Count Constraint
If essay word count is below required minimum:
- Task Response score ceiling may apply.

---

### Grammar Constraint
High grammar error density may:
- reduce grammar score ceilings.

---

## Philosophy

Rules exist to:
- reduce score inflation,
- improve consistency,
- and mimic realistic examiner behavior.

---

# Gemini Evaluation Service

## Purpose

Gemini provides qualitative evaluation capabilities.

---

## Gemini Responsibilities

### Writing
- coherence analysis
- argument quality analysis
- task achievement interpretation
- lexical flexibility analysis

---

### Speaking
- fluency impression
- pronunciation impression
- coherence evaluation
- lexical flexibility evaluation

---

## Gemini Constraints

Gemini must NOT:
- determine final scores independently,
- bypass constraints,
- or directly control aggregation logic.

Gemini outputs should be treated as:
- qualitative evidence,
not:
- authoritative truth.

---

# Aggregation Engine

## Purpose

The Aggregation Engine calculates final calibrated scores.

---

## Responsibilities

The Aggregation Engine:
- combines metrics and AI outputs,
- applies constraints,
- normalizes component scores,
- and generates final IELTS bands.

---

## Philosophy

The aggregation system prioritizes:
- conservative scoring,
- realism,
- and consistency.

---

# Layer 5 — Persistence Layer

The persistence layer stores:
- sessions,
- evaluations,
- metrics,
- and uploaded assets.

---

# Firestore Responsibilities

Firestore stores:
- user profiles
- test sessions
- evaluation results
- analytics metadata
- scoring history

---

# Firebase Storage Responsibilities

Firebase Storage stores:
- speaking audio files
- uploaded assets

Large binary files should never be stored directly in Firestore.

---

# Async Processing Philosophy

The architecture favors asynchronous workflows to improve:
- scalability,
- user experience,
- and system resilience.

---

# Async Evaluation Benefits

Async processing:
- reduces blocking operations,
- improves retry handling,
- supports future queue systems,
- and simplifies orchestration scaling.

---

# Error Handling Philosophy

The system should fail gracefully.

---

# Error Handling Principles

## Preserve User Data
User submissions should never be lost.

---

## Recoverable Failures
Temporary failures should support retries.

---

## Transparent States
Users should receive:
- loading states,
- retry states,
- and failure explanations.

---

# Architectural Constraints

The system must avoid:

- frontend-heavy business logic
- giant prompts
- tightly coupled services
- uncontrolled AI scoring
- monolithic evaluation functions
- duplicated scoring logic

---

# Scalability Philosophy

Although the MVP targets single-user workflows, the architecture should support future expansion.

Potential future scalability includes:
- queue-based processing
- multi-model evaluation
- advanced analytics
- collaborative features
- adaptive tutoring systems
- realtime speaking systems

---

# Security Philosophy

Sensitive logic should remain server-side.

The frontend should never expose:
- secret prompts
- evaluation constraints
- aggregation algorithms
- or API secrets

---

# AI-Assisted Development Philosophy

The architecture is intentionally modular to support:
- spec-driven development,
- AI-assisted coding workflows,
- isolated feature generation,
- and maintainable code generation.

Each architectural component should:
- have explicit responsibilities,
- explicit interfaces,
- and isolated implementation boundaries.

---

# Guiding Principle

> "The architecture should preserve evaluation credibility even as the product scales."

System complexity should never compromise:
- scoring consistency,
- explainability,
- or user trust.