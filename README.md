# DreamTale – Make Your Own Dream World

DreamTale is a creative mobile application that allows users to build and explore their own imaginary worlds using Artificial Intelligence.  
Instead of consuming static stories, users actively design worlds, create characters, and influence evolving storylines that grow over time.

---

## 📌 Project Overview

- **Project Type:** Mobile Application  
- **Platform:** Cross-platform (Android & iOS)  
- **Experience:** Single-user interactive storytelling  
- **Content Type:** AI-generated text-based narratives  

DreamTale generates daily story events based on user-defined world rules, characters, and prior story context, creating a living and evolving narrative experience.

---

## 🎯 Core Features (Planned)

- World creation with custom rules and themes  
- Character creation and progression  
- Daily AI-generated story updates  
- User intervention in story flow  
- Chronological story timeline  
- Secure authentication and user-specific data isolation  

---

## 🧱 System Architecture (High Level)

- **Frontend:** Flutter mobile application  
- **Backend:** Supabase (Authentication + PostgreSQL database)  
- **AI Service:** OpenAI API for story generation  

All frontend and application logic is developed locally on team members' machines.  
Supabase and OpenAI are used as managed cloud services.

---

## 🗂️ Repository Structure

```text
dreamtale/
│
├── frontend/        # Flutter mobile application
├── backend/         # Supabase configuration and AI logic
├── docs/            # Project documentation and guidelines
├── .github/         # GitHub workflows
└── README.md
```

---

## 🛠️ Tools & Technologies

- Flutter & Dart
- Supabase (Backend-as-a-Service)
- OpenAI API
- GitHub (Version Control)
- Jira (Project Management)
- Visual Studio Code (IDE)

---

## 📋 Version Control & Jira Guidelines

Detailed rules for **branch naming**, **Jira integration**, and **pull request workflows**
are documented separately for clarity and formal evaluation.

📄 **Read full guidelines here:**  
➡️ [Version Control, Branch Naming & Jira Integration Guidelines](/docs/version-control-guidelines.md)

This document defines:

- Branch naming formats and enforcement
- Jira–GitHub traceability rules
- Pull request and review policies
- Sprint merge and release flow

---

## 🔄 Development Workflow

### Branch Strategy

**main**

- Stable and protected branch
- Contains only sprint-complete verified code
- Merged only at the end of each sprint
- Merge performed only by the Team Lead

**dev**

- Active development branch
- Base branch for all feature branches
- All completed work is merged here first

All development work is done on feature branches created from `dev`.
At the end of each sprint, `dev` is reviewed and merged into `main`.

---

## 📅 Sprint Plan (Summary)

- **Sprint 1:** Project setup, planning, tooling, documentation
- **Sprint 2:** Backend schema design, authentication, core UI flows
- **Sprint 3:** AI integration and dynamic story generation

---

## 👥 Team

**Group 4 – DreamTale**

- Lovepreet Singh Virdi – Team Lead
- Kamraan Ahmed
- Monisha Thandavamoorthy
- Tusharbir Singh Mutty
- Dipesh Raj Joshi

---

## 🔐 Security & Best Practices

- API keys managed via environment variables
- No secrets committed to GitHub
- Shared Supabase project used by the entire team
- Supabase Row Level Security (RLS) planned for user-level data isolation

---

## 📌 Current Status

Project is currently in **Sprint 1 (Planning & Setup Phase)**.

---

## 📬 Contact

For project coordination or queries, please contact:

**Lovepreet Singh Virdi**  
Team Lead – DreamTale Project