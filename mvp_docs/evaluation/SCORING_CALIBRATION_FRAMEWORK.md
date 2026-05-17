# SCORING_CALIBRATION_FRAMEWORK.md

# Purpose

This document defines the scoring calibration architecture, evaluator consistency philosophy, and trust-preservation framework for the AI-powered IELTS CBT Simulator.

The calibration system is designed to:
- preserve long-term scoring consistency,
- reduce evaluator drift,
- prevent score inflation,
- stabilize AI-assisted evaluation behavior,
- and maximize user trust.

This document acts as:
- the evaluation stability constitution,
- the scoring consistency reference,
- and the calibration governance framework.

---

# Calibration Philosophy

The platform follows several core calibration principles.

---

# Realism Over Generosity

The system prioritizes:
- realistic preparation value,
- conservative interpretation,
- and evidence-based scoring.

The evaluator should NOT optimize for:
- user emotional satisfaction,
- artificially high bands,
- or motivational inflation.

---

# Consistency Over Variability

Stable scoring behavior is prioritized over:
- dynamic interpretation,
- creative scoring flexibility,
- or excessive evaluator variability.

Users should experience:
- predictable evaluation behavior,
- repeatable scoring logic,
- and stable band expectations.

---

# Trust-First Calibration

User trust is treated as:
- a critical system objective.

Trust is strengthened through:
- stable scoring,
- transparent reasoning,
- and realistic evaluation behavior.

---

# Deterministic-First Calibration

Deterministic systems should anchor:
- scoring ceilings,
- evidence thresholds,
- and evaluation normalization.

LLM outputs should remain:
- constrained,
- calibrated,
- and aggregation-controlled.

---

# Calibration Architecture

The calibration system operates across multiple layers.

---

# High-Level Calibration Pipeline

```text
Metrics Evidence
      ↓
Rule Constraints
      ↓
LLM Interpretation
      ↓
Aggregation Engine
      ↓
Calibration Layer
      ↓
Final Score Output
```

---

# Calibration Responsibilities

The calibration layer is responsible for:
- score normalization,
- realism enforcement,
- evaluator stabilization,
- and consistency preservation.

---

# Score Normalization Philosophy

Scores should:
- reflect realistic IELTS preparation standards,
- avoid unrealistic spikes,
- and maintain stable difficulty expectations.

---

# Normalization Objectives

The system should reduce:
- unstable score jumps,
- exaggerated component variation,
- and unrealistic high-band outcomes.

---

# Conservative Scoring Philosophy

When evidence is ambiguous:
- lower scores are generally preferred
unless:
- strong supporting evidence exists.

---

# Why Conservative Calibration Matters

Conservative calibration:
- improves realism,
- increases long-term trust,
- and reduces false confidence risk.

Artificial generosity may:
- temporarily please users,
but:
- ultimately damages credibility.

---

# Evaluator Drift Prevention

Evaluator drift occurs when:
- scoring behavior gradually changes over time.

---

# Drift Risk Sources

Examples:
- prompt mutations
- model updates
- context instability
- inconsistent orchestration
- hallucinated generosity

---

# Drift Prevention Mechanisms

The system should preserve:
- stable prompts,
- fixed calibration rules,
- deterministic anchors,
- and version-controlled orchestration.

---

# Calibration Anchors

Calibration anchors are:
- stable evaluation references
used to:
- monitor scoring consistency.

---

# Example Anchor Categories

### Weak Band 5 Essays
### Stable Band 6 Essays
### Borderline Band 7 Essays
### Hesitant Speaking Samples
### Strong Fluency Samples

---

# Anchor Philosophy

Anchor samples should remain:
- versioned,
- traceable,
- and periodically reviewed.

---

# Score Ceiling Philosophy

High IELTS bands should require:
- strong consistent evidence.

The system should avoid:
- accidental high-band inflation.

---

# Ceiling Examples

### Weak grammar stability caps Grammar scores
### Heavy hesitation caps Fluency scores
### Low lexical diversity caps Lexical Resource scores
### Weak development caps Task Response scores

---

# Anti-Score-Inflation Safeguards

The system includes safeguards against:
- inflated evaluation,
- LLM generosity bias,
- and unrealistic scoring outcomes.

---

# Safeguard Examples

### Conservative aggregation
### Evidence thresholds
### Constraint ceilings
### Calibration smoothing
### Stability weighting

---

# Stability Weighting Philosophy

The system may reduce confidence when:
- evaluation evidence is unstable,
- transcription quality is weak,
- or qualitative interpretation conflicts with metrics.

---

# Confidence Handling Philosophy

The system should avoid:
- fake precision,
- absolute certainty,
- and unsupported scoring confidence.

---

# Confidence-Aware Evaluation

The platform may:
- reduce scoring aggressiveness
when:
- evidence quality is weak.

---

# Example Confidence Risks

### Poor audio quality
### Heavy background noise
### Extremely short responses
### Severe grammar instability
### Incomplete task response

---

# Calibration Smoothing

Calibration smoothing reduces:
- unstable score spikes,
- exaggerated component variation,
- and inconsistent evaluation outcomes.

---

# Smoothing Philosophy

The system should prefer:
- stable realism,
over:
- volatile scoring behavior.

---

# Cross-Component Consistency

Component scores should remain:
- logically coherent,
- realistically aligned,
- and evidence-compatible.

---

# Example Inconsistency Risks

### Extremely high Lexical score with unstable grammar
### High Fluency despite fragmented speech
### Strong Coherence with weak development

---

# Calibration Monitoring Philosophy

Calibration quality should be continuously monitored.

---

# Monitoring Objectives

The system should track:
- score distributions,
- evaluator consistency,
- drift patterns,
- and unusual scoring behavior.

---

# Potential Monitoring Metrics

### Average band distributions
### High-band frequency
### Constraint trigger frequency
### Component variance
### Retry frequency

---

# Explainability Philosophy

Calibration systems should remain:
- observable,
- explainable,
- and auditable.

Users should understand:
- why scores were constrained,
not merely:
- what the scores are.

---

# Transparency Mechanisms

Users may receive:
- score explanations,
- constraint indicators,
- and evidence summaries.

---

# Trust Preservation Philosophy

Trust is strengthened through:
- consistency,
- transparency,
- and realistic evaluation behavior.

Trust is weakened through:
- score volatility,
- contradictory feedback,
- and unexplained scoring changes.

---

# Calibration Persistence Philosophy

The system should preserve:
- calibration metadata,
- scoring traces,
- applied constraints,
- and evaluation versions.

This supports:
- auditing,
- debugging,
- recalibration,
- and regression analysis.

---

# Human-Like Consistency Philosophy

Perfect examiner replication is impossible.

The goal is:
- realistic preparation utility,
not:
- exact institutional equivalence.

The evaluator should behave like:
- a stable conservative examiner,
not:
- a highly emotional or inconsistent evaluator.

---

# AI Governance Philosophy

LLM systems should remain:
- constrained,
- observable,
- and calibration-controlled.

The platform should avoid:
- unrestricted evaluator autonomy,
- hidden score manipulation,
- and opaque scoring behavior.

---

# Scalability Philosophy

The calibration framework should support future:
- multi-model consensus scoring
- advanced analytics
- evaluator benchmarking
- adaptive tutoring
- realtime scoring
- calibration dashboards

Future expansion must preserve:
- trust-first evaluation,
- conservative realism,
- and deterministic-first orchestration.

---

# Future Expansion Opportunities

Potential future systems include:
- ensemble evaluator calibration
- dynamic confidence scoring
- calibration dashboards
- evaluator benchmarking tools
- cross-attempt consistency analysis
- advanced statistical normalization

All future systems should preserve:
- scoring credibility,
- explainability,
- and trust stability.

---

# Guiding Principle

> "Calibration exists to preserve realistic preparation value, not to maximize user satisfaction."

Long-term trust should always outweigh short-term emotional approval.