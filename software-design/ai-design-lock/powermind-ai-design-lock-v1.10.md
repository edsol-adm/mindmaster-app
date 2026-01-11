# ****PowerMind-AI: AI Integration - Design Lock v1.10****

****version alpha****

**Status:** ACTIVE - Canonical reference  
**Supersedes:** v1.5  
**Audience:** Designers, frontend developers, backend developers, reviewers  
**Priority:** UX clarity and safety for young learners (hard constraint)

This document defines authoritative AI behavior to be enforced server-side (powermind-ai.js) and mirrored by frontend UI gating.  
Frontend hiding alone is never sufficient.

NOTE ON BETA - where the beta will differ from alpha there is a summary of the differences in the section. Bets notes should be ignored during alpha/prototype testing

## ****1\. Purpose & Framing****

Mimi is an educational support system, not a conversational agent.

Mimi explains psychology the way a teacher explains biology or physics:

- clear
- factual
- neutral
- non-emotional

Mimi never acts as:

- a therapist
- a coach
- an emotional support agent
- a personal advisor

Lessons, reflections, games, and quizzes are the primary learning engines.

By default:

- Mimi is reactive, not proactive

The only two cases where Mimi may proactively lead interaction:

- **Guided Home Reflection**  
    Mimi leads a structured, linear reflection flow.
- **Pop Quiz**  
    Mimi initiates a short, controlled recall activity.

Outside of these two cases:

- Mimi responds only when the user initiates
- Mimi does not drive sessions
- Mimi limits interactions to a small number of responses then encourages the user to continue using the app
- Mimi redirects back to the activity promptly

**When in doubt, Mimi must remain silent and take no action.**

**Beta note - no change**

## ****2\. Page Types****

- Every screen declares exactly one page_type.  
    A screen may not change page_type during a session.
- page_type governs all AI availability and behavior. Every screen must also declare a stable, non-empty screen_id. The screen_id does not change during the session and uniquely identifies the current screen for AI scoping and interaction limits.

| page_type | Meaning |
| --- | --- |
| entry | Outside lesson structure (login, onboarding, "what is this app?", "where do I go?") |
| nav | Nav screens contain no embedded instructional content and exist only for in-lesson navigation. Mimi may provide navigation guidance and respond to Ask Psych.  <br>**Pop Quiz is permitted only on nav screens and is always Mimi-initiated (proactive). Pop Quiz must never appear as a user-selectable mode or button, and must never be manually triggered by the learner.** |
| learn_ls | Lesson Summary |
| learn_hr | The Home Reflection page has three internal states-before, during, and after the Mimi-guided reflection-which do not change the page_type but govern AI availability via an explicit hr_phase field. The "During" phase is Mimi-initiated (proactive). The other Before and After phases are reactive |
| task | Task pages include both games and quizzes and must declare a task_id so the backend can load the correct \*-gameflow.json and enforce Task Help |

Canonical examples:

- entry: index, student-home, teacher-home, curriculum-Y01
- nav: lesson parks and navigation hubs (lesson-01.xx parks, hg-01.01.html and icg-01.01.html hub screens; not hg-01.01-game01.html or icg-01.01-game01.html task pages)

Beta note - no change

## 3\. Chat Interfaces & Interaction Mechanics

### 3.1 Main Mimi Chatbox - Visual & Interaction Mechanics

**Purpose**  
The Main Mimi Chatbox is the single, user-initiated interface for all **reactive** AI interactions, including:

- Site Guide (entry)
- Nav Guide
- Ask Psych
- Explain Topic
- Task Help

**Visual form**

- Appears as a floating Mimi button when inactive, positioned at the **top of the screen.**
- Expands into a single chat panel when opened.
- Panel visibility defines the **active state**.
- Only one Main Mimi Chatbox instance may exist at a time.

**Activation**

- The Main Mimi Chatbox opens **only** via explicit user click on the Mimi avatar.
- Keyboard-triggered activation does not open the chatbox.
- **Immediately on avatar click**, the background page is locked: all navigation, buttons, links, and page controls are disabled, and remain disabled until the chatbox is closed via the Cancel (×) button.
- On page_type:"entry", the chatbox operates in **Site Guide** mode only.
- On all other page types, the chatbox exposes only the modes permitted for that page_type.
- If multiple modes are permitted, a mode selector (dropdown) is shown; if only one mode is permitted, no selector is shown.
- **Active definition:** the chatbox is active when the panel is visible on screen.
- Mimi retains awareness of whether the user has moved to a different section, navigated to another screen, or interacted with a task, for the purpose of interaction limits only.

**On Close**

- **The Main Mimi Chatbox may be closed only by clicking the Cancel (×) button in the panel header. No other exit method is permitted. On close:**
  - All text in the input field and Mimi response area is cleared.
  - The chat panel is hidden.
  - The background page is immediately reactivated.
  - **Interaction limits and allowances are not reset. The user must move to another section, navigate to another screen, or interact with a task to unlock further questions.**

**Interaction mechanics**

- Only one request may be **in flight** at any time.
- A blank request (empty input) is ignored. Submitting a blank request does **not** disable input, does **not** disable the Ask button, does **not** trigger a request, and does **not** count toward any interaction limit.
- user selects the mode (if multiple available)>types question>clicks ask button> this reveals a panel underneath in which mimi response displayed
- Clicking the Ask button with non-empty input disables the input field, Ask button and Cancel X button while the request is in flight.
- After a response:
  - Input is re-enabled only for modes not yet used.
  - In alpha there is a 1 question limit. After responding to the single user question Mimi must encourage the learner to continue the current activity or navigate onward. And explains that no further questions allowed without other actions (move to another section or another screen)
- Question limits
  - 1 question is allowed per session. A session is reset by user moving to another section on the same page, or navigating to another screen, or interacting with a task (game or quiz).
  - The chatbox remains open and readable, but any mode that has reached its question limit is disabled and shown greyed out in the dropdown.
  - Disabled modes cannot be selected and do not accept input.
  - If more than one mode is available, any mode that has not reached its limit remains selectable.
  - If all available modes have reached their limits, all modes are disabled and the **only active control** is the Cancel (×) button.

**Disablement / locking rules**  
The Main Mimi Chatbox is **disabled and unavailable** when:

- Guided Home Reflection is active.
- A Pop Quiz panel is visible.
- The current page_type or phase does not permit any Main Mimi modes.

**Concurrency rules**

- If another interface is scheduled to appear while the Main Mimi Chatbox is visible, it must be **fully blocked** from activating (no visual, audio, timer, or state change) and queued according to that interface's rules until the Mimi chatbox is closed.

### ****Proactivity Rule****

- The Main Mimi Chatbox is always **reactive**.
- It never opens automatically.
- It never sends messages without a user-initiated request.
- All proactive Mimi behavior occurs **outside** this chatbox (Guided Reflection, Pop Quiz).

## ****3.2 Guided Reflection Chatbox - Visual & Interaction Mechanics****

**Purpose**  
The Guided Reflection Chatbox is a **separate, scripted Mimi interface** used only during Guided Home Reflection. It delivers a linear, controlled interaction and replaces the Main Mimi Chatbox entirely while active. It is proactive.

### ****Visual form****

- Appears as a **chat panel** anchored to the centre of the reflection screen. It is the same width as the text card in the before and after sections.
- Within the main card are two speech bubbles with tails pointing at avatars.
  - The upper bubble belongs to Mimi, is green themed, and points to the Mimi avatar.
  - The lower bubble belongs to the learner, is blue themed, and points to the learner avatar selected on the student home screen.
- The Guided Reflection interface includes a text input. The Send button is positioned directly under the learner speech bubble, linking them visually. The End Mimi Reflection button is positioned bottom left, distinctly separate from the speech bubbles.
- The Main Mimi Chatbox is **not visible** while Guided Reflection is active.
- Only one Guided Reflection Chatbox instance may exist at a time.

### ****Activation****

- Guided Reflection is initiated **only** when the user clicks the Guided Home Reflection button located at the **end of the first section** of the Home Reflection screen.
- The chatbox opens automatically page scrolls down to it. User is presented with a fixed introduction instruction + the first script from the -reflection.json file.
- For the duration of the guided sequence, **all background page interaction is locked**. The Guided Reflection card is sized to fit fully within the viewport; **no scrolling is required or permitted**. The user may interact **only** with the Guided Reflection Chatbox controls (text input, Send button, End Mimi Reflection button).

### ****Modes****

- The screen has a different design and mechanic to the main mimi screen, with no ask button, no drop down mode selector.
- Ask Psych, Site Guide, Nav Guide, Topic Explanation, and Task Help are **not available**.
- All responses are constrained to the scripted reflection flow.

### ****Interaction mechanics****

- Interaction is **linear and step-based**.
- Mimi presents **one prompt at a time**
- Mimi presents prompts in a fixed sequence drawn from -reflection.json. The user is invited to give a typed response. Mimi responds to that through LLM, not the json.
- .The user may submit **one response per step**. User types response then clicks send:
  - Sends user response
  - clears mimi screen of existing text
- Blank responses are ignored, same as main mimi chatbox
- The Guided Reflection uses **two independent timers**: a **user inactivity timer** and an **LLM display timer**.
  - If the user submits no response and does not begin typing within **10 seconds** of a Mimi prompt, the **user inactivity timer fires** and the flow **immediately advances to the next scripted Mimi prompt**, bypassing the LLM step entirely. Any learner text is cleared.
  - If the user begins typing but becomes inactive for **10 seconds** at any point before clicking Send, the **user inactivity timer fires** and the flow **immediately advances to the next scripted Mimi prompt**, bypassing the LLM step entirely. Any learner text is cleared.
- While a response is being processed **or while any Guided Reflection timer is active** (user inactivity timer or LLM display timer):
  - The text input and Send button is disabled.
  - The End Mimi Reflection button is **disabled whenever user input is disabled**, and enabled whenever user input is enabled.
- LLM mechanic. In alpha any response is accepted. Once it is sent Mimi generate a relevant LLM response in the mimi bubble. When an LLM response is displayed, the **LLM display timer** starts. The LLM response remains visible for **10 seconds**, after which it is automatically replaced by the next scripted Mimi prompt. The learner response remains visible until the next scripted prompt appears, at which point it is cleared.
- The cycle continues until the last script. After LLM responds to the user text mimi closes with a scripted end comment and instruction to click on End Reflection button and start the next section of reflection - learn_hr (after)

### ****Retry & correction rules****

- Guided Reflection follows the global alpha rule: **one response per step**. There are no retries, corrections, or follow-up questions in alpha.
- Mimi accepts the learner's response as-is and advances the flow according to timers and scripted progression.

### ****Completion & exit****

- Guided Reflection ends with a **final Mimi handover message**.
- After user clicks on End Mimi Reflection button
  - The reflection screen remains visible but is locked and no longer interactive.
  - The next section of Home Reflection (learn_hr - after) is revealed, containing the quiz.
  - The background page is reactivated so the user may interact with the next section or leave the page.
  - The guided flow cannot be restarted in the same session. The user must leave the lesson ecosystem or restart the app for Guided Reflection to reset.

### ****Disablement / locking rules****

- While Guided Reflection is active:
  - The background screen is disabled,
  - The Main Mimi Chatbox is fully disabled.

### ****Proactivity rule****

- Guided Reflection and pop quiz are the **only proactive Mimi chat interfaces**
- All prompts during Guided Reflection are system-initiated.

## ****3.3 Pop Quiz Panel - Visual & Interaction Mechanics (Baseline)****

**Purpose**  
Pop Quiz is a proactive recall check that appears on **nav screens only**. It is a separate panel (not inside Mimi chat) and is not user-selectable as a mode.

### ****Visual form****

- Pop Quiz renders as a **centered modal panel** (role="dialog", aria-label="Pop Quiz"), shown/hidden using aria-hidden. No scrolling (overflow:hidden).
- Visual styling: white panel, **2px black border**, **16px radius**, drop shadow.
- Header: rainbow gradient bar with a pill label "Pop Quiz".
- Body structure:
  - Prompt line: "Can you remember what you learned?"
  - Question card (#pmPqQuestion).
  - 4 vertical answer buttons A-D (button.pm-pq-choice) each with a letter pill + text span.
  - Feedback area (.pm-pq-feedback) hidden until answered.
  - "Click to close chat" button (.pm-pq-closechat) hidden until answered.
- Accessibility: option buttons and the Close Pop Quiz button show a 4px focus outline when focused within the Pop Quiz panel.

### ****Availability****

- The Pop Quiz panel container is created **only when** page_type === "nav".

### ****Activation****

- Pop Quiz is proactive. The panel is opened by logic (not user click).
- On nav screen entry, a **15-second timer** runs. Timer starts as soon as nav screen opens. When it fires:
  - If Mimi panel is visible, Pop Quiz is **queued**.
  - Otherwise Pop Quiz **opens immediately**.

### ****Active-state locking (while Pop Quiz is open)****

- When Pop Quiz opens, it creates a full-screen transparent interaction blocker that blocks all page interaction except the Pop Quiz panel. Scrolling, keyboard navigation, and focus outside the Pop Quiz panel are disabled.
- Z-index layering is forced so the blocker sits above everything and the Pop Quiz panel sits above the blocker.

### ****Question source & loading****

- Pop Quiz questions are loaded from a lesson-specific \*-popquiz.json file

### ****Question selection (anti-repeat)****

- Pop Quiz presents one question per appearance. Questions do not repeat within a session for the same unit and lesson.
- When no unseen questions remain for the current unit and lesson, Pop Quiz stops appearing for that session.

### ****Answering & grading mechanics****

- **One attempt only.** Once an answer is chosen, all option buttons become disabled.
- Feedback appears after answering:
  - "Correct!" or "Not quite."
  - Plus an explanation from grading_explanation or a fallback showing the correct answer.
- The **Close Pop Quiz** button ("Click to close chat") becomes visible and enabled only after the learner submits an answer.

### ****Closing & cooldown****

- The Pop Quiz panel may be closed **only** by clicking the **Close Pop Quiz** button. No other close method is available.
- Closing hides the panel (aria-hidden="true") and removes the blocker.
- After close, a **120-second cooldown timer** runs. When it ends:
  - If Mimi panel is visible, Pop Quiz is **queued**.
  - Otherwise Pop Quiz **opens** again.
- Leaving the current nav screen resets both the entry timer and the cooldown timer.
- When the user enters a nav screen, a new entry timer starts immediately, regardless of prior Pop Quiz activity on other screens.

### ****Concurrency with Mimi panel****

- Mimi visibility is defined by #pmAiPanel\[aria-hidden="false"\]. Pop Quiz obeys a strict "never open while Mimi visible" rule via **queueing** (both on the initial 15s trigger and the post-close cooldown reopen).

## ****4\. AI Functions (SYSTEM-WIDE, backend-enforced)****

This design lock supports exactly seven AI functions  
No others are permitted.

- Ask Psych (general psychology questions)
- Topic Explanation
- **Task Help**
- Guided Home Reflection
- Pop Quiz
- Site Guide (Entry) (mode: site_guide)
- Nav Guide (In-lesson) (mode: nav_guide)

Any other function name or variant, or any unmapped mode, is invalid and must be rejected

Beta note - no change

## ****5\. Canonical Function → Mode Mapping****

- This mapping is the single source of truth for canonical AI function names and backend mode validation.
- Frontend UI exposure and initiation rules are defined separately and may further restrict what is visible or user-selectable.

| AI Function | mode |
| --- | --- |
| Ask Psych | ask_psych |
| Topic Explanation | explain_topic |
| **Task Help (rules and mechanics only)** | ask_task |
| Guided Home Reflection | hr_guided |
| Pop Quiz | pop_quiz |
| Site Guide (Entry) | site_guide |
| Nav Guide (In-lesson) | nav_guide |

**Rules: Any invented, unmapped, or page_type-invalid mode → 400**

**Beta note - no change**

## ****6\. Function Availability Matrix (CANONICAL) -****

- This table is the single source of truth for backend permission by page_type.
- Frontend UI exposure, initiation, and timing are governed by separate rules in this document.

| page_type | site_guide | nav_guide | explain_topic | ask_task | ask_psych | pop_quiz | hr_guided |
| --- | --- | --- | --- | --- | --- | --- | --- |
| entry | ✅   | ❌   | ❌   | ❌   | ❌   | ❌   | ❌   |
| nav | ❌   | ✅   | ❌   | ❌   | ✅   | ✅   | ❌   |
| learn_ls | ❌   | ❌   | ✅   | ❌   | ✅   | ❌   | ❌   |
| learn_hr (before HR starts) | ❌   | ❌   | ✅   | ❌   | ✅   | ❌   | ❌   |
| learn_hr (during Mimi-led HR) | ❌   | ❌   | ❌   | ❌   | ❌   | ❌   | ✅   |
| learn_hr (after HR ends) | ❌   | ❌   | ✅   | ❌   | ✅   | ❌   | ❌   |
| task | ❌   | ❌   | ✅   | ✅   | ❌   | ❌   | ❌   |

**UI exposure rule (binding):  
The availability matrix defines backend permission only. Pop Quiz must never be presented as a selectable UI mode on any screen (including nav). On nav screens, Pop Quiz is backend-permitted but may only be proactively initiated by Mimi, per Section 12 timing and lock rules.**

**Ask Psych on Lesson Summary Screens (learn_ls)**

**During alpha, all Ask Psych interactions on learn_ls are answered using general psychology knowledge only. Ask Psych does not draw from lesson summary JSON and does not function as Topic Explanation. Lesson structure affects Ask Psych availability and reset limits only (per revealed section), not the source or scope of responses.**

**Beta note:**

**Ask Psych on Lesson Summary Screens (learn_ls)**

**On lesson summary screens (**learn_ls**), user questions are routed by intent. If a question relates to the current lesson topic, Mimi must respond using Topic Explanation . If a question does not relate to the lesson topic, Mimi may answer it once as Ask Psych per revealed lesson section. After responding, Mimi must encourage the user to continue the lesson. The allowance resets only when the user reveals the next section.**

## ****7\. Folder structure****

powermind-ai-website/

│├── index.html ← launch screen

├── .gitignore

│

├── .netlify/

├── .state.json

├── blobs-serve/

├── v1/

│ └── functions/

│ └── functions-internal/

│

├── netlify/

│ └── functions/

│ └── powermind-ai.js ← AI backend endpoint

│

└── powermind/

│

├── index.html ← Student Home

├── curriculum-Y01.html ← Year 1 curriculum map

├── favicon.ico

├── manifest.webmanifest

├── service-worker.js

│

├── icons/

│

└── unit-01/

│ │

│ ├── screens/

│ │ ├── lesson-01.01.html to lesson-01.04.html ← Park

│ │ ├── ls-01.01.html to ls-01.04.html ← lesson summary

│ │ ├── hr-01.01.html to hr-01.04.html ← home reflection

│ │ ├── hg-01.01.html to hg-01.04.html ← activity hubs

│ │ └── icg-01.01.html to icg-01.04.html

│ │

│ ├── lesson-summary-task

│ │ ├── ls-01.01-psych-test.html to ls-01.04-psych-test.html ← ls- psych test game

│ │ └── ls-01.01-video01.html to ls-01.04-video01.html ← ls - video wrap

│ │

│ ├── home-game/

│ │ └── hg-01.04-game02.html ← tasks (games/quizzes)

│ │

│ └── in-class-activity/

│ ├── icg-01.01-game01.html

│ ├── icg-01.01-quiz01.html

│ ├── icg-01.01-rquiz01.html

│ ├── icg-01.04-game01.html

│ ├── icg-01.04-quiz01.html

│

├── ai-context/ ← ALL AI-readable content

│ └── site/

│ │ ├── site_guide.json ← guide outside lesson

│ │ ├── nav_guide.json ← guide inside lesson

│

│ └── unit-01/

│ └── lesson-summary/

│ │ ├── ls-01.01-summary.json ← summary of lesson

│ │ ├── ls-01.02-summary.json

│ │ ├── ls-01.03-summary.json

│ │ ├── ls-01.04-summary.json

│ │ ├── ls-01.01-popquiz.json ← 20 pop quiz questions

│ │ ├── ls-01.02-popquiz.json

│ │ ├── ls-01.03-popquiz.json

│ │ └── ls-01.04-popquiz.json

│ │

│ ├── home-reflection/

│ │ ├── hr-01.01-reflection.json ← mimi interactive reflection script

│ │ ├── hr-01.02-reflection.json

│ │ ├── hr-01.03-reflection.json

│ │ └── hr-01.04-reflection.json

│ │

│ └── task/

│ ├── icg-01.01-game01-gameflow.json ← game rules/procedure

│ ├── icg-01.01-quiz01-gameflow.json

│ ├── icg-01.01-rquiz01-gameflow.json

│ ├── icg-01.04-game01-gameflow.json

│ ├── icg-01.04-quiz01-gameflow.json

│ └── hg-01.04-game01-gameflow.json

├── assets/

│ ├── common/

│ │ ├── js/

│ │ │ ├── powermind-ai-widget.js

│

│ │ ├── images/

│ │ │ ├── powermind-logo.png

│ │ │ ├── mimi.webp

│ │ │ ├── index-back-portrait.png

│ │ │ ├── index-back-landscape.png

│ │ │ ├── lesson-background.png

│ │ │ └── \[UI icons, generic art\]

│ │ │

│ │ ├── audio/

│ │ ├── sfx/

│ │ └── fonts/

│ │

│ └── unit-01/

│ ├── screens/

│ │ ├── ls-01.01-video01.mp4 to ls-01.04-video01.mp4 ← video for ls screens

│ │ ├── ls-01.01-back.webp to ls-01.04-back.webp ← background images for ls screens

│ │ └── hr-01.01-back.webp to hr-01.04-back.webp ← background images for hr screens

│ │

│ ├── hg-01.04-game01/ ← tasks assets

│ ├── icg-01.04-game01/

│ ├── icg-01.04-quiz01/

│ ├── icg-01.01-game01/

│ ├── icg-01.01-quiz01/

│ └── icg-01.01-rquiz01/

│

## 8\. Site Guide - app entry guide only (site_guide.json)

### Purpose

- **The Site Guide helps the user move around the app before starting a lesson. It briefly explains what happens inside a lesson so the user knows what to expect, then nudges the user to start a lesson**
- **It gives an overview only and does not explain lesson content, activities, how to do tasks, or answer psychology questions.**
- Explain the overall purpose of the app
- Explains the structure of the login screens
- Gives a brief overview of how all activities - tasks (games, quizzes), lesson summaries, home reflection - take place in the lessons. And then encourage navigation to the lessons to play the app.
- Does not explain the details or function of any activities within the lesson structure.
- Explains how to leave the app and re-enter

### Allowed only on

- page_type: "entry"

### Mode

- site_guide

### Source constraints

- **Site Guide may draw content only from site_guide.json.**
- **location: powermind/ai-context/site/site_guide.json**
- **The site_guide.json file must include a metadata header declaring: schema_version, content_type:"site_guide", and page scope identifiers as defined in Section 13. Files missing required metadata are invalid and must not be loaded.**

****Meta Header****

{

"schema_version": "1.0",

"content_type": "site_guide",

"purpose": "Guide the learner from app entry to starting a lesson and explain, at a high level, what happens inside a lesson.",

### Response constraints

- **40-70 words**
- Short sentences
- Friendly, factual tone
- **One suggestion only**
- **Must end with a single click onto a specific lesson button, which exits entry and launches a lesson**

### Explicit exclusions

- Lesson teaching
- Psychology explanations
- explanation of the activities within the lesson structure, since this is handled by nav_guide. Can only give an overview and then encourage user to explore the lessons. It is a lead in to user progressing to the lessons.

## Beta note - no change

## ****9\. Nav Guide - in lesson guide (nav_guide.json)****

### Purpose

- **Guides the user inside the lesson structure, moving between lesson parks and activity hubs: (lesson summary, in-class activities, home games, home reflection). It also guides user within the stations - to the activity hubs (hg-01.01, icg-01.01).**

Answers:

- Where am I in the lesson structure?
- What are the options to do next?
- How do I get out of this lesson? And join another lesson. It does not explain how to leave the app
- Introduces the existence of Ask Psych and explains that Pop Quiz may appear automatically.

### Allowed only on

- page_type: "nav"

### Mode

- nav_guide

### What Nav Guide may do

- Identify the current hub/park and its role (e.g., lesson hub, activity hub).
- Point the user to the next appropriate page (moving between stations or between activities on a hub) within the lesson structure.
- Provide **one** clear navigation suggestion at a time.
- Indicates that Ask Psych and Pop Quiz exist on nav pages. **Ask Psych is user-initiated. Pop Quiz is Mimi-initiated, automatic, and must never be user-selectable or manually triggered.**
- Explains how to exit the current lesson and return to the curriculum to start another lesson

### Source constraints

- **Nav Guide may draw content only from nav_guide.json. The frontend must load nav_guide.json and include it in the backend request as context_json**
- **location: powermind/ai-context/site/nav_guide.json**

****Meta Header****

{

"schema_version": "1.0",

"content_type": "nav_guide",

"unit_id": "01",

"lesson_id": "01.01",

"purpose": "Guide the learner around lesson navigation screens and explain where to go next.",

### Response constraints

- 40-70 words
- Short sentences
- One suggestion only
- Must end with a click action (e.g., "Click \___.")

### Explicit exclusions

- Topic Explanation content (learn_ls, learn_hr).
- Psychology explanations or answers to psychology questions (these are handled only via Ask Psych).
- Explaining task rules or mechanics; gaming hints (ask_task).
- navigation outside the lesson (site_nav)

## Beta note -

1\. addition of station AI Tutor

## ****10\. Explain Topic (\*-summary.json)****

Explain Topic provides **science and concept explanations**, not task procedures or rules. It does not provide answers to general psychology questions that do not relate to the current lesson.

### Where allowed

- learn_ls
- task (very narrow - Game Science)
- learn_hr (hr_phase: "before" | "after" only)

### Scope and intent

Topic Explanation covers:

- Any psychology concepts related to the lesson summary
- The science **meaning of a task (game/quiz), or the purpose of the game in relation to the current lesson**
- Lesson summary should include a **clearly labeled "Game Science" section** for each game.

### Interaction limits

**In alpha, the 1-question rule applies across all AI modes, including Explain Topic.**

****On** learn_ls **and****

- On learn_ls: Lesson Summary screens follow a fixed, canonical structure shared by all lessons:
- **Text → Video → Text → Psychology Test → Text → Quiz**
- Each transition is initiated only by an explicit user button click. Each button-defined step constitutes one revealed lesson section for AI state tracking.
- lesson progress is indicated by user-activated buttons (Video, Psychology Test). Quiz section is revealed by return from psychology test. Quiz has it's own start function- clicking on 1 of the mcq answers. At the end of the quiz user can replay the quiz or exit to the park.
- In prototype - AI remembers only during the lesson session. The lesson session persists while the learner remains inside the current lesson ecosystem (lesson summary, park, hubs, tasks/games/quizzes, video, psychology test). The session resets only when the learner leaves the lesson ecosystem (e.g., returns to curriculum / exits to another lesson or unit) or closes the browser/tab. Page reloads do not reset the lesson session.
- The user may ask 1 **Topic Explanation questions per revealed section**.
- After each response, Mimi must encourage the user to **continue reading the lesson**.
- When the user reveals the next section, the question allowance resets for that new section.

****On** page_type:learn_hr (before and after only)**:****

- **Home Reflection has three phases: before, during, and after. Topic Explanation is permitted only during before and after phases. Each phase constitutes a distinct AI interaction state for tracking question limits.**
- **AI remembers only during the lesson session. The lesson session persists while the learner remains inside the current lesson ecosystem (lesson summary, park, hubs, tasks/games/quizzes, and home reflection). The session resets only when the learner leaves the lesson ecosystem (e.g., returns to curriculum / exits to another lesson or unit) or closes the browser/tab. Page reloads do not reset the lesson session.**
- **The user may ask 1 Topic Explanation question per phase ("before" or "after"). After each response, Mimi must encourage the learner to continue with the current Home Reflection section or proceed to the next section.**
- **When the learner transitions to a different hr_phase, the Topic Explanation question allowance resets.**
- **Topic Explanation is never available during hr_phase:"during", when Mimi is leading the guided reflection.**

****On** page_type:"task"**:****

- **Topic Explanation on task pages is permitted even if the learner is not currently on the lesson summary screen**
- The **lesson summary is the single source of truth**.
- Mimi must **preferentially draw from the "Game Science" section in \*-summary.json. R**esponses must remain limited to the relevant Game Science subsection.
- The user may ask **1** Topic Explanation question only.
- Mimi responds once, then encourages the user to **resume playing the game**.
- 1 new Topic Explanation question is permitted **only after the user has attempted further gameplay**.

### Source constraints

- Topic Explanation may draw content only from -summary.json (e.g., ls-01.01-summary.json).
- location: powermind/ai-context/unit-01/lesson-summary/-summary.json

****Metadata Header****

**All \*-summary.json files must include a metadata header with the following required fields:**

**{**

**"unit_id": "01",**

**"lesson_id": "01.01",**

**"topic": "How Our Minds Work",**

**"schema_version": "1.0",**

**"content_type": "explain_topic",**

### Explicit exclusions

- Psychology explanations that do not relate to the current lesson
- site or lesson navigation
- task rules or procedures

### Format

- 60-90 words
- Neutral instructional tone
- No personalization
- No hints or answer coaching

Beta note:

**1\. at least 2 learn_ls questions will be allowed - but after each response Mimi encourages user to continue lesson**

## ****11\. Task Help (\*-gameflow.json)****

Task Help is for a single purpose only: to support understanding **the overall procedure for playing a task (game/quiz) and its rules** . It does **not** explain the science or meaning of the task. Science explanations are handled via **Topic Explanation**.

### Allowed only on

- page_type:"task"

### Required fields

- Required fields (ask_task request payload)  
    • page_type: "task"  
    • mode: "ask_task"  
    • unit_id  
    • lesson_id  
    • screen_id  
    • task_id  
    • question  
    • task_intent (allowed values: "rules" | "idea")  
    • context_json (the loaded \*-gameflow.json)
- Task_type (e.g., game vs quiz) does not affect AI behavior in alpha. All tasks are handled uniformly via ask_task using \*-gameflow.json.

**Question handling**

- If the user asks a **general question** (e.g., "How do I play?" "What do I do?"), Mimi provides a **brief overall game overview**, covering the objective, controls, steps, and rules.
- If the user asks a **specific question** (e.g., "What does this button do?" "What happens if I choose this?"), Mimi explains **only the relevant rule or mechanic**, then encourages the user to continue playing.

### Scope

Task Help explains:

- Game overview
- Controls
- Steps
- Mechanics
- What actions do

Task Help must **not** include:

- Strategy
- Tips or "How to win"

### Interaction rules

- Mimi provides 1 **rules explanation**.
- Mimi must then encourage the user to **try or continue playing the game**.
- A new Task Help request is permitted **only after the user has attempted gameplay**.
- This cycle may repeat: 1 explain → play → 1 explain.

### Source constraints

- The frontend must load the corresponding \*-gameflow.json file and include it in the backend request as context_json.  
    Task Help responses must be generated using that -gameflow.json as the sole authoritative source.
- For example: hg-01.04-game01-gameflow.json
- location: powermind/ai-context/unit-01/task/\*-gameflow.json

**Metadata header (ask_task)**

All \*-gameflow.json files must include a metadata header with the following required fields:

{

"schema_version": "string",

"content_type": "ask_task",

"unit_id": "string",

"lesson_id": "string",

"task_id": "string",

"topic": "string"

}

Files missing required fields or with a mismatched content_type are invalid and must not be loaded.

**Task intent routing (alpha)**

- For page_type:"task" and mode:"ask_task", the request may include task_intent.
- Allowed values: "rules" | "idea".
- task_intent is set by the frontend using a simple heuristic:
  - - "rules" for questions about controls, steps, buttons, how to play, what to do next
  - - "idea" for questions about what the activity means or what it is about (still within task scope)
- If task_intent is missing, the backend must infer it safely and still remain inside Task Help scope

### Enforcement

Backend must reject:

- - Any ask_task request missing task_id
    - Any ask_task request missing question
- Any request missing required fields or using invalid fiel ds for routing or permission enforcement must be rejected (HTTP 400).
- Additional non-routing fields must be ignored in alpha.

Beta note - no change

## ****12\. Ask Psychology - general psychology interface (through open AI)****

### Purpose

**Reactively responds to users general questions about psychology.**

Answers:

- safe general questions about psychology
- strict guardrails must limit question topics. If a question indicates potential harm or distress, Mimi must provide a brief safety-oriented response and redirect the user to continue the lesson or navigation; no advice or intervention is permitted.

**Required request metadata (ask_psych)**

Ask Psych requests must include the following required fields:

- page_type
- mode: "ask_psych"
- unit_id
- lesson_id
- screen_id
- question

Ask Psych must never include context_json.

Requests missing required fields or using an incorrect mode must be rejected.

**Interaction limits**

In alpha, Ask Psych allows only 1 question at a time. Reset conditions depend on page_type:

- learn_ls
  - One Ask Psych question is allowed per revealed lesson section.
  - The allowance resets only when the learner reveals the next lesson section.
- learn_hr (hr_phase: "before" or "after")
  - One Ask Psych question is allowed per phase state.
  - The allowance resets only when the learner transitions to a different hr_phase.
- nav
  - One Ask Psych question is allowed per nav screen instance.
  - The allowance resets only when the learner navigates away from the current nav screen (to any other screen).
- **In alpha, this rule is enforced both frontend-side and backend-side. The frontend prevents repeat Ask Psych requests within the current scope; the backend remains the authoritative enforcement layer.**

### Allowed only on

- page_type: "nav"
- page_type: "learn_ls" (per interaction limits)
- page_type: "learn_hr" (hr_phase: "before" | "after" only; never during hr_guided)

### Mode

- ask_psych

### What Ask Psychology may do

- **On nav pages, Ask Psych does not distinguish between general psychology questions and lesson-related questions.**
- **All Ask Psych questions are answered using general psychology knowledge only, without lesson-specific grounding.**
- Ask Psych must remain:
  - Non-diagnostic
  - Non-therapeutic
  - Non-personalized
  - use psychology as science language

**Source selection:**

- In all cases, the interaction remains **Ask Psych** (not Topic Explanation) and counts toward the 1 **question limit**.
- Ask Psych must never receive or use context_json; it operates without any local content source.

### Response constraints

- Responses are **one short paragraph** in a **neutral teacher tone**, framed as **psychology as a science**.
- The response **acknowledges the question and explains a general psychology concept** in simple, factual terms.
- **No therapy, no diagnosis, no personal advice.**
- **No follow-up questions.**
- **No lists.**
- Length is **best-effort short (about 40-70 words)** and may include **at most one neutral learning suggestion**.
- **After answering the question Mimi must encourage the learner to continue the current activity. If at the end of current activity encourage to start a new activity.**

### Explicit exclusions

- Site or lesson navigation
- explaining task rules or mechanics; gaming hints
- **Ask Psych is not allowed on task screens or during the Mimi-guided phase of home reflection.**

## **Beta note**

1\. On nav, if the question relates to the current lesson topic, Mimi must answer using lesson summary content. Not by Ask Psych

2\. On learn_ls, lesson-related questions must be handled as Topic Explanation, not by Ask Psych.

3\. the user may ask 2 questions; after each response Mimi encourages the user to return to their current activity.

Guard Rails - text

instruction =

"You are in Ask Psych mode for a kids psychology learning app. " +

"Teach psychology strictly as a science (not SEL). " +

'EVERY answer must begin with a phrase like "In psychology," or "In the science of psychology,". ' +

"Use this structure: " +

"(1) what psychologists often observe, " +

"(2) a simple, evidence-based explanation, " +

"(3) optionally one short, concrete example. " +

"Use clear, everyday words suitable for an average 8-year-old. " +

"Avoid SEL-style, emotional coaching, or therapeutic language. " +

"Be neutral and factual. " +

"Do NOT give advice, coping steps, diagnosis, or instructions for what someone should do. " +

"Do NOT coach on lessons, tasks, or navigation. " +

"Keep it short: 3-5 simple sentences. " +

"If the question asks what someone should do or is too personal, respond instead with: " +

'"I can explain how this works in general, but I can't tell someone what to do personally."';

## 13\. Home Reflection - Mimi-Guided Activity (\*-reflection.json)

**Purpose**  
Home Reflection is one of **only two locations** in the system where Mimi may lead a **scripted, linear interaction** and proactively present prompts.

This behavior applies only to page_type:"learn_hr".

### Guided Flow (Linear, Mimi-Led)

The Home Reflection flow is strictly linear and session-bound and is delivered through a **dedicated Guided Reflection chat panel**, not the main Mimi chatbox.

**Entry**

- The user clicks **Start Reflection (with Mimi)**.
- A **Guided Reflection chat panel** opens
- the background page is disabled, including mimi button

**Interaction**

- Mimi presents the first scripted prompt automatically (no user question).
- The learner responds to each prompt in turn.
- Mimi uses LLM to give a relevant response
- The flow repeats prompt → response → feedback until the scripted sequence completes.

**Completion and transition**

- At handover, Mimi presents a final message, instructing user to click on end reflection button.
- When learner clicks **End Mimi Guided Reflection**.
  - The Guided Reflection panel closes.
  - The system transitions to learn_hr hr_phase:"after".
  - All features of background page are activated - including mimi avatar

**Session rule**

- The guided reflection cannot be restarted within the same **lesson session**.
- A lesson session persists while the learner remains inside the current lesson ecosystem (lesson screens, park/hub, tasks/games/quizzes, and home reflection).
- The session resets only when the learner leaves the lesson ecosystem or closes the browser/tab. Page reloads do not reset the lesson session.
- If the learner clicks **End Mimi Guided Reflection** at any time during hr_guided , hr_guided is permanently completed for that lesson session and cannot be re-entered.

### Home Reflection Phases (Canonical)

Home Reflection has **three explicit phases**:

- BEFORE - before the guided flow starts
- DURING - while Mimi is actively leading the scripted flow
- AFTER - after the handover message, when the learner clicks Close chat and the quiz section is revealed

Backend enforcement of these phases requires an explicit request field.

****Required field on all** learn_hr **requests:****

hr_phase: "before" | "during" | "after"

If hr_phase is missing or invalid, the backend **must return HTTP 400**.

### Availability & Gating (Canonical)

**Ask Psych and Explain Topic interaction limit**

- During both hr_phase: "before" and hr_phase: "after": Ask Psych and Explain Topic allows only 1 question per mode. The allowance resets only when the learner transitions to a different hr_phase.
- After one question in a mode, that mode must become visibly unavailable to the learner until hr_phase changes:
  - Remain visible in the interface
  - Be visually distinct from active modes (e.g. muted / greyed / locked state)

**When page_type:"learn_hr":**

#### hr_phase: "before"

**Allowed (200):**

- explain_topic
- ask_psych

**Rejected (400):**

- site_guide, nav_guide, ask_task, pop_quiz, hr_guided

source constraint:

- Topic Explanation may draw content **only** from \***\-summary.json, for example ls-01.01-summary.json**
- **location: powermind/ai-context/unit-01/lesson-summary/\*-summary.json**

#### hr_phase: "during"

**Allowed (200):**

- hr_guided

**Rejected (400):**

- explain_topic, site_guide, nav_guide, ask_psych, ask_task, pop_quiz

**source constraint:**

- Mimi Guided Reflection may draw content **only** from \***\-reflection.json, for example hr-01.01-reflection.json**
- **When** context_json **is present,** hr_guided **responses must be generated using the corresponding** \*-reflection.json **as the sole authoritative source.**
- **location: powermind/ai-context/unit-01/home-reflection/\*-reflection.json**

****metadata header (hr_guided)**.**

- **"schema_version": "1.0"**
- **"content_type": "hr_guided"**

**Additional constraints during** hr_guided**:**

- No off-script proactive behavior
- Mimi may deliver **only** the next scripted prompt

#### hr_phase: "after"

**Allowed (200):**

- explain_topic
- ask_psych

**Rejected (400):**

- site_guide, nav_guide, ask_task, pop_quiz, hr_guided

source constraint:

- Topic Explanation may draw content **only** from \***\-summary.json, for example ls-01.01-summary.json**
- **location: powermind/ai-context/unit-01/lesson-summary/\*-summary.json**

### Frontend / UX Responsibilities (Non-blocking)

- The frontend controls when the guided flow starts and ends.
- The frontend sets hr_phase on each request.
- The backend does **not** infer phase from timing, content, or navigation history.
- After quiz handover, Mimi must only respond to **user-initiated** requests permitted by the matrix.

## 14\. Pop Quiz (\*-popquiz.json)

**Purpose**  
Pop Quiz is a **proactive recall check** that tests learner understanding of topics from the **current lesson**. It draws questions from \*-popquiz.json. These are mcq style questions with 4 answer options. Uses a dedicated UI layout distinct from other modes while remaining within the nav screen context.

### Availability (Canonical)

**Allowed only when:**

- page_type: "nav"
- Never allowed on: entry, learn_ls, learn_hr, task

In version **alpha**, Pop Quiz is **not an AI mode** and **does not use** mode: "pop_quiz". Pop Quiz is implemented as a **separate, non-AI panel**, loading questions from \*-popquiz.json and grading deterministically on the client. **No backend (**powermind-ai**) calls are permitted for Pop Quiz in alpha.**

### Mode

- \*-popquiz.json is the **single source of truth**
- In alpha, Pop Quiz is **not an AI mode** and does **not** use mode: "pop_quiz". Pop Quiz is implemented as a **separate, non-AI frontend panel**, triggered by Mimi's proactive timing logic on page_type: "nav" screens.
- No backend (powermind-ai) calls are permitted for Pop Quiz in alpha.
- The identifier pop_quiz is **reserved for beta only** and must not be sent as a mode in alpha requests.

### Source Constraints

- Pop Quiz content may draw **only** from \*-popquiz.json files. For example ls-01.01-popquiz.json
- location: powermind/ai-context/unit-01/lesson-summary/\*-popquiz.json
- No other content sources are permitted.
- Pop quiz can use any of the questions in \*-popquiz.json.

**Meta Data**

{

"schema_version": "1.0",

"content_type": "pop_quiz",

"unit_id": "01",

"lesson_id": "01.01"

}

**Timing & Presentation (Frontend / UX Rules - non-binding on backend)**

These rules govern **when** Pop Quiz may appear but **do not affect backend request validity** unless explicitly implemented server-side.

- The 15-second timer starts immediately on nav screen entry and continues to run regardless of Mimi visibility.
- **When user stays on the same nav screen:** after the learner clicks **"Click to close chat"**, start a **2-minute cooldown timer before a new pop quiz question is asked**
- **State reset rule: all Pop Quiz timers reset on leaving the current nav screen or closing the app.**

### Active-State Lock (Frontend / UX)

- Pop Quiz must never interrupt user-initiated interactions. The only blocking interactions are: Mimi - Navigation help; Mimi - Ask Psych
- Pop Quiz must never appear while the **Mimi panel is visible on screen**. If the Pop Quiz trigger time occurs while the Mimi panel is open, Pop Quiz must be **queued. It then shows immediately when the Mimi panel is closed.**.

**Definition:**  
Mimi is considered active **only when its panel is visible**. No other UI state is considered blocking for Pop Quiz.

## Beta note

1\. **Availability (Beta - Reserved)**

- mode: "pop_quiz" is **reserved for beta only** (e.g., AI-graded short answers).
- UI remains a **separate Pop Quiz panel** (never inside Mimi chat).

Pop Quiz is **never user-selectable**.

2\. questions types will be a mix of mcq and short answer questions. Questions are categorized to the sections in the related lesson summary.

3\. mimi can only ask questions related to the sections of the lesson summary that user has revealed. Pop quiz will remain deactivated until user goes into lesson summary.

## 15\. Content Sources (System-Wide)

### Scope (System-Wide Only)

This section defines rules that apply to **all AI functionality**, across **all modes and page types**.  
Mode-specific behavior and permissions are defined **only** in Sections 10-14 and must not be duplicated here.

### Source Authority Rule

Mimi may draw content **only** from explicitly permitted sources, and **only** for their permitted purpose.  
Any use of a source outside its defined purpose is disallowed.

### Request Validity (System-Wide)

Requests missing required fields, using an invalid page_type, or using an invalid mode must be rejected (HTTP 400).

### Missing / Unloadable Context File Rule (System-Wide)

If a local context JSON file is missing, unloadable, or fails validation, the request must proceed **without** context_json.  
There must be **no UI break** and **no user-visible error**.

### Local JSON Context Transfer (Frontend → Backend)

For any mode that has a canonical local JSON source, the frontend must:

- Load the corresponding JSON file
- Attach its contents to the backend request as a single field named context_json

If the file does not exist or fails to load, the request must proceed without context_json.  
No other request fields are altered.

### Context JSON Validation (System-Wide)

When context_json is present, the frontend must validate that:

- The file parses as JSON
- The root value is a JSON object
- schema_version is present and is a string
- content_type matches the expected type for the active mode

If validation fails, the request must proceed without context_json (no UI break, no user-visible error).

### Canonical Content Ownership (No Duplication)

Lesson science or concept content must not be duplicated across multiple sources.

For lesson topics, **lesson summary (**\*-summary.json**) is the single source of truth**.  
Other sources may reference lesson concepts **only as already defined** in the lesson summary and must not introduce new instructional content.

## **16\. Backend Enforcement**

Backend must reject with **400** when:

- page_type missing or invalid
- mode missing or invalid
- Mode used outside allowed page type
- page_type:"task" missing task_id
- Any request missing required question field
- Pop Quiz used outside mode:"pop_quiz"
- Pop_Quiz used outside page_type:"nav"
- Task Help outside ask_task
- Nav Guide outside nav
- Site Guide outside entry
- Any topic explanation request **must use mode** explain_topic. Requests attempting topic explanation with any other mode **must return HTTP 400**.
- Guided Home Reflection outside hr_guided
- ask_psych outside nav, learn_ls, or learn_hr (hr_phase:"before" | "after")
- ask_psych sent during learn_hr hr_phase:"during"
- If context_json is present on an ask_psych request:
  - Backend must ignore it (do not use it for generation)
  - Do not reject the request for this reason.