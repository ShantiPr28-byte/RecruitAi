# 🎯 RecruitAi — AI-Powered Campus Recruitment Platform

<div align="center">

![RecruitAi Banner](https://img.shields.io/badge/RecruitAi-AI%20Recruitment%20Platform-00d4aa?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Live-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)

**A full-stack intelligent campus placement management system built with Spring Boot & vanilla JavaScript**

🌐 [Live Demo](https://recruitai-pu35.onrender.com)

</div>

---

## 📌 About

**RecruitAi** is a comprehensive campus recruitment platform that streamlines the entire placement process — from student registration and job applications to recruiter approvals and placement tracking.

It connects **three types of users**:
- 🎓 **Students** — Apply for jobs, track application status, access courses & mock interviews
- 🏢 **Recruiters** — Post jobs, manage applicants, shortlist & select candidates
- 🏫 **College Admin** — Oversee all placements, manage recruiters, track placement stats

---

## ✨ Features

### 🎓 Student Portal
- Register and build a complete profile (branch, CGPA, skills, resume)
- Browse and apply for active job postings
- Real-time application status tracking (Applied → Shortlisted → Interview → Selected)
- Access learning courses and mock interview resources
- Placement status dashboard

### 🏢 Recruiter Portal
- Company profile management
- Post detailed job listings with eligibility criteria
- Auto-shortlist eligible students based on CGPA and branch
- Manage applicants — shortlist, interview, select or reject
- Create coding tests for candidates
- View test results and performance

### 🏫 Admin Portal
- Full student management with detailed profiles
- Recruiter approval/rejection workflow
- Course and mock interview management
- Placement analytics and branch-wise reports
- All job postings overview

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Java 17, Spring Boot 3, Spring Security |
| **Authentication** | JWT (JSON Web Tokens) |
| **Database** | MySQL with Hibernate ORM |
| **Frontend** | HTML5, CSS3, Vanilla JavaScript |
| **Deployment** | Render |
| **Build Tool** | Maven |

---

## 🚀 Live Demo

🌐 **[https://recruitai-pu35.onrender.com](https://recruitai-pu35.onrender.com)**

> ⚠️ Note: The app is hosted on Render's free tier. It may take 30-50 seconds to load on first visit as the server spins up from sleep.

---

## ⚙️ Key Highlights

- **Role-based access control** — Separate dashboards and APIs for each user type
- **JWT Authentication** — Secure stateless authentication
- **Auto-shortlisting** — Automatically matches eligible students to job criteria
- **Real-time status updates** — Application pipeline with multiple stages
- **Invite code system** — Controlled recruiter and admin registration
- **Placement analytics** — Branch-wise placement tracking and reporting

---

## 🏗 Project Structure
```
RecruitAi/
├── src/main/java/
│   ├── controller/        # REST API endpoints
│   ├── service/           # Business logic
│   ├── model/             # Database entities
│   ├── repository/        # Data access layer
│   ├── dto/               # Data transfer objects
│   └── security/          # JWT authentication
├── src/main/resources/
│   └── static/            # Frontend HTML files
└── pom.xml
```

---

## 👥 Team

| Member | GitHub |
|---|---|
| Shashank Rai | [@Shashankrai30](https://github.com/Shashankrai30) |
| Shanti | [@ShantiPr28-byte](https://github.com/ShantiPr28-byte) |

---

## 📄 License

This project is licensed under the MIT License.

---

<div align="center">
Made with ❤️ for Campus Placement Management
</div>
