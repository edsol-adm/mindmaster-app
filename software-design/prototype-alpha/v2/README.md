# Prototype Alpha v2 — Functional Feasibility & Offline Usability

## Purpose of v2

Prototype Alpha v2 marked the transition from conceptual validation (v1) to a **minimal functional prototype**.  
The objective of this iteration was to test whether PowerMind’s learning design could operate as a **real, executable system** under basic classroom conditions.

At this stage, the key question was:

> Can a functional, offline-capable digital prototype deliver the intended learning experience in a way that children and teachers can navigate independently?

---

## What v2 Consisted Of

Prototype Alpha v2 introduced **executable functionality**, while remaining deliberately constrained in scope.

### 1. Functional offline HTML prototype
- Browser-based HTML5 activities packaged as a **single-file, offline prototype**
- Designed to run fully without internet connectivity
- No backend services or server components
- No user accounts or authentication

**Reference artefact:**  
The file `mindmaster_prototype_v2.html` is included in this directory to illustrate the functional scope of Prototype Alpha v2.  
It is provided as a **reference artefact only**, is **not maintained**, and has been **superseded by Prototype Alpha v3**.

### 2. Core navigation structure
- Menu screen with levels, units, and locked lessons
- Level and unit selection
- Entry point into one playable lesson (Level 2 → Unit 4 → Lesson 1)

Navigation was intentionally simple to test baseline comprehension.

### 3. Limited content scope
- Structural representation of multiple levels and units
- One complete, playable lesson
- Early implementation of the Explore → Practice → Reflect learning flow

### 4. Basic interaction and feedback logic
- Core interaction types (tap, select, sort, drag-and-drop)
- Immediate correctness feedback
- Simple practice and completion logic

### 5. Local state simulation
- Browser local storage used to simulate session completion
- No cloud sync or persistence across devices
- No analytics or reporting pipeline

---

## What v2 Did *Not* Include

To keep the scope appropriate for this stage, Prototype Alpha v2 did **not** include:
- Polished visual design or animations
- Audio prompts or rich feedback
- Classroom sync or teacher dashboards
- Learning analytics or reporting
- Home learning mode
- AI functionality
- PWA packaging or installability

---

## What Was Tested in v2

Testing focused on **functional feasibility and usability**, not learning outcomes.

### 1. Offline operability
- Could the prototype run reliably without internet connectivity?
- Did activities load and respond correctly in an offline environment?

### 2. Navigation comprehension
- Could users independently reach the playable lesson?
- Were menus and transitions understandable without explanation?

### 3. Interface usability
- Readability of fonts and labels
- Recognisability of icons
- Clarity of interaction affordances

### 4. Child autonomy
- Could students complete activities without step-by-step adult guidance?
- Where did confusion or hesitation occur?

---

## Participants

- 3 classroom teachers  
- 3 students  

Testing involved short, structured hands-on sessions and observation, rather than extended classroom deployment.

---

## Key Findings and Learnings

Feedback from Prototype Alpha v2 confirmed that:

- Offline delivery was technically viable in a browser-based setup
- Core interactions functioned as intended
- Children could complete activities independently once inside a lesson
- Navigation cues and visual hierarchy required improvement
- The interface needed to be more engaging and explicit for younger learners

These findings directly informed the design priorities for v3.

---

## Decisions Informed by v2

As a result of v2 testing:

- Navigation and visual hierarchy became a primary focus for the next iteration
- Engagement elements (audio, animation, clearer feedback) were prioritised
- Interaction patterns were refined for consistency and clarity
- v3 expanded content breadth to test engagement across multiple activity formats

---

## Status of v2

Prototype Alpha v2 is **complete and closed**.

It is documented here to demonstrate the iterative development process under a Rapid Application Development (RAD) approach.  
The included HTML file is retained solely for transparency and historical reference.

---

## How v2 Fits in the Alpha Sequence

- **v1** — Conceptual and pedagogical validation  
- **v2** — Functional feasibility and offline usability (this stage)  
- **v3** — Engagement, instructional clarity, and classroom viability  

The current contents of the `prototype-alpha/` root directory represent **Prototype Alpha v3**, incorporating learnings from v1 and v2.
