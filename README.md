# 🏆 G.R.I.A.L. Methodology

**Grounding • Restrictions • Itinerary • Architecture • Launch**

> The first software methodology designed specifically for **AI-Assisted Programming (Vibe Coding)** and **High-Velocity Solo Developers**.

## 🛑 The Problem

Traditional methodologies (Scrum, Agile) manage _people_. They fail when your teammate is an AI that writes 100 lines per second but forgets the context in 10 minutes. This leads to:

- Infinite Feature Creep.
- Spaghetti Code.
- "Context Drift" (AI Hallucinations).

## 🛡️ The Solution: G.R.I.A.L.

G.R.I.A.L. is a pre-code ritual and a strict documentation standard that acts as a "Guardrail" for Large Language Models (LLMs) like Claude 3.5 Sonnet or GPT-4o.

### The 5 Pillars

#### 1. G - Grounding (Propósito)

One sentence that defines the _only_ problem the app solves. If a prompt doesn't serve this sentence, it is rejected.

#### 2. R - Restrictions (El Anti-Roadmap)

A list of explicitly banned features. This creates a "Negative Constraint" that stops the AI from over-engineering.

#### 3. I - Itinerary (Happy Path)

A strictly linear user flow. No edge cases allowed in V1.

#### 4. A - Architecture (God Entity)

Definition of the single most important database entity. The AI is forbidden from altering this schema once defined.

#### 5. L - Launch Criteria (Definition of Done)

A binary condition for deployment. Stops the loop of eternal polishing.

## 🔥 The Phoenix Protocol (Memory Management)

To prevent AI hallucination:

1. Complete one feature from the Roadmap.
2. Commit & Push.
3. **DELETE** the AI chat history.
4. Start fresh instructing the AI to read the `GRIAL.md` file.

## 🚀 Getting Started

1. Copy `GRIAL_TEMPLATE.md` to your root folder.
2. Spend 45 minutes filling it out.
3. Point your AI (Cursor, Copilot, Windsurf) to read it before every session.

---

_Created by Hang Tu Wong Ley Franco. Open Source under MIT License._
