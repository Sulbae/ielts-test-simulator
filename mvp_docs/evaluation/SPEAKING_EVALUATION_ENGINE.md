# SPEAKING_EVALUATION_ENGINE.md

# Purpose

This document defines the IELTS Speaking evaluation architecture, scoring philosophy, and orchestration system for the AI-powered IELTS CBT Simulator.

The Speaking Evaluation Engine is designed to:
- simulate realistic IELTS Speaking evaluation behavior,
- preserve scoring consistency,
- maximize explainable speaking feedback,
- and maintain conservative trust-oriented assessment behavior.

This document acts as:
- the Speaking scoring constitution,
- the Speaking evaluation orchestration blueprint,
- and the AI Speaking assessment alignment framework.

---

# Speaking Evaluation Philosophy

The Speaking Evaluation Engine follows several core principles.

---

# Realistic Examiner Simulation

The system should simulate:
- strict examiner behavior,
- realistic scoring constraints,
- and conservative interpretation.

The platform prioritizes:
- preparation realism,
not:
- motivational scoring.

---

# Deterministic-First Evaluation

The system prioritizes:
- measurable speech evidence,
- deterministic speech metrics,
- and rule-governed orchestration.

LLMs assist interpretation but do not independently determine final Speaking bands.

---

# Explainable Speaking Feedback

Speaking feedback should be:
- evidence-backed,
- transparent,
- and educational.

Users should understand:
- what affected fluency,
- what reduced pronunciation clarity,
- and how speaking performance can improve.

---

# Conservative Calibration

If uncertainty exists:
- lower bands are generally preferred
unless:
- strong evidence supports higher performance.

---

# Speaking Complexity Philosophy

Speaking evaluation is inherently probabilistic.

Unlike Writing:
- audio quality,
- accents,
- microphone quality,
- background noise,
- and transcription uncertainty
all influence evaluation stability.

The system should remain:
- conservative,
- transparent,
- and limitation-aware.

---

# IELTS Speaking Component Architecture

The engine evaluates four IELTS Speaking criteria.

---

# Component 1 — Fluency and Coherence

## Purpose

Measures:
- speaking flow,
- response continuity,
- hesitation control,
- and idea organization.

---

# Fluency Responsibilities

The system evaluates:
- pause frequency,
- hesitation density,
- filler usage,
- speech continuity,
- and response progression.

---

# Deterministic Signals

Examples:
- words per minute
- filler frequency
- pause estimation
- interruption density
- repetition frequency

---

# Common Weaknesses

Examples:
- excessive hesitation
- fragmented responses
- filler overuse
- repetitive phrasing
- weak response development

---

# Component 2 — Lexical Resource

## Purpose

Measures:
- vocabulary flexibility,
- paraphrasing ability,
- and spoken lexical variation.

---

# Lexical Responsibilities

The system evaluates:
- vocabulary range,
- repetitive wording,
- paraphrasing behavior,
- and contextual word usage.

---

# Common Weaknesses

Examples:
- repetitive vocabulary
- simplistic wording
- memorized phrases
- lexical dependency
- weak paraphrasing

---

# Component 3 — Grammatical Range and Accuracy

## Purpose

Measures:
- spoken grammar control,
- sentence flexibility,
- and structural stability.

---

# Grammar Responsibilities

The system evaluates:
- grammar stability,
- sentence variation,
- tense consistency,
- and structural control.

---

# Common Weaknesses

Examples:
- unstable grammar
- repetitive sentence structures
- agreement errors
- tense inconsistency
- overly simple structures

---

# Component 4 — Pronunciation

## Purpose

Measures:
- speech intelligibility,
- pronunciation clarity,
- and listener comprehension ease.

---

# Pronunciation Philosophy

The system does NOT attempt:
- native-speaker imitation scoring.

The system evaluates:
- intelligibility,
- consistency,
- and communication clarity.

---

# Pronunciation Responsibilities

The system evaluates:
- articulation clarity,
- stress consistency,
- rhythm stability,
- and intelligibility indicators.

---

# Pronunciation Limitations

Pronunciation evaluation is inherently imperfect.

Factors affecting reliability include:
- microphone quality
- internet compression
- environment noise
- accent variation
- transcription instability

The system should communicate these limitations transparently.

---

# High-Level Speaking Evaluation Pipeline

```text
Audio Recording
      ↓
Audio Upload
      ↓
Speech-to-Text Transcription
      ↓
Transcript Normalization
      ↓
Deterministic Speech Metrics
      ↓
Rule Constraint Application
      ↓
LLM Qualitative Evaluation
      ↓
Aggregation Engine
      ↓
Calibration Layer
      ↓
Persistence
      ↓
Feedback Rendering
```

---

# Stage 1 — Audio Recording

## Purpose

Capture speaking responses in structured asynchronous format.

---

# Recording Philosophy

The MVP uses:
- asynchronous recording,
- controlled timing,
- and staged response flow.

Realtime conversation is intentionally excluded from MVP.

---

# Recording Responsibilities

The system manages:
- response timing
- recording duration
- upload integrity
- submission lifecycle

---

# Stage 2 — Speech-to-Text Transcription

## Purpose

Convert speaking audio into structured transcripts.

---

# Transcription Philosophy

Transcription is treated as:
- an approximation layer,
not:
- perfect linguistic truth.

---

# Transcription Responsibilities

The transcription system should:
- maximize clarity,
- preserve spoken structure,
- and minimize hallucinated corrections.

---

# Transcription Risks

Potential risks include:
- accent misinterpretation
- dropped words
- punctuation instability
- speech overlap
- background noise distortion

---

# Trust Philosophy

Users should understand:
- transcription uncertainty exists,
- and speaking evaluation has probabilistic limitations.

Transparency increases trust.

---

# Stage 3 — Transcript Normalization

## Purpose

Prepare transcripts for evaluation consistency.

---

# Normalization Responsibilities

Examples:
- filler segmentation
- sentence grouping
- repetition cleanup
- punctuation normalization

---

# Stage 4 — Deterministic Speech Metrics

## Purpose

Generate measurable speaking indicators.

---

# Metrics Categories

## Fluency Metrics
- words per minute
- hesitation density
- filler frequency
- pause estimation

---

## Lexical Metrics
- vocabulary diversity
- repetition frequency
- paraphrasing indicators

---

## Grammar Metrics
- grammar instability
- sentence complexity
- tense consistency

---

## Pronunciation Indicators

Indirect indicators:
- transcription confidence
- speech clarity consistency
- articulation stability

---

# Metrics Philosophy

Metrics provide:
- measurable evidence,
not:
- complete speaking authority.

---

# Stage 5 — Rule Engine Constraints

## Purpose

Apply realistic IELTS speaking constraints.

---

# Constraint Examples

---

## Fluency Ceiling

Heavy hesitation may:
- reduce Fluency ceilings.

---

## Grammar Stability Constraint

High grammar instability may:
- reduce Grammar ceilings.

---

## Lexical Repetition Constraint

Excessive repetition may:
- reduce Lexical Resource ceilings.

---

## Response Development Constraint

Short underdeveloped responses may:
- reduce Fluency and Coherence ceilings.

---

# Rule Philosophy

Rules exist to:
- preserve realism,
- reduce score inflation,
- and improve evaluation consistency.

---

# Stage 6 — LLM Qualitative Evaluation

## Purpose

Provide examiner-like qualitative interpretation.

---

# LLM Responsibilities

The LLM evaluates:
- coherence quality
- speaking development
- fluency impression
- lexical flexibility
- communicative effectiveness

---

# Pronunciation Responsibilities

The LLM may assist:
- pronunciation interpretation
through:
- transcript artifacts
- rhythm patterns
- speech consistency indicators

However:
pronunciation scoring should remain conservative.

---

# LLM Constraints

The LLM MUST NOT:
- independently determine final Speaking bands,
- bypass constraints,
- or directly aggregate scores.

---

# LLM Philosophy

The LLM acts as:
- a qualitative examiner assistant,
not:
- the authoritative speaking scorer.

---

# Stage 7 — Aggregation Engine

## Purpose

Combine:
- speech metrics,
- constraints,
- and qualitative analysis
into calibrated Speaking scores.

---

# Aggregation Responsibilities

The aggregation layer:
- normalizes component scores,
- applies ceilings,
- resolves inconsistencies,
- and calculates final Speaking bands.

---

# Aggregation Philosophy

The aggregation system prioritizes:
- realism,
- consistency,
- and conservative interpretation.

---

# Stage 8 — Calibration Layer

## Purpose

Preserve:
- realistic scoring behavior,
- stable evaluation,
- and trust consistency.

---

# Calibration Responsibilities

Calibration may:
- smooth unstable outputs,
- reduce unrealistic spikes,
- and enforce conservative scoring.

---

# Calibration Philosophy

Speaking evaluation should avoid:
- artificial confidence generation,
- unstable score volatility,
- and exaggerated fluency interpretation.

---

# Explainability Architecture

The Speaking engine prioritizes:
- transparent feedback,
- measurable explanations,
- and actionable insights.

---

# Explainability Mechanisms

Users should receive:
- component score breakdowns,
- hesitation indicators,
- repetition analysis,
- and pronunciation observations.

---

# Speaking Feedback Philosophy

Feedback should:
- reference observable patterns,
- explain measurable weaknesses,
- and remain IELTS-oriented.

Avoid:
- vague motivational feedback,
- unsupported praise,
- and fake precision claims.

---

# Transparency Philosophy

The system should communicate:
- evaluation limitations,
- transcription uncertainty,
- and probabilistic interpretation boundaries.

Transparency strengthens trust.

---

# Anti-Score-Inflation Safeguards

The engine includes safeguards against:
- unrealistic speaking scores,
- superficial fluency inflation,
- and LLM generosity bias.

---

# Safeguard Examples

### Constraint ceilings
### Conservative aggregation
### Hesitation penalties
### Development quality validation
### Pronunciation uncertainty weighting

---

# Memorized Speaking Detection Philosophy

The system should identify:
- over-rehearsed responses,
- unnatural speaking patterns,
- and scripted delivery behavior.

Highly memorized responses should not automatically receive high Fluency scores.

---

# Evaluation Consistency Philosophy

The Speaking engine should produce:
- stable outputs,
- predictable evaluation logic,
- and realistic preparation utility.

Perfect official IELTS replication is impossible.

The goal is:
- high preparation realism,
not:
- institutional equivalence.

---

# Persistence Philosophy

The system should preserve:
- speech metrics,
- transcription metadata,
- evaluation traces,
- scoring constraints,
- and calibration metadata.

This supports:
- auditability,
- debugging,
- and future recalibration.

---

# Async Processing Philosophy

Speaking workflows should remain:
- async-first,
- retry-safe,
- and orchestration-controlled.

Future scalability may include:
- realtime speaking,
- streaming transcription,
- and multi-model evaluation.

---

# AI Governance Philosophy

AI systems should remain:
- constrained,
- observable,
- and orchestrated.

The platform should avoid:
- uncontrolled AI scoring,
- opaque pronunciation authority,
- and hidden evaluation logic.

---

# Future Expansion Opportunities

Potential future systems include:
- realtime examiner simulation
- adaptive follow-up questioning
- speech rhythm visualization
- pronunciation waveform analysis
- speaking improvement coaching
- conversational AI examiner systems

Future systems should preserve:
- transparency,
- conservative realism,
- and trust-first evaluation.

---

# Guiding Principle

> "The Speaking Evaluation Engine should help users understand how understandable, stable, and IELTS-ready their spoken English truly is."

Evaluation credibility should always outweigh artificial fluency optimism.