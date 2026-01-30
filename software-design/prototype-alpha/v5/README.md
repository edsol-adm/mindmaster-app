# Prototype Alpha-05 — Addition of User Dashboards and associated functionalities

🌐 Web app: https://powermind-ai.com

For all user types login with:
username: powermind
password: powermind

## What Alpha-05 Builds On

The project is in alpha stage: core architecture and most of the major features are set. The application is viable - we are testing its consistency and establishing a structure for scalability. Alpha-05 builds directly onto **Prototype Alpha-04**. As with previous Alphas, Unit-01 is a model for all 10 units. In Alpha-04 the unit-01 ecosystem comprised:

- Access through a fully functioning PWA enabled web app
- Navigation and admin ecosystem. Login, student dashboard, curriculum (showing 10 units with 4 lessons per unit)
- Lesson ecosystem. 4 lesson hubs, designed as a park with stations around it. Each station provides user activities: lesson-summary; in-class-activities; home-games; home-reflection; AI-tutor (currently redundant), and a proactively launched Pop Quiz.
- Lesson-summary provides a summary of the in-class-lesson. For in-class students this can be revision. For home users it provides essential learning to enable them to productively navigate the other stations. Features: includes a summary of the lesson; a psychology video related to the lesson topic; a psychology test conducted through powermind; a lesson knowledge quiz with gamified formats.
- In-class-activities: 1 clickable powermind game that students used in class; a variable number of gamified quizzes.
- Home-games: 2 powermind games
- Mimi AI functionality with 6 different modes on 7 different page types - site entry/admin screens navigation guide; lesson ecosytem navigation guide; topic explanations available on lesson summary, home reflection and within games (strictly limited to game science); game rules and navigation within gamified activities; a proactively guided home reflection; an Ask Psychology function to ask general psychology questions, which is available on lesson summary and home reflection screens, and on the lesson ecosystem navigation screens.
- With the introduction of AI the app introduces a personalized learning experience for users.

---

## Purpose of Alpha-05

Prototype Alpha-05 extends the Alpha phase to incorporate an admin management function and testing functionalities.

The purpose of Alpha-05 is to assess:

- 3 dashboard types - student (enhanced from alpha-04), teacher, edsol-admin. The teacher and edsol-admin dashboards are designed to be easily adapted for school-admin and donor dashboards.
- a per level pre and post test. The test is designed to assess the overal psychology literacy of users, linked to their development through engagement with powermind-ai app. This is an important global assessment as increased Psychology Literacy is linked to strengthened Mental Resilience, a core goal of the app. This is a teacher or Mimi guided activity.
- Unit completion tests - tests are designed to narrowly test the users knowledge of a completed unit. This is a teacher or Mimi guided activity.
- A teacher resource function. On the teacher dashboard a teacher may access lesson plans, worksheets. This function is scalable to add additional resources.
- A user registration function. On the edsol-admin dashboard the administrator can create new schools and classrooms. They can then add a group of students to a class. Or add individual students to an existing class. Dummy data (code embedded) is used in Alpha-05. In Alpha-06 a live PostgreSQL database will be added and dummy data from this will be used to replace the code enmbedded data. This will allow addition of real data to the app in subsequent alphas.
- Level structure is introduced for the first time. Each year grade comprises 2 levels - for in-class users this will equate to a semester (6 months).
- Sample games for all units of Grade 01 are added, which includes navigation screens neccessary for accessing the games.

---

## Alpha-05 Known Limitations

- Functionality at scale.
- Does not aim to validate learning or behavioral outcomes.
- No dummy or real student data in a database for display of performance analytics - by school, class, student. Alpha-06 will integrate a live PostgreSQL database.
- Simpicity of games and other gamified learning activities.
- Simplicity of learning screens (Lesson Summary, Home Reflection)
- Limits on AI training, accuracy, records by design. With functionality demonstrated AI can be scaled, accuracy refined, testing with larger cohorts over extended period of time. Folowing this, recording of user interaction will be meaninful and provide a foundation for further refinement of AI capability.
- Refinement of navigation screens and process.

These limitations are expected and acceptable within Alpha.

---

## Details of new features and functionality in Alpha-05

### 1. Dashboards

- Student dashboard. The existing dashboard had minimal design changes implemented. This screen requires further enhancement. 2 tests have been added to the dashboard - pre/post test psychology literacy test; unit-completion test
- Teacher dashboard.the dashboard is in 2 sections. Left - function buttons: lesson resources, powermind classroom (Access to the curriculum and lesson resources), automated psychology literacy test generator, automated progress report generator. The latter is currently disabled. Right - a user analysis display. Teacher selects school, class or individual student from a drop down which then populates the analytics measures for the group.
- Edsol-admin dashboard. Essentially the same screen as for the teacher dashboard. The dropdown list has a donor dropdown list added. And there is an additional user registration button which launches the user registration screen.

---

### 2. Pre/Post Test - Psychology Literacy Test

Normally pre and post tests are designed to confine assessment to a body of knowledge being taught. In the case of powermind that would be to a single level of study, or 5 units. However, this test aims to assess progress in broader terms, while still linking the test to the 5 units studied.

- The test assessment model changes through all 6 years of the powermind curriculum, adjusted for the additional knowledge users are exposed to through studying the units of study in powermind-ai.
- Assessment of psyhcology literacy starts pre level 01. For this a model has been designed which aims to replicate the psychological understanding of an average child of 5 years age. The model is defined in terms of 20 psychological skills (for example problem solving, emotional management, handling mistakes). The aim is not to assess the child's psychology. But rather, their understanding of the psychological skill in an objective manner, founded on psychology as science. For example, "What is an effective way to respond when someone is angry?" Not, "How would you respond if someone got angry?"
- The post test for level 01 is based on the same "Average Child" model but is modified to take account of their exposure to the level 01 course of powermind (unit 01 to 05). The new model aims to simulate a more advanced understanding only of the psychology skills taught in level 01. These skills only represent a compontent of the model, and so the test is a broader assessment of the psychology literacy of the student. And so captures any progress gained through the personalized learning experience gained by users of powermind-ai through engagement with AI through Ask Psych, Explain Topic, Home Reflection.
- The pre test "Average Child" model for level 02 is the same as the model for post test level 01. Post test level 02 is modified to take account of their exposure to the level 02 course of powermind (unit 06 to 10). In this way a complete suite of tests can be developed for all 6 year grades.
- in Alpha-05 the test is launched from student dashboard. In later alphas the test will be auto generated by the teacher and then launched on the screens of selected students.

---

### 3. Unit Completion Test

This test is an academic test of the student's understanding of what they learned in the unit.

- On the student dashboard users launch the test, displaying a screen with only 2 dropdown menus to select year grade and unit.
- The user is instructed to confirm this selection and then the test starts
- the test comprises 10 questions drawn randomly from a library of 20 questions. The questions use a variety of 10 gamified quiz formats. One question is displayed at a time and the correct answer is displayed at the end of the test.
- in Alpha-05 the test is launched from student dashboard. In later alphas the test will be auto generated by the teacher and then launched on the screens of selected students.

---

### 4. Teacher Resource Function

- The resource is accessed by clicking on a button on the teacher dashboard
- Teachers can then access in pdf format lesson plans, and lesson worksheets.
- For Alpha-05 resources are limited to unit-01. Later alphas will add additional resources. For example, activity stimulants - images of different facial expressions singifying different emotions.

---

## 5. User registration function

This screen is only accessible from the edsol-admin dashboard. It's purpose is to enable Edsol administrators to add new individual students to an existing class, or create new classes and then populate them with the students. On completion students are registered to use the application. They are provided with personalized login credentials which will direct them on login to the student dashboard. From here they access the lesson ecosystem through the curriculum page.

- From drop downs admin selects an existing school and class. They may also create new schools and classes.
- With a class selected admin assigns a teacher to the class.
- And then adds new students individually or by class.
- Each record records user credentials (for students, their unique student ID), first and last name, auto generated username and password.
- Edsol admin liases with school admin during app deployment, providing them with login details for all new students. In this way students are registered to use the app

---

## 6. Addition of home games for units 02 to 10

- navigation screens for lessons 01 and 02 for units 02 to 10 are added, to allow navigation to games in units 02 to 10.
- 1 or 2 home games are added to demonstrate the viability of meaningful pedagogy for all unit topics. In total 11 home games are added.

---

## What Alpha-05 Does _Not_ Test

- Learning outcomes - short or long term
- Behavioural outcomes - particularly change in mental resilience
- Platform stability at scale
- Performance measurement and record - test results, record of qualitative and quantitative interaction with Mimi AI
- Classroom synchronisation or multi-user management
- AI personalisation - the AI Tutor (personalized topic review lessons) function is still disabled in Alpha-04

These areas are intentionally deferred to later phases.

---

## Testing Approach in Alpha-05

Testing is **exploratory and observational**, focusing on:

- System usability, correct functionality and stability under live delivery conditions as a PWA enabled web app
- functionality and unsability of the user dashboard types
- functionality and usability of the tests
- functionality and usability of the user registration function

Testing outputs are captured through:

- System-level observation
- Iteration notes documenting design decisions
- Controlled synthesis of feedback

No raw learner data is collected or retained.

---

## Summary - Alpha-05

Prototype Alpha-05 represents an extension of the Alpha phase into teacher and administration management, with the introduction of 3 separate logins and their associated dashboards. These allow the introduction of a teacher resources hub and a student registration function.

2 student testing capabilities have been added - Unit Tests, Psychology Literacy pre and post tests.

Furthermore, there is a limited extension of the app beyond the unit 01 main testing ecosystem, by the introduction of 11 home games in units 02 to 10.

In the next alpha a live PostgreSQL database will be added which in alpha will be populated with dummy data. This will be used to test several functionalities

- Recording Qualitative and quantitative student performance data.
- Recording student, teacher, edsol-admin, school-admin, donor personal credentials in order to test selected login functionality
- analytics display, accuracy.

