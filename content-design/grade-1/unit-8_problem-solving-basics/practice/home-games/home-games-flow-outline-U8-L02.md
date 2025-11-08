# MindMaster Grade 1 – Unit 8: Problem-Solving Basics
**Home Game Flow Outline – Lesson 2: Steps for Solving Problems**

---

## Table of Contents
- [Home Game 2A – Step Quest: The Four-Path Adventure](#home-game-2a--step-quest-the-four-path-adventure)
- [Home Game 2B – Pattern Problem Solver: Simon Says Steps](#home-game-2b--pattern-problem-solver-simon-says-steps)
- [How Lesson 2 Fits into the Full Learning Arc](#how-lesson-2-fits-into-the-full-learning-arc)

---

## Home Game 2A – Step Quest: The Four-Path Adventure
> Jump to: [Setup](#setup) · [Play](#play) · [Scoring](#scoring) · [Win Condition](#win-condition) · [Continuity Note](#continuity-note)

### Learning Objective
Students learn and apply the four-step problem-solving framework: Stop and Notice → Think of Options → Choose One → Try It Out. They understand that following a process makes problem-solving feel less overwhelming.

### Game File Name & Format
`hg-08.02-01.html` — Interactive Fiction / Branching Narrative

### Game Purpose
Apply the four-step problem-solving model in engaging narrative contexts. Players experience how each step influences the next and how following the process leads to better outcomes than skipping steps or rushing to action.

### Estimated Play Time
10–12 minutes (3 quests × 3–4 minutes each, including reading and decision time)

---

### Setup
**Opening Screen:**
- Title: "Step Quest: The Four-Path Adventure"
- Background: Storybook-style illustration showing a path through a colorful forest
- Character introduction: Meet Quest Hero Quinn (cartoon child adventurer with map and compass)
- Instructions: "You're on an adventure! When problems appear, you'll need to use the Four Steps to solve them. Every choice you make matters!"
- Four Steps reminder (scrollable reference, accessible anytime):
  - 🛑 Stop and Notice — See the problem clearly  
  - 💭 Think of Options — Imagine different ideas  
  - ✓ Choose One — Pick the best idea  
  - 🎯 Try It Out — Do it and see what happens
- Button: "Begin Quest" → starts story

**UI Elements:**
- Story Text Display (center): Narrative text appears here with illustrations
- Choice Buttons (bottom): 2–3 options appear at decision points
- Quest Progress (top): Shows which step player is currently on (🛑💭✓🎯)
- Path Gems (top right): "Path Gems: 0/20"
- "Step Guide" button (always accessible): Opens reminder of four steps

---

### Play
**Story Structure (3 complete quests, each with 4-step decisions):**

#### QUEST 1: The Bridge Problem
**Story Setup:** "You're walking through the forest when you reach a bridge. Oh no! Part of the bridge is broken. You need to cross to continue your adventure."

**Step 1 — Stop and Notice:**
- Text: "What do you do first?"
- Choice A: "Rush across the bridge quickly!" (impulsive—skips noticing)
- Choice B: "Stop and look at the bridge carefully to see what's wrong." (correct—Stop and Notice)
- Choice C: "Turn around and give up." (avoidance)

**Feedback & Branch:**
- Choice B selected: "Good! You STOPPED and NOTICED: three planks are missing in the middle. Now you can think of solutions!" → Earn 2 Path Gems → Continue to Step 2
- Choice A or C: "Wait! Before acting, it helps to STOP and NOTICE the problem first. Let's try again." → Show correct observation → Earn 1 Path Gem → Continue to Step 2

**Step 2 — Think of Options:**
- Text: "You see the missing planks. What could you do?"
- Choice A: "Look for a different way across (maybe stones in the water)." (good option)
- Choice B: "Find wood to repair the bridge." (good option)
- Choice C: "Jump over the gap." (risky but creative)
- Choice D: "Call for help from someone nearby." (good option)
- Player can select one option (or game could allow selecting multiple to show brainstorming, then move forward with one)

**Feedback & Branch:**
- Any reasonable option selected: "Great THINKING! You imagined different solutions. Now let's CHOOSE one." → Earn 2 Path Gems → Continue to Step 3
- If risky option: "That's creative! A bit risky though. Let's think about which option is safest." → Earn 1 Path Gem → Continue to Step 3

**Step 3 — Choose One:**
- Text: "You thought of several options. Which ONE will you try first?"
- Display the option(s) from Step 2
- Player selects one

**Feedback & Branch:**
- Player chooses: "You CHOSE: [their option]. Now let's TRY IT OUT and see what happens!" → Earn 2 Path Gems → Continue to Step 4

**Step 4 — Try It Out:**
- Animation/Illustration shows Quinn attempting the chosen solution
- Outcome varies by choice:
  - Find stones path: "You carefully step on stones across the stream. Success! You made it across safely!"
  - Repair bridge: "You find some planks nearby and fix the bridge. Now it's safe for everyone!"
  - Call for help: "A friendly forest ranger appears and helps you cross safely!"
  - Jump (if chosen): "You jumped, but it was scary! You made it, but next time a safer plan might work better."
- Feedback: "You TRIED IT OUT! The four steps helped you solve the problem." → Earn 2 Path Gems
- Quest 1 Complete! → Display: "Bridge Problem Solved! You used all Four Steps!"

---

#### QUEST 2: The Lost Pet Problem
**Story Setup:** "You arrive in a village. A child is crying because their pet bunny hopped away and is now lost in the village square where many people are walking."

**Step 1 — Stop and Notice:**
- Choice A: "Stop and ask the child: 'What does your bunny look like?'" (correct—gathering info)
- Choice B: "Run around randomly looking." (skips noticing)
- Choice C: "Tell the child to stop crying." (dismissive)
- Feedback: Choice A earns 2 gems and continues; others redirect with 1 gem.

**Step 2 — Think of Options:**
- Choice A: "Look under benches and bushes."
- Choice B: "Ask other villagers if they saw the bunny."
- Choice C: "Listen for bunny sounds."
- Choice D: "Make a 'Lost Bunny' announcement."
- Feedback: All reasonable → 2 gems. Player selects one to move forward.

**Step 3 — Choose One:**
- Player confirms their choice from Step 2.
- Earn 2 gems.

**Step 4 — Try It Out:**
- Outcome animation based on choice:
  - Look under bushes: "You find the bunny hiding under a bench! The child is so happy!"
  - Ask villagers: "Someone points you to where they saw the bunny! You find it!"
  - Listen for sounds: "You hear a soft sound and find the bunny near a garden!"
  - Make announcement: "Everyone helps look, and soon the bunny is found!"
- Earn 2 gems.
- Quest 2 Complete!

---

#### QUEST 3: The Teamwork Problem
**Story Setup:** "Your quest group has three adventurers (including you). You find a treasure chest that needs three different keys to open. Each adventurer has one key, but you all want to open the chest at different times."

**Step 1 — Stop and Notice:**
- Choice A: "Grab the chest and try to open it yourself." (skips noticing the team aspect)
- Choice B: "Stop and notice: We each have one key, but we need all three at once." (correct)
- Feedback: Choice B → 2 gems. Choice A redirects with reminder about noticing the full problem.

**Step 2 — Think of Options:**
- Choice A: "Everyone use their key at the same time."
- Choice B: "Take turns trying each key separately."
- Choice C: "Work together to figure out which order the keys go in."
- Feedback: Choices A and C are optimal (teamwork-focused) → 2 gems. Choice B shows less teamwork → 1 gem.

**Step 3 — Choose One:**
- Player selects best teamwork approach.
- Earn 2 gems.

**Step 4 — Try It Out:**
- Animation: All three adventurers work together, inserting keys simultaneously or in sequence.
- "The treasure chest opens! Inside is a golden medal that says: 'Best Problem-Solvers!' You all solved it together using the Four Steps!"
- Earn 2 gems.
- Quest 3 Complete!

**Final Story Screen:**  
"Your adventure is complete! You solved THREE problems using the Four Steps every time. You're now a Step Quest Master!"

---

### Scoring
**Path Gem System:**
- 2 Gems per optimal step choice (8 gems per quest × 3 quests = 24 gems possible)
- 1 Gem for learning attempts or suboptimal choices
- **Bonus Gems:**
  - Perfect Path (+4 gems): Make optimal choices on all four steps in at least one quest
  - Step Master (+3 gems): Complete all three quests
  - Scientific Thinker (+2 gems): Select "Think of Options" carefully at least twice (tracked if player spends time considering before choosing)
- **Maximum possible:** 24 gems (optimal path) + 9 bonus gems = 33 gems total  
- **Minimum possible:** 12 gems (all learning attempts) + 3 bonus (completion) = 15 gems

Display: Path Gems counter updates after each step. Visual gem trail appears along the story path illustration.

---

### Win Condition
**Completion:** Player completes all three quests (each using all four steps) and receives "Step Quest Master Medal"

**Medal Screen:**
- Quest Hero Quinn: "You collected [X] Path Gems on your adventure! You've mastered the Four Steps!"
- Visual: Medal showing the four step symbols (🛑💭✓🎯) with gem count
- Hero Title:
  - 28+ gems = ⭐⭐⭐ Grand Step Master (gold medal)
  - 22–27 gems = ⭐⭐ Skilled Step User (silver medal)
  - Below 22 = ⭐ Quest Learner (bronze medal, with encouragement: "Every adventurer learns by practicing the steps!")
- Story Summary: Final screen shows all three problems solved with illustrations
- Replay Option: "New Adventure" button → replays with slightly different story details or problem scenarios

**Navigation:**
- "Return to Home Games" button → links to `hg-08.02.html`
- "Return to Lesson" button → links to `lesson-08.02.html`

---

### Continuity Note
This game transforms Lesson 2's four-step framework into an engaging narrative experience. By making consequential choices at each step, players internalize the sequence and understand why each step matters. The branching structure shows cause-effect relationships between steps—skipping "Stop and Notice" leads to confusion, while following all four steps leads to success. This prepares players for Lesson 3, where they'll dive deeper into Step 2 (Think of Options) by generating multiple creative solutions.

[⬆ Back to TOC](#table-of-contents)

---

## Home Game 2B – Pattern Problem Solver: Simon Says Steps
> Jump to: [Setup](#setup-1) · [Play](#play-1) · [Scoring](#scoring-1) · [Win Condition](#win-condition-1) · [Continuity Note](#continuity-note-1)

### Learning Objective
Students apply the four-step model to solve simple problems and recognize that the goal is to have a plan to try, not to find a perfect answer immediately.

### Game File Name & Format
`hg-08.02-02.html` — Simon Says / Repeat the Pattern

### Game Purpose
Reinforce automatic recall of the four-step sequence through pattern repetition. Players internalize the order of steps by watching and repeating, building muscle memory and procedural knowledge.

### Estimated Play Time
8–10 minutes (45–60 seconds per round × 10 rounds)

---

### Setup
**Opening Screen:**
- Title: "Pattern Problem Solver: Simon Says Steps"
- Background: Colorful game show stage with four large step buttons
- Character introduction: Meet Pattern Master Pax (cartoon child game show host with microphone)
- Instructions: "Watch carefully! I'll show you how to solve a problem using the Four Steps. Then YOU repeat the pattern by pressing the steps in the same order!"
- Four Step Buttons displayed (center stage, large and colorful):
  - 🛑 STOP & NOTICE (red button)
  - 💭 THINK OPTIONS (blue button)
  - ✓ CHOOSE ONE (yellow button)
  - 🎯 TRY IT OUT (green button)
- Button: "Start Game Show!" → begins tutorial

**Tutorial (20 seconds):**
- Pattern Master Pax: "I'll press the steps to solve a problem. Watch my pattern, then copy it exactly!"
- Demo: Pax presses all four buttons in order: 🛑 → 💭 → ✓ → 🎯 (each lights up and makes sound)
- "Now YOU try! Press them in the same order."
- Player presses buttons; gets immediate feedback
- "Perfect! That's how the game works. Ready for real problems?"
- Button: "Let's Play!" → starts Round 1

**UI Elements:**
- Four Step Buttons (center): Large, clickable, with visual feedback when pressed
- Problem Display (top): Shows current problem scenario
- Round Counter (top left): "Round 1 of 10"
- Star Score (top right): "Stars: 0"
- Lives/Chances (bottom): Three hearts (❤️❤️❤️) — lose one for major errors

---

### Play
**Gameplay Loop (10 rounds, increasing difficulty):**

#### ROUNDS 1–3: Basic Pattern (4 steps)
**Round Structure:**
- **Problem Presentation:**
  - Pattern Master Pax announces a problem (text + simple illustration)
  - Examples:
    - Round 1: "Problem: You want to play with a toy, but your friend is using it."
    - Round 2: "Problem: You can't find your shoes before going outside."
    - Round 3: "Problem: Your snack fell on the floor."
- **Watch Phase:**
  - Pax: "Watch how I solve this problem using the Four Steps!"
  - Demonstration: The four buttons light up in sequence with narration:
    - 🛑 Lights up: "First, I STOP and NOTICE: My friend has the toy."
    - 💭 Lights up: "Then I THINK OF OPTIONS: Ask to share, wait my turn, play something else."
    - ✓ Lights up: "Next I CHOOSE ONE: I'll ask to take turns."
    - 🎯 Lights up: "Finally, I TRY IT OUT: I ask my friend!"
  - Each button glows and makes a distinct tone (musical notes: C-D-E-F)
  - Pattern completes, buttons reset
- **Repeat Phase:**
  - Pax: "Now YOU repeat the pattern! Press the steps in order."
  - All four buttons are now clickable
  - Player Task: Click the four buttons in correct order (🛑 → 💭 → ✓ → 🎯)
  - **Real-time Feedback:**
    - Correct button: Lights up, plays tone, stays lit
    - Wrong button: Button shakes, makes "error" sound (gentle, not harsh)
  - Player must complete all four in sequence
- **Round Completion Feedback:**
  - Perfect (no errors): "Perfect Pattern! You followed all Four Steps!" → Earn 3 Stars ⭐⭐⭐
  - Minor mistakes (1–2 wrong presses): "Good job! You got the pattern with a few tries." → Earn 2 Stars ⭐⭐
  - Several tries needed: "You figured it out! Keep practicing the pattern." → Earn 1 Star ⭐
  - Failed after many attempts: Pax shows the sequence again, player earns 1 Star for effort
- **Scientific Frame Reinforcement:**
  - After Round 3: "Notice: the same four steps work for EVERY problem. The pattern stays the same!"

---

#### ROUNDS 4–6: Partial Pattern Recognition
**Variation:** Pax only highlights SOME steps, player must complete the full sequence  
**Example Round 4:**
- Problem: "You and your sibling both want to watch different shows."
- Pax: "I'll start the pattern. You finish it!"
- Watch Phase: Pax presses 🛑 and 💭 (first two steps)
- Repeat Phase: Player must press ALL four steps in order (🛑 → 💭 → ✓ → 🎯)
- Tests whether player has internalized the full sequence
- Scoring same as Rounds 1–3

---

#### ROUNDS 7–9: Speed Challenge
**Variation:** Player must repeat the pattern within a time limit  
**Example Round 7:**
- Problem: "You're trying to build something but it keeps falling apart."
- Pax demonstrates all four steps (normal speed)
- Repeat Phase: "Quick! Repeat the pattern in 15 seconds!"
- Timer appears, counts down
- Bonus Star: If completed within time limit → +1 Bonus Star ⭐
- Regular scoring still applies

---

#### ROUND 10: Master Challenge
**Final Round:**
- Problem: "Your friend group can't agree on which game to play at recess."
- Pax: "This is the MASTER challenge! I'll show the pattern once. Then repeat it perfectly for bonus stars!"
- Watch Phase: All four steps demonstrated (slightly faster pace)
- Repeat Phase: Player must complete with no errors
- **Master Bonus:** Perfect completion → +5 Bonus Stars ⭐⭐⭐⭐⭐
- If mistakes made: regular scoring applies (1–3 stars)

---

### Scoring
**Star System:**
- 3 Stars per round: Perfect pattern repetition (no errors)
- 2 Stars per round: Good repetition (1–2 minor errors)
- 1 Star per round: Completed with help or multiple tries
- **Bonus Stars:**
  - Speed Challenge Bonus: +1 star per round (Rounds 7–9) if completed within time
  - Master Challenge Bonus: +5 stars if Round 10 perfect
  - Perfect Game Bonus: +5 stars if all 10 rounds completed with 3 stars each  
- **Maximum possible:** 30 stars (10 rounds × 3 stars) + 3 speed bonuses + 5 master bonus + 5 perfect game = 43 stars total  
- **Minimum possible:** 10 stars (all rounds completed with 1 star each)

Display: Star counter updates after each round. Stars cascade down screen with sparkle effect.

---

### Win Condition
**Completion:** Player completes all 10 rounds and receives "Pattern Problem Solver Champion Trophy"

**Trophy Screen:**
- Pattern Master Pax: "Amazing! You earned [X] stars! You've mastered the Four-Step Pattern!"
- Visual: Trophy showing the four step buttons in sequence with star count
- Champion Title:
  - 38+ stars = ⭐⭐⭐ Grand Pattern Champion (gold trophy with confetti)
  - 28–37 stars = ⭐⭐ Pattern Master (silver trophy)
  - Below 28 = ⭐ Pattern Learner (bronze trophy, with encouragement: "Keep practicing! Your brain is learning the pattern!")
- Pattern Mastery Certificate: Shows player successfully used the four-step pattern 10 times
- Replay Option: "Play Again" button → restart with different problems

**Navigation:**
- "Return to Home Games" button → links to `hg-08.02.html`
- "Return to Lesson" button → links to `lesson-08.02.html`

---

### Continuity Note
This game uses a different learning modality (pattern memory and repetition) to reinforce the same four-step sequence from Lesson 2 and Game 2A. By watching, listening, and physically repeating the pattern, players build procedural memory that makes the framework automatic. The Simon Says format is engaging and game-like while drilling the core sequence. This strong foundation prepares players for Lesson 3, where they'll expand their creativity within Step 2 (Think of Options).

[⬆ Back to TOC](#table-of-contents)

---

## How Lesson 2 Fits into the Full Learning Arc

Lesson 2 transforms the understanding from Lesson 1—*that problems are normal*—into a structured, actionable process for solving them. It introduces the **four-step framework** (Stop and Notice → Think of Options → Choose One → Try It Out) that becomes the mental backbone for all later problem-solving activities. Through narrative and pattern-based play, students move from simply *recognising problems* to *engaging with them systematically*, discovering that structure brings calm and clarity when situations feel tricky.

- **Lesson 1:** Normalises problems as everyday experiences and establishes the mindset that challenges are opportunities for the mind to work.  
- **Lesson 2 (this lesson):** Builds a reliable process—teaching students to pause, think, decide, and act through a clear step-by-step framework.  
- **Lesson 3:** Deepens flexible thinking within the second step ("Think of Options"), encouraging creativity and comparison of multiple solutions.  
- **Lesson 4:** Develops persistence and help-seeking, showing that successful problem-solving often means trying again and drawing on others’ support.

> 🧭 **Learning Arc Summary:** From *Noticing Problems* → *Following Steps* → *Thinking Flexibly* → *Persisting and Seeking Help.*  
> Lesson 2 marks the pivotal shift from awareness to agency—students begin to experience problem-solving as a repeatable mental process they can control, forming the bridge between understanding a problem and confidently tackling it.

---

*Document version: Lesson 2 only (Home Games 2A & 2B)*  
*For cross-unit alignment and quick navigation to all game flow outlines, see the [Home Games Overview](../README.md) in the `practice/home-games` directory.*
```markdown
