# MVP_SCOPE.md

# Purpose

This document defines the exact scope boundaries for the initial MVP of the AI-powered IELTS CBT Simulator.

The purpose of the MVP is to:
- validate evaluation quality,
- establish trustworthiness,
- verify user demand,
- and build a scalable architectural foundation.

The MVP intentionally prioritizes:
- assessment realism,
- evaluation consistency,
- and explainable feedback
over feature quantity.

---

# MVP Philosophy

The MVP is designed around a single core principle:

> "A smaller but highly credible evaluation experience is more valuable than a broad but shallow feature set."

The initial release should feel:
- professional,
- trustworthy,
- and academically credible.

The MVP should avoid becoming:
- a generic chatbot,
- a gamified language app,
- or an overloaded exam platform.

---

# Core MVP Objectives

## 1. Simulate Real IELTS Conditions

Provide realistic test-taking workflows for selected IELTS modules.

The simulator should include:
- authentic timing behavior,
- realistic section flow,
- and strict evaluation patterns.

---

## 2. Deliver Explainable Evaluation

Users should receive:
- component band scores,
- measurable weaknesses,
- evidence-based explanations,
- and actionable improvement suggestions.

---

## 3. Validate Hybrid Evaluation Architecture

The MVP should validate the effectiveness of:
- deterministic linguistic metrics,
- rule-based scoring constraints,
- and Gemini-assisted qualitative analysis.

---

## 4. Establish Scalable Technical Foundations

The MVP architecture should support future expansion without requiring major rewrites.

---

# Included Modules

The MVP intentionally focuses on only two productive IELTS skills.

---

# MODULE 1 — Writing Task 2

## Included Features

### Writing Simulation
- Task 2 essay interface
- IELTS-style prompt presentation
- 40-minute timer
- autosave draft behavior
- submission workflow

---

### Writing Evaluation
- overall band estimation
- component band breakdown
- task response analysis
- coherence analysis
- lexical analysis
- grammar analysis

---

### Explainable Feedback
- highlighted weaknesses
- sentence-level corrections
- measurable writing metrics
- evidence-based scoring explanations
- actionable revision suggestions

---

### Deterministic Metrics
- word count
- lexical diversity
- repetition analysis
- grammar density
- paragraph structure analysis

---

### Hybrid Evaluation Pipeline
- local metric extraction
- Gemini-assisted evaluation
- scoring constraints
- aggregation engine

---

# MODULE 2 — Speaking Part 2

## Included Features

### Speaking Simulation
- cue card presentation
- preparation timer
- recording workflow
- async audio submission
- automatic stop behavior

---

### Speaking Evaluation
- overall speaking band estimation
- fluency analysis
- lexical analysis
- grammar analysis
- pronunciation impression analysis

---

### Speaking Metrics
- words per minute
- filler detection
- pause estimation
- response duration
- repetition analysis

---

### Async Processing Pipeline
- audio upload
- speech-to-text conversion
- transcript normalization
- evaluation orchestration

---

# Shared MVP Features

## Authentication
- Google login
- email authentication

---

## Session History
- past evaluations
- stored results
- score history

---

## Transparent Evaluation UI
- score breakdown visualization
- evidence display
- evaluation summaries

---

## PWA Support
- responsive interface
- installable app behavior
- mobile-friendly experience

---

# Technical Scope

## Frontend
- Next.js
- TypeScript
- TailwindCSS
- Zustand

---

## Backend
- Firebase ecosystem
- Firestore
- Firebase Storage
- API routes / server functions

---

## AI Layer
- Gemini API
- hybrid evaluation architecture
- structured prompt contracts

---

# Explicitly Excluded From MVP

The following features are intentionally excluded from the initial MVP.

---

# IELTS Sections Not Included

## Excluded
- Reading
- Listening
- Writing Task 1
- Speaking Part 1
- Speaking Part 3

These sections may be added after validation of the core evaluation engine.

---

# Advanced Speaking Features

## Excluded
- realtime speaking conversations
- AI interviewer avatars
- live pronunciation scoring
- streaming conversations

Reason:
These features significantly increase:
- complexity,
- latency,
- infrastructure cost,
- and debugging difficulty.

---

# Gamification Systems

## Excluded
- leaderboards
- streak systems
- achievement systems
- social competition features

Reason:
The MVP prioritizes:
- evaluation realism,
- credibility,
- and learning quality.

---

# Monetization Systems

## Excluded
- advanced subscription billing
- payment gateways
- enterprise plans
- team management

The initial release focuses on:
- product validation,
- evaluation quality,
- and user trust.

---

# Advanced AI Tutoring

## Excluded
- fully adaptive curriculum
- AI-generated study plans
- dynamic learning paths
- long-term coaching systems

These systems require:
- stable evaluation infrastructure,
- large user behavior datasets,
- and validated scoring reliability first.

---

# Architectural Constraints

The MVP must preserve:
- modular backend design,
- deterministic-first evaluation logic,
- and structured AI orchestration.

The system should avoid:
- tightly coupled logic,
- giant prompts,
- and frontend-heavy evaluation behavior.

---

# Development Priorities

## Phase 1 — Evaluation Core
Build:
- scoring architecture,
- metrics engine,
- aggregation logic,
- prompt contracts.

---

## Phase 2 — Writing Pipeline
Build:
- writing simulator,
- evaluation flow,
- explainable feedback system.

---

## Phase 3 — Speaking Pipeline
Build:
- async audio workflow,
- transcription pipeline,
- speaking evaluation.

---

## Phase 4 — UX Refinement
Build:
- analytics visualization,
- improved UI states,
- experience polish.

---

# Success Criteria

The MVP will be considered successful if users perceive the platform as:

- realistic,
- strict,
- trustworthy,
- and genuinely useful for IELTS preparation.

Success is measured more by:
- evaluation credibility,
than by:
- feature quantity.

---

# Future Expansion Opportunities

Potential future modules include:
- Reading simulator
- Listening simulator
- Writing Task 1
- Speaking Part 1 & 3
- adaptive learning systems
- AI conversational examiner
- personalized improvement analytics
- teacher dashboards
- collaborative learning features

These future systems should continue following:
- hybrid evaluation principles,
- transparency-first scoring,
- and strict examiner philosophy.