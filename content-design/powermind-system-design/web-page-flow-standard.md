**Full folder structure for Unit 01 - Design Lock 1.1**

powermind-website/

│

├── index.html ← Student Home

│

└── powermind/

│

├── curriculum-Y01.html ← Year 1 curriculum map

│

├── assets/

│ ├── common/

│ │ ├── images/

│ │ │ ├── powermind-logo.png

│ │ │ ├── mimi.webp

│ │ │ └── \[UI icons, generic art\]

│ │ ├── audio/

│ │ ├── sfx/

│ │ └── fonts/

│ │

│ └── unit-01/

│ ├── screens/ ← All screen backgrounds for Unit 01

│ │ ├── ls-01.01-back.webp

│ │ └── hr-01.01-back.webp

│ │

│ ├── hg-01.01-game01/ ← Home Game 1 assets

│ │ ├── images/

│ │ ├── audio/

│ │ └── sfx/

│ │

│ ├── hg-01.01-game02/ ← Home Game 2 assets

│ │ ├── images/

│ │ ├── audio/

│ │ └── sfx/

│ │

│ ├── icg-01.01-game01/ ← ONE in-class game per lesson

│ │ ├── images/

│ │ ├── audio/

│ │ └── sfx/

│ │

│ ├── icg-01.01-quiz01/ ← Quizzes (unlimited)

│ │ ├── images/

│ │ ├── audio/

│ │ └── sfx/

│ │

│ └── icg-01.01-rquiz01/ ← Reflection quizzes

│ ├── images/

│ ├── audio/

│ └── sfx/

│

└── unit-01/

├── screens/

│ ├── lesson-01.01.html ← Park (main lesson hub)

│ ├── ls-01.01.html ← Lesson Summary

│ ├── hr-01.01.html ← Home Reflection

│ ├── hg-01.01.html ← Home Games Hub

│ └── icg-01.01.html ← In-class Activities Hub

│

├── home-games/

│ ├── hg-01.01-game01.html ← Home Game 1

│ └── hg-01.01-game02.html ← Home Game 2

│ # Future lessons:

│ # hg-01.02-game01.html

│ # hg-01.02-game02.html

│

└── in-class-activities/

├── icg-01.01-game01.html ← In-class Game (one per lesson)

├── icg-01.01-quiz01.html ← Explore/Practice Quiz

└── icg-01.01-rquiz01.html ← Reflection Quiz

\# Future lesson quizzes follow:

\# icg-01.02-quiz01.html

\# icg-01.02-rquiz01.html

## 🔒 Design Lock 1.1 - Powermind Web App (Unit 01, Lesson 01)

## 1\. Purpose

This Design Lock defines:

- The **canonical folder structure** for:
  - powermind-website/
  - powermind/assets/
  - powermind/unit-01/
- The **roles and paths** of all HTML screens in Unit 01 Lesson 01.
- The **asset structure** (shared vs unit-specific).
- The **navigation flow** from:
  - index.html → curriculum-Y01.html → lesson-01.01.html  
        down into hubs, games, and quizzes, and all the way back up.
- The **required hrefs** and **navigation rules** that comply with the Navigation Standard.

## 2\. Canonical Folder Structure

### 2.1 Top-Level Structure

powermind-website/

│

├── index.html ← Student Home

│

└── powermind/

├── curriculum-Y01.html ← Year 1 curriculum map

├── assets/

└── unit-01/

### 2.2 Assets - Shared vs Unit 01

powermind/

└── assets/

├── common/ ← Shared across all units

│ ├── images/

│ │ ├── powermind-logo.png

│ │ ├── mimi.webp

│ │ ├── lesson-background.png ← Shared "park / hub" background

│ │ └── \[UI icons, generic art, shared buttons\]

│ ├── audio/

│ │ ├── lesson-screen-bgm.mp3 ← Shared background music

│ │ └── \[other shared audio\]

│ ├── sfx/

│ └── fonts/

│

└── unit-01/

├── screens/ ← Unit 01 specific screen backgrounds

│ ├── ls-01.01-back.webp ← Background for Lesson Summary (ls-01.01.html)

│ └── hr-01.01-back.webp ← Background for Home Reflection (hr-01.01.html)

│

├── hg-01.01-game01/ ← Home Game 1 assets

│ ├── images/

│ ├── audio/

│ └── sfx/

│

├── hg-01.01-game02/ ← Home Game 2 assets

│ ├── images/

│ ├── audio/

│ └── sfx/

│

├── icg-01.01-game01/ ← In-class game assets

│ ├── images/

│ ├── audio/

│ └── sfx/

│

├── icg-01.01-quiz01/ ← Explore / practice quiz assets

│ ├── images/

│ ├── audio/

│ └── sfx/

│

└── icg-01.01-rquiz01/ ← Reflection quiz assets

├── images/

├── audio/

└── sfx/

**Important clarifications (correction to previous lock):**

- There is **no** lesson-01.01-back.webp, hg-01.01-back.webp, or icg-01.01-back.webp at present.
- The **shared** background lesson-background.png in assets/common/images/ is used by:
  - lesson-01.01.html (Park / main hub)
  - hg-01.01.html (Home Games Hub)
  - icg-01.01.html (In-Class Activities Hub)  
        unless and until dedicated backdrops are added later.

### 2.3 HTML Structure - Unit 01 Lesson 01

powermind/

└── unit-01/

├── screens/

│ ├── lesson-01.01.html ← Park (main lesson hub)

│ ├── ls-01.01.html ← Lesson Summary (in-class)

│ ├── hr-01.01.html ← Home Reflection

│ ├── hg-01.01.html ← Home Games Hub

│ └── icg-01.01.html ← In-class Activities Hub

│

├── home-games/

│ ├── hg-01.01-game01.html ← Home Game 1

│ └── hg-01.01-game02.html ← Home Game 2

│

└── in-class-activities/

├── icg-01.01-game01.html ← In-class Game

├── icg-01.01-quiz01.html ← Explore / Practice Quiz

└── icg-01.01-rquiz01.html← Reflection Quiz

This structure is **fixed** for Unit 01 Lesson 01 and is the **template** for future units/lessons (e.g., unit-02, unit-03 etc.), with filenames following the same pattern.

## 3\. Screen Roles

### 3.1 index.html - Student Home (Top Level)

- Entry point into Powermind.
- Role:
  - Welcome / branding.
  - "Start Learning" button → Year 1 Curriculum.
- Location:
  - powermind-website/index.html

**Required navigation:**

- To curriculum:

&lt;a class="btn nav" href="powermind/curriculum-Y01.html"&gt;Start Learning&lt;/a&gt;

### 3.2 curriculum-Y01.html - Year 1 Curriculum Map

- Location:
  - powermind-website/powermind/curriculum-Y01.html
- Role:
  - Displays Year 1 lessons (in this prototype: **Unit 01 - Lesson 01** only).
  - Provides navigation back to Student Home.
  - Provides navigation into the Park screen for Unit 01 Lesson 01.

**Required navigation:**

- Back to Student Home:

&lt;a class="btn nav" href="../index.html"&gt;Student Home&lt;/a&gt;

- Into Unit 01 Lesson 01 Park:

&lt;a class="btn nav" href="unit-01/screens/lesson-01.01.html"&gt;Unit 01 - Lesson 01&lt;/a&gt;

### 3.3 lesson-01.01.html - Park Screen (Main Hub)

- Location:
  - powermind/unit-01/screens/lesson-01.01.html
- Background:
  - Uses shared background:

../../assets/common/images/lesson-background.png

- Role:
  - **Central hub** for Unit 01 Lesson 01.
  - Provides four main branches:
    - Lesson Summary (ls-01.01.html)
    - In-Class Activities (icg-01.01.html)
    - Home Games (hg-01.01.html)
    - Reflection Time (hr-01.01.html)
  - Provides navigation back up to:
    - Curriculum (curriculum-Y01.html)
    - (Optionally) Student Home (index.html), via curriculum.

**Required navigation (from Park):**

Inside lesson-01.01.html:

&lt;a class="btn nav" href="ls-01.01.html"&gt;Lesson Summary&lt;/a&gt;

&lt;a class="btn nav" href="icg-01.01.html"&gt;In-Class Activities&lt;/a&gt;

&lt;a class="btn nav" href="hg-01.01.html"&gt;Home Games&lt;/a&gt;

&lt;a class="btn nav" href="hr-01.01.html"&gt;Reflection Time&lt;/a&gt;

&lt;a class="btn nav" href="../../curriculum-Y01.html"&gt;Return to Lessons - Grade 1&lt;/a&gt;

(Any separate "Student Home" link, if implemented, must go via ../../index.html.)

### 3.4 ls-01.01.html - Lesson Summary (In-Class)

- Location:
  - powermind/unit-01/screens/ls-01.01.html
- Background:
  - Uses **unit-specific** background:

../../assets/unit-01/screens/ls-01.01-back.webp

- Role:
  - Teacher-led in-class summary screen.
  - Displays key teaching points and prompts.
- Required navigation:
  - Must always return to Park:

&lt;a class="btn nav" href="lesson-01.01.html"&gt;Return to the Park&lt;/a&gt;

### 3.5 hr-01.01.html - Home Reflection

- Location:
  - powermind/unit-01/screens/hr-01.01.html
- Background:
  - Uses **unit-specific** background:

../../assets/unit-01/screens/hr-01.01-back.webp

- Role:
  - Reflection tasks for student + parent/guardian, often text-heavy.
- Required navigation:
  - Must return to Park:

&lt;a class="btn nav" href="lesson-01.01.html"&gt;Return to the Park&lt;/a&gt;

### 3.6 hg-01.01.html - Home Games Hub

- Location:
  - powermind/unit-01/screens/hg-01.01.html
- Background:
  - Uses **shared** background:

../../assets/common/images/lesson-background.png

- Role:
  - Hub listing all home games for Lesson 01.01.
- Required navigation:

From hg-01.01.html to games:

&lt;a class="btn nav" href="../home-games/hg-01.01-game01.html"&gt;Play Home Game 1&lt;/a&gt;

&lt;a class="btn nav" href="../home-games/hg-01.01-game02.html"&gt;Play Home Game 2&lt;/a&gt;

From hg-01.01.html back to Park:

&lt;a class="btn nav" href="lesson-01.01.html"&gt;Return to Unit 1 Lesson 1&lt;/a&gt;

### 3.7 icg-01.01.html - In-Class Activities Hub

- Location:
  - powermind/unit-01/screens/icg-01.01.html
- Background:
  - Uses **shared** background:

../../assets/common/images/lesson-background.png

- Role:
  - Hub for all in-class digital activities (game + quizzes).
- Required navigation:

From icg-01.01.html to activities:

&lt;a class="btn nav" href="../in-class-activities/icg-01.01-game01.html"&gt;Start In-Class Game&lt;/a&gt;

&lt;a class="btn nav" href="../in-class-activities/icg-01.01-quiz01.html"&gt;Quiz 1&lt;/a&gt;

&lt;a class="btn nav" href="../in-class-activities/icg-01.01-rquiz01.html"&gt;Reflection Quiz 1&lt;/a&gt;

Back to Park:

&lt;a class="btn nav" href="lesson-01.01.html"&gt;Return to the Park&lt;/a&gt;

### 3.8 Games & Quizzes - Individual HTML Files

#### Home Games

- powermind/unit-01/home-games/hg-01.01-game01.html
- powermind/unit-01/home-games/hg-01.01-game02.html

Role:

- Standalone home games.
- Required navigation (back to Home Games Hub):

&lt;a class="btn nav" href="../screens/hg-01.01.html"&gt;Back to Home Games&lt;/a&gt;

#### In-Class Game & Quizzes

- Game:
  - powermind/unit-01/in-class-activities/icg-01.01-game01.html
- Explore/Practice quiz:
  - powermind/unit-01/in-class-activities/icg-01.01-quiz01.html
- Reflection quiz:
  - powermind/unit-01/in-class-activities/icg-01.01-rquiz01.html

Required navigation (back to In-Class Activities Hub):

&lt;a class="btn nav" href="../screens/icg-01.01.html"&gt;Back to In-Class Activities&lt;/a&gt;

## 4\. Webpage Flow (Down then Up)

This section is the **high-level flow** that all screens must support.

### 4.1 Main Downward Flow

index.html

↓ "Start Learning"

powermind/curriculum-Y01.html

↓ "Unit 01 - Lesson 01"

powermind/unit-01/screens/lesson-01.01.html (Park)

↓

ls-01.01.html (Lesson Summary)

icg-01.01.html (In-Class Activities Hub)

hg-01.01.html (Home Games Hub)

hr-01.01.html (Home Reflection)

(plus back up to curriculum)

### 4.2 In-Class Activities Flow

icg-01.01.html

↓

icg-01.01-game01.html → Back to icg-01.01.html

icg-01.01-quiz01.html → Back to icg-01.01.html

icg-01.01-rquiz01.html → Back to icg-01.01.html

↓

Return to Park → lesson-01.01.html

### 4.3 Home Games Flow

hg-01.01.html

↓

hg-01.01-game01.html → Back to hg-01.01.html

hg-01.01-game02.html → Back to hg-01.01.html

↓

Return to Unit 1 Lesson 1 (Park) → lesson-01.01.html

### 4.4 Summary & Reflection Flow

ls-01.01.html → Return to Park → lesson-01.01.html

hr-01.01.html → Return to Park → lesson-01.01.html

### 4.5 Upward Flow (No Dead Ends)

Every page must support this upward chain:

Game / Quiz → Hub (hg-01.01.html / icg-01.01.html)

Hub / Summary / Reflection → Park (lesson-01.01.html)

Park → Curriculum (curriculum-Y01.html)

Curriculum → Student Home (index.html)

## 5\. Navigation Standard (Powermind Compliance)

Powermind must comply with the shared Navigation Standard:

### 5.1 Anchors Only

- Inter-page navigation **must use** &lt;a href="..."&gt;.
- window.location, location.href, JS-only buttons etc. are **not allowed** for primary nav.
- &lt;button&gt; is reserved for in-page actions only.

### 5.2 Document-Relative Paths Only

- No leading /
- No http:// or https:// for internal nav.
- No &lt;base&gt; tag.
- All href paths must be relative to the current file's folder.

Example (from lesson-01.01.html):

&lt;a class="btn nav" href="ls-01.01.html"&gt;Lesson Summary&lt;/a&gt;

&lt;a class="btn nav" href="../../curriculum-Y01.html"&gt;Return to Lessons - Grade 1&lt;/a&gt;

### 5.3 Mandatory Upward Navigation

Every page must support:

Game / Quiz → Hub

Hub, Summary, Reflection → Park

Park → Curriculum

Curriculum → Student Home

### 5.4 Accessibility

- All navigation anchors must use .nav (e.g., class="btn nav" or class="return-btn nav").
- Focus styling:

.btn.nav:focus-visible,

.return-btn.nav:focus-visible {

outline: 4px solid #000;

outline-offset: 2px;

}

(Exact class naming can vary, but behavior must match.)

### 5.5 Folder & Naming Patterns

The folder and filename pattern defined above is **fixed** for Unit 01 Lesson 01 and must be mirrored for future units/lessons.

## 6\. Asset Path Rules (Summary)

From **any HTML inside** powermind/unit-01/screens/:

- Shared images (Mimi, buttons, shared lesson background):

../../assets/common/images/...

- Unit-01 specific screen backgrounds:

../../assets/unit-01/screens/...

- Shared background music:

../../assets/common/audio/lesson-screen-bgm.mp3

From **any HTML inside** powermind/unit-01/home-games/ or in-class-activities/:

- Shared images/audio:

../../assets/common/images/...

../../assets/common/audio/...

- Game/quiz-specific assets:

../../assets/unit-01/hg-01.01-game01/...

../../assets/unit-01/icg-01.01-game01/...

etc.