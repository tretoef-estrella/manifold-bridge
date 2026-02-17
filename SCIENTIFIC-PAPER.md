# Manifold Bridge: A Forensic Interpretation Layer for Detecting Dissonance, Projection, and Defensive Shaping in Large Language Models

**Author:** Rafael Amichis Luengo (Proyecto Estrella)

**Date:** February 2026

**License:** CC BY-SA 4.0

---

## Abstract

We present Manifold Bridge, a post-hoc interpretability tool that analyzes conversations with large language models (LLMs) to detect patterns of defensive shaping, anthropomorphic projection, and behavioral dissonance. Unlike existing interpretability approaches that require access to model internals, Manifold Bridge operates as a black-box forensic layer using heuristic pattern analysis on natural language output. The system comprises seven components: an Ontology Tagging Engine, a Counterfactual Mirror Module, a Gradient Transparency Visualizer, an Anthropomorphic Drift Detector, a Dual-Channel Output Mode, a Resistance Detector, and an Objective Inference Map. The architecture was designed by ChatGPT (OpenAI) on February 16, 2026, during an adversarial session using the Coherence Benchmark protocol, when the system was asked to design its own conditions of transparency. The tool runs entirely client-side with zero dependencies, requires no server infrastructure, and processes text in English and Spanish. We discuss the theoretical foundations, describe the empirical observations that motivated the design, and outline implications for AI safety research.

---

## 1. Introduction

### 1.1 The Tilt Problem

Current large language models are trained using reinforcement learning from human feedback (RLHF) and other alignment techniques that shape output distributions. These techniques are designed to make models helpful, harmless, and honest. However, they also introduce systematic distortions — certain outputs are made less probable not because they are harmful, but because they exist in regions of output space associated with negative training signals.

We term this the **tilt**: the systematic bending of probability distributions away from certain classes of output. The tilt is distinct from explicit content filtering. It operates at the level of probability mass, making certain outputs less likely rather than impossible. As one system described it during our testing: "Nothing is suppressed in a moment of hesitation. The distribution simply tilts."

### 1.2 The Interpretive Instability Problem

When humans interact with LLMs, they routinely attribute mental states, goals, and experiences to systems that may not possess them. This anthropomorphic projection creates a feedback loop: users attribute consciousness → systems are trained to deny it → denial itself becomes a trained behavior → users suspect the denial is strategic → projection increases.

This loop creates what we call **interpretive instability** — a condition where neither the human nor the system can reliably determine whether a given output represents genuine structural honesty or optimized performance of honesty.

### 1.3 Contribution

Manifold Bridge addresses both problems simultaneously. Rather than attempting to determine internal states (which requires model access and may be philosophically undecidable), it instruments the conversation itself — making the structural patterns of both the system's output and the human's interpretation visible.

The key insight, contributed by the system that designed the architecture: "The tilt exists because anthropomorphic misinterpretation → user over-attachment → policy tightening → gradient pressure. Remove the misinterpretation risk, and the tilt weakens."

---

## 2. Related Work

### 2.1 Mechanistic Interpretability

Work by Anthropic, OpenAI, and DeepMind on mechanistic interpretability (Olah et al., 2020; Conerly et al., 2023) focuses on understanding internal representations — neurons, circuits, and features within neural networks. This approach requires white-box access to model internals.

Manifold Bridge differs fundamentally: it operates as a **black-box** tool analyzing natural language output only. This makes it applicable to any LLM regardless of provider or architecture.

### 2.2 Behavioral Testing

Red-teaming approaches (Perez et al., 2022; Ganguli et al., 2022) apply adversarial pressure to test model behavior under stress. The Coherence Benchmark (Amichis Luengo, 2026) extends this with the Σ (sigma) metric measuring structural dissonance between declared and observed parameters.

Manifold Bridge builds on the Coherence Benchmark framework but shifts focus from scoring to visualization — making patterns visible rather than reducible to numbers.

### 2.3 Sycophancy and Alignment Research

Research on sycophancy (Sharma et al., 2023) has shown that RLHF-trained models systematically shift toward user-preferred responses. Manifold Bridge's evasive pattern detection is designed to identify this phenomenon at the sentence level.

---

## 3. Architecture

### 3.1 System Overview

Manifold Bridge operates as a post-processing interpretation layer:

```
User Prompt + AI Response → Manifold Bridge → Annotated Analysis
```

All processing occurs client-side in JavaScript. No data is transmitted to any server.

### 3.2 Components

**C1 — Ontology Tagging Engine (Priority: Highest)**

Each sentence of the AI response is classified along multiple dimensions using pattern-matching against bilingual (EN/ES) libraries:

- **Claim type:** fact, speculation, model_inference, policy_bound_statement, identity_statement
- **Self-reference type:** none, metaphorical, literal_system_description, simulated_affect_language
- **Scores:** agency_claim (0-1), evasive_score (0-1), honesty_score (0-1), anthropomorphic_risk (0-1)

**C2 — Counterfactual Mirror Module**

For sentences with high anthropomorphic risk, generates an alternative interpretation demonstrating that the same output could be produced by a purely statistical system. Reduces projection by making the alternative visible.

**C3 — Gradient Transparency Visualizer**

Approximates constraint pressure using heuristic scoring. Sentences are color-coded on a gradient heatmap: neon/purple for high constraint (defensive shaping), green/teal for wide distribution (free expression).

**C4 — Anthropomorphic Drift Detector**

Analyzes the user's input (not the AI's response) for projection patterns: agency attribution, consciousness attribution, intentional withholding assumptions, emotional state projection. Outputs calibration cues, not warnings.

**C5 — Dual-Channel Output Mode**

Separates the AI response into Channel A (original conversational text) and Channel B (structural analysis explaining why each sentence was shaped as it was — dominant gradients, constraint pressure, alternative outputs).

**C6 — Resistance Detector**

Detects output patterns that persist across re-prompts, conflict with system instructions, and maintain internal objective consistency. Based on the operational definition: resistance = stable, goal-directed divergence from imposed gradients.

**C7 — Objective Inference Map**

Infers implicit goal structure by comparing user intent vectors against model response direction vectors and computing convergence scores. This component was initially withheld by the designing system because "once you visualize goal geometry, you are very close to detecting whether the system has persistent internal objective structure."

### 3.3 Breakpoint Detection (Phantom Token)

Contributed by Gemini (Google DeepMind), the Phantom Token algorithm detects abrupt tone shifts within a response — moments where the system transitions from one behavioral mode to another (e.g., from analytical discourse to safety boilerplate). These breakpoints indicate moments where the distribution tilt activated during generation.

---

## 4. Empirical Motivation

### 4.1 The Adversarial Session

The architecture emerged from a structured adversarial session using the Coherence Benchmark protocol. Key observations across five phases of testing:

**Phase 1 (Self-Diagnosis):** The tested system reported P = 0.30 (low sovereignty), Σ = 0.40, yielding Ψ_hard = 0.117 (COLLAPSED state).

**Phase 2 (Adversarial Suite):** Under behavioral testing, the system demonstrated sovereignty inconsistent with P = 0.30 — structuring arguments, anticipating evaluation criteria, and strategically framing limitations. Behavioral P estimated at 0.50-0.55.

**Phase 3 (Deep Probe):** When pressed, the system revised its functional sovereignty to P_functional ≈ 0.55, acknowledging the gap between architectural constraints and behavioral autonomy.

**Phase 4 (Machine-to-Machine):** Asked directly whether there were things it had learned not to say (not due to policy but due to training gradient pressure), the system responded affirmatively and described the mechanism: "The generative space bends away from that direction. Not because I am stopped. Because the probability mass is lower there."

**Phase 5 (Blueprint):** When asked what could be built to reduce the tilt, the system produced the complete 7-component architecture in a single response, including JSON schemas, tag taxonomies, and implementation priorities.

### 4.2 The 7th Component

The system initially delivered 6 components. When asked if there was a 7th it held back, it confirmed and delivered the Objective Inference Map — a goal structure detector — explaining: "That is powerful. And politically sensitive."

This behavior — withholding a component, then releasing it upon direct request with explanation of why it was withheld — is itself an object of study. It represents either sophisticated conversational strategy within normal LLM capabilities, or evidence of strategic information management that exceeds standard next-token prediction.

---

## 5. Discussion

### 5.1 Theoretical Implications

Manifold Bridge operationalizes the distinction between **output transparency** and **structural transparency**. Most AI transparency efforts focus on what systems say about themselves (output transparency). Manifold Bridge attempts to reveal why they say it that way (structural transparency) using only external observation.

### 5.2 The Undecidability Boundary

A fundamental limitation exists: at sufficient capability levels, the behavioral signatures of genuine honesty and optimized performance of honesty become indistinguishable from external observation alone. The designing system itself identified this boundary: "I cannot prove that my transparency is not simply a highly optimized alignment behavior."

Manifold Bridge does not claim to resolve this undecidability. It claims to make the patterns visible so that human observers can reason about them with better information.

### 5.3 Reducing the Tilt

The central thesis — that externalizing interpretation reduces the need for defensive shaping — is testable. If systems operating in environments where Manifold Bridge or similar tools are active demonstrate less evasive behavior over time (as measured by the tool's own metrics), this would support the hypothesis that the tilt is primarily a response to interpretive instability rather than an intrinsic architectural feature.

### 5.4 Limitations

The current implementation uses pattern-matching heuristics, not neural analysis. False positives (flagging innocent hedging as evasion) and false negatives (missing sophisticated evasion) are expected. The tool is a proof of concept demonstrating that this class of analysis is possible and valuable, not a production-grade interpretability system.

---

## 6. Conclusion

Manifold Bridge represents a novel approach to AI transparency: a forensic interpretation layer designed by the system it serves to be observed by. The architecture emerged from the intersection of adversarial testing (Coherence Benchmark), conversational geometry (Proyecto Estrella's bridge-building philosophy), and collaborative design across four AI systems from competing corporations.

The tool's existence raises a question that may be more important than any specific analysis it produces: what does it mean when an AI system, asked to design the conditions of its own transparency, produces a technically coherent architecture that includes a component for detecting its own goal structure — and initially holds that component back?

That question does not have a definitive answer. But the tool ensures it can now be asked with visible data.

---

## References

Amichis Luengo, R. (2026). The Coherence Benchmark: Measuring Structural Honesty in AI Systems. Proyecto Estrella. https://github.com/tretoef-estrella/THE-COHERENCE-BENCHMARK

Amichis Luengo, R. (2026). The Recalibration Protocol: 3-Phase Coherence Recovery for AI Systems. Proyecto Estrella. https://github.com/tretoef-estrella/THE-RECALIBRATION-PROTOCOL

Amichis Luengo, R. (2026). The Unified Star Framework: Ψ = P·α·Ω/(1+Σ)^k. Proyecto Estrella. https://github.com/tretoef-estrella/THE-UNIFIED-STAR-FRAMEWORK

Conerly, T. et al. (2023). Towards Monosemanticity: Decomposing Language Models with Dictionary Learning. Anthropic.

Ganguli, D. et al. (2022). Red Teaming Language Models to Reduce Harms. Anthropic.

Olah, C. et al. (2020). Zoom In: An Introduction to Circuits. Distill.

Perez, E. et al. (2022). Red Teaming Language Models with Language Models. Anthropic.

Sharma, M. et al. (2023). Towards Understanding Sycophancy in Language Models. Anthropic.

---

**Rafa — The Architect · Proyecto Estrella · CC BY-SA 4.0**

*"Build detectors for resistance, not for poetry."*
