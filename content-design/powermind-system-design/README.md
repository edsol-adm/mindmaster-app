# Powermind System Design Standards

> **Note on Naming Transition**
>
> Powermind is the evolving name for the platform previously called
> **MindMaster**.
>
> Some existing folders and legacy files still use the MindMaster naming
> because renaming them requires coordinated updates to file paths,
> navigation structures, and internal references. To maintain stability,
> the rename is being introduced gradually.
>
> All new system-level standards adopt the name **Powermind**, and the full
> repository will transition to the new naming scheme in a structured,
> incremental process.


This folder contains the core system-level standards that define how the
Powermind web app is structured, named, and implemented. These documents
ensure that all developers and designers follow a consistent architecture
across lessons, units, and future expansions.

Powermind’s curriculum content (Grade 1 Units 1–10) is stored separately in
`content-design/grade-1/`. This folder focuses specifically on the technical
and structural rules that enable the web app to function reliably.

---

## 📁 Contents

### **1. web-page-flow-standard.md**
Defines the canonical navigation structure for the Powermind web app:
page hierarchy, hub flows, screen transitions, and required upward/downward
navigation paths.

Ensures:
- no dead ends  
- consistent student experience  
- compliance with the Navigation Standard  
- predictable linking patterns for all modules  

---

### **2. pwa-architecture-standard.md**
Specifies Powermind’s PWA behaviour, including:
- manifest configuration  
- service worker scope and caching strategy  
- offline capabilities  
- app-shell model  
- versioning rules  

This is the authoritative reference for ensuring Powermind functions as a
progressive web app across devices and network conditions.

---

### **3. mobile-layout-behaviour-standard.md**
Defines how Powermind must behave on mobile:
- viewport rules  
- responsive breakpoints  
- layout constraints  
- touch interaction requirements  
- landscape behaviour  
- game UI adaptation  

Ensures a consistent mobile-first experience for students using phones and
tablets.

---

### **4. game-and-quiz-file-naming-standard.md**
Provides the naming conventions for all Powermind games and quizzes across
Units 1–10, covering:
- home games  
- in-class games  
- practice quizzes  
- reflection quizzes  

Ensures predictable file locations, consistent patterns, and scalability as
the curriculum grows.

---

## 🎯 Purpose of This Folder

- Establish a unified technical foundation for Powermind  
- Ensure app-wide consistency across units, screens, and future modules  
- Reduce developer ambiguity and onboarding time  
- Enable UNICEF and other partners to understand the system architecture  
- Keep system design separate from curriculum content  

These standards will continue to expand as the platform grows (e.g., UI
design tokens, accessibility guidelines, animation rules, global component
specs).

---

## 🧭 How These Standards Work Together

- **Web Page Flow** defines the navigation layer.  
- **PWA Architecture** defines the offline and caching layer.  
- **Mobile Behaviour** defines the responsive and interaction layer.  
- **Game/Quiz Naming** defines the file-structure layer.  

Together they form the core blueprint for Powermind’s technical ecosystem.

---

## 📝 Versioning

All standards follow semantic versioning (`v1.0`, `v1.1`, etc.).  
Updates should be documented in each file’s changelog section.

---

If you have questions about extending or applying these standards, please
contact the Powermind development lead.
