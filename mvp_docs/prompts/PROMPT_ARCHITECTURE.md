# PROMPT_ENGINEERING_ARCHITECTURE.md

# Purpose

This document defines the prompt engineering architecture, orchestration philosophy, and LLM behavior management system for the AI-powered IELTS CBT Simulator.

The prompt architecture is designed to:
- preserve scoring consistency,
- minimize hallucination risk,
- maximize JSON reliability,
- improve evaluation explainability,
- and optimize scalable AI-assisted orchestration.

This document acts as:
- the AI orchestration constitution,
- the prompt engineering reference,
- and the LLM behavior alignment framework.

---

# Prompt Engineering Philosophy

The platform follows several core prompt engineering principles.

---

# Prompts Are Infrastructure

Prompts should be treated as:
- modular system components,
not:
- ad hoc text instructions.

Prompt architecture directly affects:
- scoring stability,
- evaluation realism,
- hallucination risk,
- and user trust.

---

# Deterministic-First Orchestration

LLMs assist:
- interpretation,
- explanation,
- and qualitative analysis.

LLMs should NOT:
- independently control scoring,
- bypass evaluation constraints,
- or generate unrestricted evaluation behavior.

---

# Conservative AI Behavior

Prompt systems should encourage:
- conservative scoring,
- evidence-backed interpretation,
- and realism-first evaluation.

The AI should avoid:
- excessive encouragement,
- unsupported praise,
- and inflated scoring behavior.

---

# Explainability First

Prompts should encourage:
- transparent reasoning,
- observable evidence references,
- and IELTS-oriented explanations.

Feedback should prioritize:
- educational usefulness,
not:
- motivational tone optimization.

---

# Modular Prompt Architecture

The platform uses layered prompt orchestration.

---

# High-Level Prompt Layers

```text
System Prompt Layer
        ↓
Task Prompt Layer
        ↓
Evaluation Prompt Layer
        ↓
Constraint Injection Layer
        ↓
Structured Output Layer
        ↓
Post-Processing Validation
```

---

# Layer 1 — System Prompt Layer

## Purpose

Defines:
- AI identity,
- evaluator behavior,
- tone constraints,
- and evaluation philosophy.

---

# System Prompt Responsibilities

The system prompt establishes:
- strict examiner behavior
- conservative evaluation philosophy
- transparency expectations
- JSON compliance requirements

---

# System Prompt Philosophy

System prompts should remain:
- stable,
- reusable,
- and highly controlled.

Frequent system prompt mutation increases:
- output instability,
- hallucination risk,
- and scoring inconsistency.

---

# Layer 2 — Task Prompt Layer

## Purpose

Defines:
- evaluation context,
- IELTS module type,
- and scoring objectives.

---

# Example Contexts

### Writing Task 2 Evaluation
### Speaking Fluency Analysis
### Pronunciation Observation
### Coherence Interpretation

---

# Task Prompt Philosophy

Task prompts should:
- remain narrow,
- define explicit responsibilities,
- and avoid mixed objectives.

---

# Layer 3 — Evaluation Prompt Layer

## Purpose

Guide:
- qualitative analysis,
- IELTS interpretation,
- and evidence-based reasoning.

---

# Evaluation Prompt Responsibilities

Prompts may request:
- argument quality analysis
- lexical flexibility interpretation
- fluency observations
- coherence analysis

---

# Evaluation Prompt Philosophy

Evaluation prompts should:
- guide interpretation,
- constrain scope,
- and minimize open-ended generation.

---

# Layer 4 — Constraint Injection Layer

## Purpose

Inject:
- deterministic constraints,
- scoring ceilings,
- and realism enforcement.

---

# Constraint Examples

### Word Count Penalties
### Grammar Stability Constraints
### Hesitation Constraints
### Repetition Constraints

---

# Constraint Philosophy

Constraints exist to:
- reduce score inflation,
- preserve realism,
- and stabilize outputs.

---

# Layer 5 — Structured Output Layer

## Purpose

Enforce:
- machine-readable outputs,
- predictable schemas,
- and frontend-safe responses.

---

# Structured Output Philosophy

LLMs should return:
- explicit JSON structures,
not:
- conversational responses.

---

# JSON Enforcement Strategy

The system should:
- strongly constrain output structure,
- minimize freeform text,
- and validate responses post-generation.

---

# JSON Reliability Techniques

Examples:
- explicit schema injection
- field-level instructions
- required keys
- output-only instructions
- strict formatting reminders

---

# Recommended Output Shape

```json
{
  "overallBand": 6.5,
  "components": {},
  "feedback": [],
  "constraintsApplied": []
}
```

---

# Post-Generation Validation

All AI outputs should pass:
- schema validation,
- type validation,
- and formatting verification.

Invalid outputs should trigger:
- retry workflows,
- repair prompts,
- or fallback strategies.

---

# Hallucination Control Architecture

Hallucination risk is treated as:
- a critical trust risk.

---

# Hallucination Prevention Principles

Prompts should:
- constrain scope,
- minimize speculative reasoning,
- and prioritize observable evidence.

---

# Forbidden AI Behaviors

The AI should avoid:
- fake certainty
- unsupported claims
- invented pronunciation precision
- exaggerated scoring confidence
- fabricated linguistic observations

---

# Evidence-Based Prompting

Prompts should encourage:
- evidence references,
- measurable observations,
- and contextual justification.

---

# Token Optimization Philosophy

Token efficiency is critical for:
- Gemini Flash free tier scalability,
- latency reduction,
- and operational sustainability.

---

# Token Efficiency Principles

Prompts should:
- avoid redundant instructions,
- minimize repeated schemas,
- and reuse modular components.

---

# Recommended Optimization Techniques

### Shared System Prompts
### Modular Prompt Fragments
### Minimal Context Injection
### Structured Outputs
### Reusable Constraint Blocks

---

# Few-Shot Philosophy

Few-shot examples should:
- demonstrate structure,
- stabilize formatting,
- and improve evaluator consistency.

Avoid:
- excessive examples,
- giant prompt payloads,
- and context pollution.

---

# Prompt Modularity Philosophy

Each prompt should:
- own one responsibility,
- remain reusable,
- and support isolated testing.

Avoid:
- giant monolithic prompts,
- mixed evaluation goals,
- and overloaded instruction blocks.

---

# Calibration Prompting

Calibration prompts may:
- enforce conservative behavior,
- stabilize scoring tendencies,
- and reduce evaluator drift.

---

# Calibration Examples

### Conservative score preference
### Evidence threshold reminders
### Anti-generosity instructions
### Realism reinforcement

---

# Retry and Repair Strategy

If outputs fail validation:
- repair prompts may be triggered.

---

# Repair Responsibilities

Repair prompts may:
- fix malformed JSON
- restore missing keys
- normalize invalid structures

Repair prompts should NOT:
- alter evaluation meaning.

---

# Prompt Versioning Philosophy

All prompts should be:
- versioned,
- traceable,
- and auditable.

---

# Why Versioning Matters

Prompt versioning supports:
- debugging
- evaluation comparison
- regression analysis
- calibration tracking

---

# Prompt Persistence Strategy

Prompt metadata may include:
- version identifiers
- evaluation type
- release notes
- calibration changes

---

# Prompt Testing Philosophy

Prompts should be:
- independently testable,
- regression-tested,
- and stability-monitored.

---

# Prompt Stability Goals

The system should prioritize:
- predictable outputs,
- scoring consistency,
- and reduced behavioral drift.

---

# Async Prompt Orchestration

Prompt orchestration should support:
- async workflows,
- modular execution,
- and retry-safe evaluation.

---

# AI Governance Philosophy

LLMs should remain:
- constrained,
- observable,
- and orchestrated.

The system should avoid:
- uncontrolled AI autonomy,
- opaque reasoning,
- and unrestricted scoring authority.

---

# Scalability Philosophy

The prompt architecture should support future:
- multi-model evaluation
- adaptive tutoring
- realtime interactions
- personalized coaching
- consensus scoring

Future expansion must preserve:
- explainability,
- deterministic-first orchestration,
- and conservative realism.

---

# Future Expansion Opportunities

Potential future prompt systems include:
- adaptive tutoring prompts
- conversational examiner prompts
- recommendation prompts
- personalized coaching prompts
- self-revision prompts
- study planning prompts

All future prompts should preserve:
- transparency,
- modularity,
- and trust-first AI behavior.

---

# Guiding Principle

> "Prompt engineering should constrain AI behavior into a predictable, explainable, and trustworthy evaluation system."

Prompt flexibility should never compromise:
- scoring realism,
- JSON reliability,
- or user trust.