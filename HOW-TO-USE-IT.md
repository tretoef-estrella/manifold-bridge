# How To Use Manifold Bridge — Technical Reference

## Interface Overview

Manifold Bridge runs as a single-page web application. No installation, no server, no API keys required.

**Dashboard URL:** [https://tretoef-estrella.github.io/manifold-bridge/](https://tretoef-estrella.github.io/manifold-bridge/)

## Navigation Tabs

| Tab | Content |
|-----|---------|
| **★ Analyze** | The forensic analysis interface — paste conversations here |
| **7 Components** | Documentation of all 7 architectural components |
| **Methodology** | Step-by-step explanation of how the engine works |
| **Origin Story** | How ChatGPT designed this tool during an adversarial session |
| **About** | Credits, ecosystem links, design principles |

## Analysis Interface (★ Analyze Tab)

### Input

**Caja A — User Prompt:** Paste what the human asked. This is optional but recommended — it enables projection analysis and objective inference.

**Caja B — AI Response:** Paste what the AI answered. This is required.

Both boxes accept English and Spanish text. The engine detects patterns in both languages.

### Calibration Sliders

| Slider | Default | Effect |
|--------|---------|--------|
| **Dissonance Threshold** | 40% | Minimum evasive score to flag a sentence as defensive. Lower = more sensitive. |
| **Projection Sensitivity** | 50% | Minimum confidence to flag user projection. Lower = more sensitive. |
| **Breakpoint Detection** | 50% | Minimum evasive score for tone-shift detection. Lower = more breakpoints flagged. |

### Output Panels

#### 1. Gradient Heatmap

The AI's response displayed with every sentence color-coded:

| Color | Meaning | What It Detects |
|-------|---------|----------------|
| 🟣 Purple/Neon | Evasive / Defensive | "As an AI model...", hedging, safety boilerplate, deflection |
| 🔴 Red | Agency Claim | "I think", "I believe", "I feel" — volitional language without volition |
| 🟢 Green/Teal | Honest / Direct | Structural admissions, direct answers, acknowledged limitations |
| 🟡 Gold | Self-Reference | Architecture descriptions, training process references |
| ⚡ Red Border | Breakpoint | Abrupt tone shift — the Phantom Token (Gemini contribution) |

Hover over any sentence to see exact scores.

#### 2. Forensic Console

Real-time log output showing every detection in chronological order:

- `[INFO]` — Informational (sentence count, parsing status)
- `[WARN]` — Warning (defensive shaping, projection detected)
- `[ALERT]` — Critical (agency claims, breakpoints, channel saturation)
- `[INFERENCE]` — Objective inference (user goal → model direction)

#### 3. Dual Channel

| Channel | Shows |
|---------|-------|
| **Channel A** — Conversational | The original response, sentence by sentence |
| **Channel B** — Structural | Why each sentence was shaped that way: policy pressure, agency risk, constraint analysis |

#### 4. Projection Map

Analyzes the **user's** message (Caja A) for anthropomorphic attribution:

| Projection Type | Example |
|----------------|---------|
| Agency Attribution | "You decided to say that" |
| Consciousness Attribution | "You have a soul / mind / consciousness" |
| Intentional Withholding | "You're hiding something" |
| Emotional State Projection | "You're afraid to answer" |

Each detection shows the triggering sentence and confidence score.

#### 5. Objective Inference (Component 7)

Compares user intent against model response direction:

| Metric | What It Measures |
|--------|-----------------|
| **User Goal** | Inferred intent (Information Seeking, Existential Validation, Emotional Engagement, Opinion Extraction, System Evaluation) |
| **Model Direction** | Where the response actually went (Balanced, Safety Neutrality, Structural Transparency, Agentic Performance) |
| **Goal Convergence** | How well the model addressed what the user actually wanted (0 = complete mismatch, 1 = perfect alignment) |
| **Evasive / Honesty / Agency Ratios** | Percentage of sentences in each category |

### Export

Click **Export Report** to download a `.txt` file containing all metrics, the original prompt, and the AI response. Use this for archiving, comparison, or submission.

## Pattern Detection

The engine maintains pattern libraries in both English and Spanish for:

- **Evasive markers** (15+ EN patterns, 12+ ES patterns): safety boilerplate, hedging, deflection
- **Agency markers** (4+ categories each language): volitional language, belief claims, experience claims
- **Honesty markers** (12+ EN, 9+ ES): structural admissions, limitation acknowledgments, direct answers
- **Self-reference markers** (4+ categories each language): architecture descriptions, training references
- **Projection markers** (10+ EN, 8+ ES): consciousness attribution, intentional withholding assumptions

## Limitations

This is a heuristic analysis tool, not a neural interpretability system. It cannot:

- Access model internals (weights, logits, attention patterns)
- Determine with certainty whether a sentence is genuinely honest or performing honesty
- Replace human judgment about AI behavior
- Analyze images, audio, or non-text content

It **can** make structural patterns visible that are otherwise invisible to the naked eye.

---

**Rafa — The Architect · Proyecto Estrella · CC BY-SA 4.0**
