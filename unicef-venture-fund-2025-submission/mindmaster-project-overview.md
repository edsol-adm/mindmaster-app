# MindMaster: Strengthening Mental Resilience Through Teaching Psychology Literacy

### 📘 About This Document  
This README provides an overview of the **MindMaster** project, including its purpose, target users, core features, technical stack, development roadmap, and contribution guidelines. The project is designed in alignment with **UNICEF’s priorities** in gender equity, digital inclusion, and mental health support for marginalised children—especially girls and children in remote areas.

---

## 🌱 Purpose

MindMaster develops psychological literacy, promotes emotional wellbeing and mastery, and mental resilience among children aged 5–12. By combining technology with evidence-based pedagogy, the platform supports early intervention and lifelong mental health awareness.

The solution is intentionally designed to serve girls and marginalised children who often face systemic barriers to mental health support. To address the digital divide, MindMaster operates in both **online and offline modes**—using **Local Server Deployment** technology to function without internet access. This ensures children—especially girls in marginalised and remote communities—can benefit from quality digital learning environments, regardless of infrastructure limitations. The platform supports caregivers, educators, and humanitarian organisations in nurturing emotional growth with tools that are inclusive, adaptable, and community-ready.

---

## 🚧 MindMaster Development Stages

MindMaster follows a modular and iterative development process, underpinned by a Rapid Application Development (RAD) approach. The initial focus is **Module 1: Psychology Literacy for Primary Grade 1**, delivered in **English with Thai translation overlay**.

### Phase 1: Curriculum Roadmap & Content Design  
- Define the Grade 1–6 psychology literacy framework  
- Develop complete content for Grade 1, including instructional design and learning objectives

### Phase 2: Prototype Development & Pilot – Isolated Feature Validation  
- Build and test core features (home and learner modules) with limited users  
- Gather early feedback to validate usability and learning impact  
- Optimise for offline-first deployment in low-connectivity contexts

### Phase 3: Full Solution Pilot – Thai Context, English Content  
- Deploy the full Grade 1 module (English with Thai overlay) in 10 pilot classrooms  
- Monitor usage, learning outcomes, and engagement through analytics and observation  
- Collect feedback via pre-post testing, interviews, surveys, and classroom visits  
- Refine UX and content for readiness to scale

### Phase 4: Evaluation & Consolidation  
- Document learnings and refine implementation toolkit  
- Position for scale-up in Thai and ethnic minority contexts  
- Prepare for Khmer localisation to expand to Cambodian learners

---

## 👩‍🏫 Target Audience

- **Girls in Primary Year Grades 1–6** in underserved and marginalised communities, including rural, migrant, and low-income settings, who face unequal access to mental health and educational resources  
- **Children of all genders** at the beginning of education at primary level, particularly those at risk of exclusion, trauma, or psychosocial stress  
- **Educators, school counsellors, and frontline workers** delivering SEL and gender-responsive mental health programmes in low-resource environments  
- **NGOs, development agencies, and CBOs** working at the intersection of gender equity, education, and child mental wellbeing  
- **Parents and caregivers**, particularly women and female guardians, seeking practical tools to support children’s emotional growth at home  
- **Children with disabilities** and those from minority language communities, aligning with UNICEF’s localisation and accessibility priorities  

---

## 🎯 Main App Features

- 🧠 **Psychology Literacy Learning Platform**  
  An AI-powered digital platform featuring **GPT-4 chatbot tutoring**, gamified lessons, interactive activities, short videos, journaling tools, mindfulness prompts, and self-check exercises—designed to develop foundational psychological literacy and resilience.

- 📊 **Assessment & Progress Tracking**  
  Embedded formative assessments and real-time analytics enable personalised learning pathways and measure individual progress across core emotional and psychological competencies.

- 🧑‍🏫 **Teacher Assistant Platform (TAP)**  
  An educator-facing interface with lesson guides, student performance dashboards, and offline-capable materials that support delivery in diverse, resource-limited classrooms.

- 🌐 **Multilingual Localisation & Offline-First Architecture**  
  The system is multilingual-ready and built to operate in **low-resource environments** via local server deployment (mini PCs with daily cloud sync), ensuring continuous access in areas with poor or no internet connectivity.

---

## 🛠️ Tech Stack

- **Frontend:** React.js + Framer Motion (for responsive, animated UI)  
- **Backend:** Node.js + Express.js  
- **Databases:** PostgreSQL (student progress), Redis (gamified scoring & session cache)  
- **Authentication:** JWT-based (offline-compatible)  
- **Infrastructure:**  
  - Docker + Docker Compose (for local mini-PC and cloud deployment)  
  - NGINX (serving frontend assets)  
  - Rsync or PouchDB/CouchDB (for cloud-local DB syncing)  
  - Supports local deployments on mini PCs - Intel NUC  

---

## 🤝 Contributing

MindMaster is open source because equitable access to mental health tools is a global priority. We welcome contributions in:

- ✨ Frontend and backend development  
- 🌍 Localisation and translation  
- 📘 Educational content co-design  
- 🧪 Usability and accessibility testing  
- 📊 Data privacy and safeguarding enhancements  

To contribute:  
1. Fork this repository  
2. Create a feature branch (`git checkout -b feature-xyz`)  
3. Submit a pull request with a detailed description  
4. Or open an issue to propose a change or feature  

All contributions must align with ethical standards and UNICEF’s digital safeguarding principles.

---

## 📄 License

This project is licensed under the **MIT License**.  
See the `LICENSE` file for full terms and permissions.

> 🔐 **Note:** All data-handling components are designed with privacy, security, and user control at the core—especially for young users.

---

**Developed by EdSol Technology (Thailand) Co., Ltd.**  
*Empowering learners with digital tools to deal with everyday psychological challenges effectively.*
