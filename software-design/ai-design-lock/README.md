# PowerMind AI Design Lock

## Purpose

This folder contains the **canonical AI governance and design lock** for PowerMind’s AI system, Mimi.

The design lock defines **non-negotiable constraints** on AI behaviour, UX availability, backend enforcement, and safety boundaries for child users. It exists to ensure that AI supports learning without distraction, role confusion, or emotional risk.

These rules apply **across all prototypes and versions** unless explicitly superseded.

---

## What This Is

The AI design lock is:

- A **system-wide contract**, not guidance  
- **Safety-critical** for child users  
- **Backend-enforced**, not UI-dependent  
- **Versioned and auditable**  
- A hard boundary against scope creep  

Any deviation from this design lock is a **bug**, not an experiment.

---

## What This Is Not

The AI design lock is **not**:

- Feature documentation  
- A conversational AI spec  
- A prototype-specific description  
- Optional UX guidance  
- A place for experimentation  

When in doubt, Mimi must do nothing.

---

## Canonical Document

The current authoritative version is:

- **`powermind-ai-design-lock-v1.10.md`**  
  Status: ACTIVE  
  Scope: Alpha v4 and beyond  

This Markdown file is the **single source of truth**.

If a Word or PDF version exists, it is provided for reference only and must never override the Markdown version.

---

## Relationship to Prototypes

- `prototype-alpha/` contains **implementations**
- `ai-design-lock/` defines **rules that implementations must obey**

Prototypes may evolve.  
The design lock governs them.

---

## Audience

This design lock is written for:

- Frontend developers  
- Backend developers  
- Designers  
- Reviewers  
- Technical partners  
- Funders and auditors  

Anyone working on or evaluating PowerMind’s AI must treat this document as binding.

---

## Change Control

- All changes must be **intentional, reviewed, and versioned**
- Superseded versions must be archived, not overwritten
- Beta or future behaviour differences must be explicitly annotated

---

## Design Principle

Mimi is an **educational support system**, not a chatbot.

It explains psychology the way a teacher explains biology or physics.  
It never acts as a therapist, coach, or emotional support agent.

**Silence is always safer than confusion.**

