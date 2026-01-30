# Prototype Alpha 04 — System Integration Validation (PWA + 5 AI Modes)

🌐 Web app: https://powermind-ai.com

## What Alpha-04 Builds On

The project is in alpha stage: core architecture and most of the major features are set. The application is viable - we are testing its consistency and establishing a structure for scalability. Alpha-04 builds directly onto **Prototype Alpha-03**. As with previous Alphas, Unit-01 is a model for all 10 units. The unit-01 ecosystem comprises:

- Navigation and admin ecosystem. Login, student dashboard, curriculum (showing 10 units with 4 lessons per unit)
- Lesson ecosystem. 4 lesson hubs, designed as a park with stations around it. Each station provides user activities: lesson-summary; in-class-activities; home-games; home-reflection; AI-tutor (currently redundant)
- Lesson-summary provides a summary of the in-class-lesson. For in-class students this can be revision. For home users it provides essential learning to enable them to productively navigate the other stations. Features: includes a summary of the lesson; a psychology video related to the lesson topic; a psychology test conducted through powermind; a lesson knowledge quiz with gamified formats.
- In-class-activities: 1 clickable powermind game that students used in class; a variable number of gamified quizzes.
- Home-games: 2 powermind games
- Home-reflection: the reflection activity is related to the lesson. It requires interaction by student, ideally suited for engagement with AI.

Alpha-03 formally closed the **learning-engine validation phase**.  
Alpha-04 introduces **system-level risks** for controlled validation.

---

## Purpose of Alpha-04

Prototype Alpha-04 extends the Alpha phase to validate **the web application**, following the successful completion of Alpha-03, which confirmed the viability of the core learning engine.

The purpose of Alpha-04 is to test:

- Whether the PowerMind learning experience remains usable and coherent when delivered as a **Progressive Web App (PWA)**
- **Several modes of reactive freeform conversational AI (Ask_Psych, Explain_Topic). A more tightly governed, reactive non-conversational AI component (Site_Guide). And a proactive, scripted conversation for the home reflection activity (Learn_hr).** Typed interaction takes place through a chatbox. Page types are used to define what modes are available - on some only a single mode is available; on others 2 modes can be selected via a dropdown menu in the chatbox. Limiting the number of allowed questions per mode avoids disrupting learner engagement with other app activities. While the introduction of AI introduces a personalized learning experience - particularly through Explain Topic, Ask Psych and the Guided Home Reflection.
- A proactive pop up (single question) quiz to test knowledge about the lesson topic. This is displayed only when users are on a lesson ecosystem navigation screen, and has a cooldown timer to ensure users are not put off by or distracted by the pop up.

---

## Alpha-04 Known Limitations

- Functionality at scale.
- Does not aim to validate learning or behavioral outcomes.
- No dummy or real student data in a database for display of performance analytics - by school, class, student. Alpha-06 will integrate a live PostgreSQL database.
- Simpicity of games and other gamified learning activities.
- Simplicity of learning screens (Lesson Summary, Home Reflection)
- Limits on AI training, accuracy, data recording by design. With functionality demonstrated AI can be scaled, accuracy refined, testing with larger cohorts over extended period of time. Folowing this, recording of user interaction will be meaninful and provide a foundation for further refinement of AI capability.
- Refinement of navigation screens and process.

These limitations are expected and acceptable within Alpha.

---

## Details of new features and functionality in Alpha-04

### 1. Live Platform Delivery (PWA)

Alpha-04 introduces delivery through a **live web platform**, implemented as a Progressive Web App, to assess:

- Whether navigation and learning flow remain clear when accessed via a browser-installed environment
- Whether delivery constraints interfere with instructional intent
- Whether session handling and navigation feel predictable to users

The PWA implementation is **fully functional for unit-01** and is treated strictly as an Alpha artefact. Since the structure and functionality of unit 02 to unit 10 is identical, PWA scalability is demonstrated, but has yet to be tested.

---

### 2. AI Functionality (6 modes) - Mimi AI

Alpha-04 introduces a **tightly governed AI component** designed to support learning _without_ acting as a therapist, coach, or autonomous agent. AI access is provided through a mode/page type matrix of 7 page types and 6 modes. Its role is strictly limited to 2 functions:

- to assist in site and gamified activity navigation
- to provide information (freeform or context-bound) of psychology as science.

AI functionality is strictly constrained to:

- Context-bound explanations, including in freeform Learn_Hr and Ask_Psych modes. Responses will be refined through in-house and live testing.
- Clear response safeguards in both reactive and proactive modes. Responses will be refined through in-house and live testing.
- In Alpha-04 user is limited to 1 question per mode. To ask another question they take action related to the page. For example, navigate to another page, open a new section of the lesson summary, or interact with a game. Alpha-04 is coded so that in beta question number can be varied by mode. For example, user might be allowed 2 or 3 questions on ask_psych; on site_guide user might remain limited to 1 question before being encouraged to explore the app.

Mimi AI access and interface

- On every page is a clickable Mimi gif style avatar which launches the Mimi chatbox, disabling all other functions while it is on the screen.
- The chatbox comprises a centered card with 3 elements:
  - when there is more than one moder available on the screen a dropdown menu offers the available modes.
  - a text editor in which user types their question
  - a response box in which Mimi AI responds to user question

Modes:

- site_guide. Reactive mode. Site Navigation outside the lesson ecosystem. Only available on site navigation and admin screens. No other modes are available on these screens. Response is drawn from a site and admin navigation json.
- nav_guide. Reactive mode. Navigation within the lesson ecosystem on the lesson stations screen (lesson summary page, in-class acitivies, home games, home reflection page). And on the home and in-class activity hub screens, which provide access to the games and gamified activities. On these screens nav_guide and ask_psych are available. Response is drawn from a lesson ecosystem navigation json.
- explain_topic. Reactive mode. User can ask questions specifically about the lesson topic. This mode is available on lesson summary and home reflection screens. And is also available on the game screens, strictly limited to questions related to the science related to the game activity. Response is drawn from a lesson summary json.
- ask_task. Reactive mode. User can get advice on the game rules and game navigation. It does not provide advice on game performance. Response is drawn from a gameflow json.
- ask_psych. Reactive mode. User can ask any psychology as science related questions. Freeform response is sourced through openAI. This mode is strictly guardrailed to comply with psychology as science constraints. And is limited to psychology topics appropriate for powermind-ai.com users.
- hr_guided. Proactive mode. On the home reflection screen Mimi launches a scripted chat on the reflection topic. Each script invites user to reflect on lesson related concept. Mimi then sources a freeform response through openAI which interacts to the user's response. The aim is to simulate reflection by the user guided by Mimi. The same guardrails are used as for ask_psych.

AI implementation is **fully functional for unit-01** and is treated strictly as an Alpha artefact. Since the structure and functionality of unit 02 to unit 10 is identical, AI scalability is demonstrated, but has yet to be tested.

---

### 3. Mimi Pop up Quiz

- The pop up quiz only appears on lesson ecosystem navigation screens. It is not AI controlled.
- Each lesson has a json file with a library of 25 questions related to the lesson content.
- A single question is randomly selected and presented proactively on a card with 4 MCQ options. After user click on answer the correct answer + explanation is displayed.
- A timer initiates the first appearance of the card, and a cooldown timer delays presentation of subsequent questions. The aim is that only 1 question should ever appear on a nav screen, and not on every screen as the user navigates around the lesson ecosystem.

---

### 4. Unit-Level Flow (Unit-01)

Alpha-04 tests the **end-to-end flow** of **Unit-01** as a live web app. Units 02 to 10 have identical internal structure. With Unit-01 functioning, Alpha-04 demonstrates scalability.

- Transitions between screens and activities in a lesson and the site entry/admin ecosystems. Both within a single lesson and between lessons in Unit-01
- For each lesson ensure pedagogical coherence between lesson summary, home reflection and gamified activities.

Alpha-04 evaluates **system coherence** and **unit pedagogical coherence** across unit-01. It does not validate curriculum coherence across all 10 units.

---

## 5. Addition of login screens

There is now a login screen with 3 login cards:

- Student - active
- Teacher: inactive in Alph-04
- EdSol Admin - inactive in Alph-04

For all user types login with:
username: powermind
password: powermind

---

## 6. Session recall in lesson ecosystem

- While users remain in the same lesson level the app remembers session status in every screen and activity.
- Session resets only when user leaves the lesson ecosystem to the navigation ecosystem and then returns to the same or another lesson.

---

## What Alpha-04 Does _Not_ Test

- Learning outcomes - short or long term
- Behavioural outcomes - particularly change in mental resilience
- Platform stability at scale
- Performance measurement and record - test results, record of qualitative and quantitative interaction with Mimi AI
- Classroom synchronisation or multi-user management
- AI personalisation - the AI Tutor (personalized topic review lessons) function is still disabled in Alpha-04

These areas are intentionally deferred to later phases.

---

## Testing Approach in Alpha-04

Testing is **exploratory and observational**, focusing on:

- System usability, correct functionality and stability under live delivery conditions as a PWA enabled web app
- AI functionality and baseline accuracy
  - reactive and proactive modes function correctly and on the correct page types. And limitations apply correctly and consistently across modes and page types
  - Whether Mimi AI remains within its defined pedagogical instruction and site navigation roles.
  - Whether learners correctly understand what Mimi AI is for in all modes
  - Whether Mimi AI provides a more immersive and individualized learning experience.
  - Whether AI behaviour aligns with **psychology literacy principles**, not SEL or counselling models.

Testing outputs are captured through:

- System-level observation
- Iteration notes documenting design decisions
- Controlled synthesis of feedback

No raw learner data is collected or retained.

---

## Summary

Prototype Alpha-04 represents an extension of the Alpha phase into a functioning and scalable platform as a live web application. It can be launched both on PC and on smartphone or tablet through a live PWA.

Through integration of AI a more immersive user experience is added. One that offers a wider variety of pedagogy functions. It also introduces an individualized and organic learning experience for students through 3 modes of AI - Explain Topic (explain lesson topics or game science), Ask Psych (a freeform conversation on any approved psychology topic), and Mimi Home Reflection (a freeform conversation related to a specific reflection activity or topic).
