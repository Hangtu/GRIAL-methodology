# 🏆 G.R.I.A.L. Methodology

**Grounding • Restrictions • Itinerary • Architecture • Launch**

> **The first AI-Native Development Framework designed to prevent LLM hallucination and context drift.**
> _A strict protocol for High-Velocity Solo Developers, Vibe Coders, and Centaurs (Human + AI)._

## 🛑 The Problem

Traditional methodologies (Scrum, Agile, Kanban) were designed to manage _people_. They fail when your teammate is an AI that writes 100 lines of code per second but loses context every 10 minutes.

In the era of **Vibe Coding**, the bottleneck is no longer writing syntax; it is maintaining **Context Integrity**. Without strict guardrails, AI development leads to:

- **Scope Creep:** The AI suggests cool features that kill the MVP.
- **Context Drift:** The AI forgets early architectural decisions.
- **Spaghetti Code:** Circular dependencies created by short-term memory patches.

## 🛡️ The Solution: G.R.I.A.L.

G.R.I.A.L. is a pre-code ritual and a strict documentation standard that acts as a "Context Anchor" for Large Language Models (LLMs) like Claude 3.5 Sonnet, GPT-4o, or O1.

### The 5 Pillars

#### 1. G - Grounding (The North Star)

A single sentence that defines the _only_ problem the application solves. If an AI prompt does not serve this sentence, it is automatically rejected.

#### 2. R - Restrictions (The Anti-Roadmap)

A list of explicitly **banned** features for the current version. This creates a "Negative Constraint" that physically stops the AI from over-engineering or adding unnecessary complexity.

#### 3. I - Itinerary (The Happy Path)

A strictly linear user flow. We do not code for edge cases in the V1 phase. We code for the "Golden Path" to revenue/value.

#### 4. A - Architecture (The God Entity)

Identification of the single most critical database entity. The AI is forbidden from altering the schema of this entity once defined, preventing data structure collapse.

#### 5. L - Launch Criteria (Definition of Done)

A binary, verifiable condition for deployment. It stops the loop of eternal polishing.

---

## 🔥 The Phoenix Protocol (Memory Management)

To prevent AI hallucination, G.R.I.A.L. enforces the **Phoenix Protocol**:

1.  **Feature Complete:** When a feature from `roadmap.json` turns "Green".
2.  **Commit & Push:** Save the state.
3.  **Burn the Chat:** Delete the current AI chat session history.
4.  **Rebirth:** Start a fresh chat. The first prompt must always be: _"Read `ARCHITECTURE.md`. What is the next status in `roadmap.json`?"_

---

## 🚀 Getting Started

1.  **Clone this repo** or copy the files to your project root.
2.  **Rename** `ARCHITECTURE_TEMPLATE.md` to `ARCHITECTURE.md`.
3.  **Fill it out:** Spend 45 minutes defining your constraints. This is the only "Slow Thinking" required.
4.  **Vibe Code:** Point your AI (Cursor, Windsurf, Copilot) to the file and start building at light speed.

## License

MIT License. Free to use for personal and commercial projects.
