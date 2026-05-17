# FIREBASE_ARCHITECTURE.md

# Purpose

This document defines the Firebase architecture and Firestore data modeling strategy for the AI-powered IELTS CBT Simulator.

The architecture is designed to:
- support scalable evaluation workflows,
- preserve modular system boundaries,
- maintain evaluation auditability,
- optimize async processing,
- and improve AI-assisted backend development consistency.

This document acts as:
- the persistence architecture reference,
- the Firestore modeling contract,
- and the long-term data scalability foundation.

---

# Architectural Philosophy

The Firebase architecture follows several core principles.

---

# Modular Data Ownership

Each collection should:
- own a single logical domain,
- have explicit responsibilities,
- and minimize cross-domain mutation.

Collections should avoid:
- ambiguous ownership,
- duplicated business logic,
- and tightly coupled document structures.

---

# Async-First Persistence

The persistence architecture is designed around asynchronous evaluation pipelines.

The system should support:
- delayed processing,
- retry-safe workflows,
- and future queue-based orchestration.

---

# Auditability First

Evaluation systems should preserve:
- historical results,
- scoring evidence,
- evaluation metadata,
- and processing traces.

The system should support future:
- score recalibration,
- evaluation comparison,
- and model version analysis.

---

# Denormalization Strategy

Firestore favors:
- read optimization,
- predictable document access,
- and simplified query patterns.

Selective denormalization is acceptable when it improves:
- scalability,
- frontend simplicity,
- and evaluation retrieval performance.

---

# High-Level Firebase Architecture

```text
Firebase Auth
      ↓
Firestore
      ↓
-----------------------------------
| users                           |
| testSessions                    |
| evaluations                     |
| analytics                       |
| prompts                         |
-----------------------------------
      ↓
Firebase Storage
      ↓
-----------------------------------
| speaking-audio                  |
| uploaded-assets                 |
-----------------------------------
```

---

# Firebase Services

The MVP uses the following Firebase services.

---

# Firebase Authentication

## Purpose

Authentication manages:
- user identity,
- session ownership,
- and access control.

---

## Supported Methods

### Initial MVP
- Google Authentication
- Email Authentication

---

## Authentication Philosophy

Authentication should remain:
- simple,
- low-friction,
- and scalable.

Complex role systems are intentionally excluded from MVP.

---

# Firestore Architecture

Firestore acts as:
- the primary application database,
- evaluation persistence layer,
- and analytics metadata store.

---

# Collection Design Philosophy

Each collection should:
- represent a distinct domain,
- avoid giant nested structures,
- and support future scalability.

---

# Core Collections

## users

Stores:
- user profile metadata
- preferences
- target band settings
- account configuration

---

## Example Structure

```json
{
  "uid": "user_123",
  "displayName": "John Doe",
  "email": "john@example.com",
  "targetBand": 7.0,
  "preferences": {
    "strictMode": true
  },
  "createdAt": "timestamp"
}
```

---

# users Collection Responsibilities

## Owns
- profile identity
- user preferences
- personalization metadata

---

## Must NOT Store
- full evaluation results
- large analytics payloads
- audio references
- raw submissions

---

# testSessions

## Purpose

Represents:
- active simulations,
- user test attempts,
- and submission lifecycle states.

---

## Example Structure

```json
{
  "sessionId": "session_001",
  "userId": "user_123",
  "module": "writing_task_2",
  "status": "submitted",
  "startedAt": "timestamp",
  "submittedAt": "timestamp",
  "wordCount": 312
}
```

---

# Session States

Possible states:
- initialized
- active
- submitted
- evaluating
- completed
- failed

---

# testSessions Responsibilities

## Owns
- session lifecycle
- timing metadata
- submission metadata
- processing state

---

## Must NOT Store
- giant evaluation payloads
- raw AI reasoning
- large audio blobs

---

# evaluations

## Purpose

Stores:
- final evaluation outputs,
- component scores,
- evidence summaries,
- and evaluation metadata.

This collection is intentionally separated from testSessions.

---

# Why Separation Matters

Separating evaluations allows:
- re-evaluation,
- versioning,
- calibration experiments,
- and future multi-model comparisons.

---

## Example Structure

```json
{
  "evaluationId": "eval_001",
  "sessionId": "session_001",
  "overallBand": 6.5,
  "components": {
    "taskResponse": 6.5,
    "coherence": 6.0,
    "lexical": 7.0,
    "grammar": 6.0
  },
  "constraintsApplied": [
    "grammar_cap"
  ],
  "createdAt": "timestamp"
}
```

---

# evaluations Responsibilities

## Owns
- scoring outputs
- component bands
- evidence summaries
- constraint metadata
- evaluation versions

---

## Must NOT Store
- large binary assets
- frontend UI state
- temporary processing state

---

# analytics

## Purpose

Stores:
- lightweight analytics metadata,
- user progress summaries,
- and future performance tracking.

---

## Example Use Cases

### Future Analytics
- average band trends
- improvement tracking
- module performance
- evaluation frequency

---

# Analytics Philosophy

Analytics should remain:
- lightweight,
- aggregate-oriented,
- and query-efficient.

---

# prompts

## Purpose

Stores:
- prompt versions,
- evaluation templates,
- and AI configuration metadata.

---

# Why Prompt Persistence Matters

Prompt storage supports:
- evaluation reproducibility,
- future calibration,
- prompt version comparison,
- and debugging.

---

# Prompt Philosophy

Prompts should be:
- versioned,
- traceable,
- and auditable.

---

# Firebase Storage Architecture

Firebase Storage stores:
- speaking audio files,
- uploaded assets,
- and large binary data.

---

# Storage Philosophy

Binary assets should NEVER be stored inside Firestore documents.

Firestore should only store:
- metadata,
- references,
- and processing status.

---

# Speaking Audio Structure

```text
/speaking-audio/{userId}/{sessionId}.webm
```

---

# Audio Metadata Strategy

Firestore should store:
- audio URL references,
- upload status,
- transcription status,
- and processing metadata.

---

# Async Evaluation Persistence Flow

## Writing Flow

```text
Create Session
    ↓
Store Submission Metadata
    ↓
Run Evaluation
    ↓
Store Evaluation Result
    ↓
Update Session Status
```

---

# Speaking Flow

```text
Upload Audio
    ↓
Store Audio Metadata
    ↓
Speech-to-Text
    ↓
Evaluation Pipeline
    ↓
Persist Evaluation
    ↓
Finalize Session
```

---

# Persistence Lifecycle Philosophy

The system should preserve:
- evaluation history,
- failed processing attempts,
- and historical scoring context.

User submissions should never be silently discarded.

---

# Security Philosophy

Sensitive logic should remain server-side.

---

# Firestore Security Principles

Clients should NOT:
- directly modify evaluation results,
- directly mutate scoring data,
- or access protected evaluation logic.

---

# Frontend Access Philosophy

Frontend systems should:
- consume controlled APIs,
not:
- directly manage persistence complexity.

---

# Scalability Philosophy

The architecture should support future:
- queue systems,
- multi-model evaluation,
- realtime processing,
- collaborative systems,
- and analytics expansion.

---

# Scalability Constraints

Avoid:
- giant documents,
- deeply nested collections,
- uncontrolled document growth,
- and frontend-managed aggregation.

---

# AI-Assisted Development Philosophy

The Firestore structure is intentionally modular to improve:
- AI-generated backend consistency,
- isolated feature implementation,
- and maintainable scaling.

Each collection should:
- have explicit ownership,
- explicit lifecycle behavior,
- and explicit access boundaries.

---

# Future Expansion Opportunities

Potential future collections may include:
- readingSessions
- listeningSessions
- adaptiveRecommendations
- studyPlans
- teacherFeedback
- collaborativeRooms

Future expansion should preserve:
- modular ownership,
- auditability,
- and evaluation consistency.

---

# Guiding Principle

> "Persistence architecture should preserve evaluation credibility, scalability, and historical traceability."

Database convenience should never compromise:
- auditability,
- modularity,
- or long-term maintainability.