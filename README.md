# 🎯 RecruitAi — AI-Powered Campus Recruitment Platform

<div align="center">

![RecruitAi Banner](https://img.shields.io/badge/RecruitAi-AI%20Recruitment%20Platform-00d4aa?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Live-brightgreen?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)
![Java](https://img.shields.io/badge/Java-17-orange?style=for-the-badge&logo=java)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3-green?style=for-the-badge&logo=springboot)

**A full-stack intelligent campus placement management system built with Spring Boot & vanilla JavaScript**

🌐 [Live Demo](https://recruitai-pu35.onrender.com)

</div>

---

## 📌 About

**RecruitAi** is a comprehensive campus recruitment platform that streamlines the entire placement process — from student registration and job applications to recruiter approvals and placement tracking. It connects **three types of users**:

- 🎓 **Students** — Apply for jobs, track application status, access courses & mock interviews
- 🏢 **Recruiters** — Post jobs, manage applicants, shortlist & select candidates
- 🏫 **College Admin** — Oversee all placements, manage recruiters, track placement stats

---

## 📸 Screenshots

### 🏫 Admin Dashboard
> Full oversight — manage recruiters, students, analytics, and approvals from one place

![Admin Dashboard](https://raw.githubusercontent.com/ShantiPr28-byte/RecruitAi/main/admin-dashboard.png)

---

### 🏢 Recruiter Dashboard
> Post jobs, manage applicants, run coding assessments, and track the hiring pipeline

![Recruiter Dashboard](https://raw.githubusercontent.com/ShantiPr28-byte/RecruitAi/main/recruiter-dashboard.png)

---

### 🎓 Student Dashboard
> Track applications, get AI job recommendations, access courses, and monitor placement status

![Student Dashboard](https://raw.githubusercontent.com/ShantiPr28-byte/RecruitAi/main/student-dashboard.png)

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

> ⚠️ Note: The app is hosted on Render's free tier. It may take 30–50 seconds to load on first visit as the server spins up from sleep.

---

## ⚙️ Local Setup & Running

### Prerequisites

- **Java 17** — [Download](https://adoptium.net/)
- **Maven 3.8+** — [Download](https://maven.apache.org/download.cgi)
- **MySQL 8.0+** — [Download](https://dev.mysql.com/downloads/)
- **Git** — [Download](https://git-scm.com/)

---

### 1. Clone the Repository

```bash
git clone https://github.com/ShantiPr28-byte/RecruitAi.git
cd RecruitAi
```

### 2. Configure the Database

```sql
CREATE DATABASE recruitai_db;
```

Open `src/main/resources/application.properties` and update:

```properties
# Database Configuration
spring.datasource.url=jdbc:mysql://localhost:3306/recruitai_db?useSSL=false&serverTimezone=UTC
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password

# JPA / Hibernate
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect

# JWT Configuration
jwt.secret=your_jwt_secret_key_here_min_32_chars
jwt.expiration=86400000

# Server Port
server.port=8080
```

### 3. Build the Project

```bash
mvn clean install -DskipTests
```

### 4. Run the Application

```bash
mvn spring-boot:run
```

Or run the JAR directly:

```bash
java -jar target/recruitai-0.0.1-SNAPSHOT.jar
```

### 5. Access the Application

Open your browser and go to:
```
http://localhost:8080
```

### 6. Create First Admin (Optional)

Generate a BCrypt hash at [bcrypt-generator.com](https://bcrypt-generator.com/) then run:

```sql
INSERT INTO users (name, email, password, role)
VALUES ('Admin', 'admin@recruitai.com', '<bcrypt_hashed_password>', 'ADMIN');
```

---

## 📡 API Documentation

**Base URL:** `https://recruitai-pu35.onrender.com/api` · or `http://localhost:8080/api` locally

All protected endpoints require:
```
Authorization: Bearer <your_jwt_token>
```

---

### 🔐 Authentication

#### Register Student
```http
POST /api/auth/register/student
```
```json
{
  "name": "John Doe",
  "email": "john@college.edu",
  "password": "password123",
  "branch": "Computer Science",
  "cgpa": 8.5,
  "skills": ["Java", "Python", "SQL"],
  "phone": "9876543210"
}
```
**Response:** `201 Created`
```json
{
  "message": "Student registered successfully",
  "userId": 12
}
```

#### Register Recruiter
```http
POST /api/auth/register/recruiter
```
```json
{
  "name": "Jane Smith",
  "email": "jane@company.com",
  "password": "password123",
  "companyName": "TechCorp Pvt Ltd",
  "inviteCode": "RECRUITER_INVITE_CODE"
}
```

#### Login
```http
POST /api/auth/login
```
```json
{
  "email": "john@college.edu",
  "password": "password123"
}
```
**Response:** `200 OK`
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "role": "STUDENT",
  "userId": 12,
  "name": "John Doe"
}
```

---

### 🎓 Student Endpoints

#### Get Profile
```http
GET /api/student/profile
Authorization: Bearer <token>
```

#### Update Profile
```http
PUT /api/student/profile
Authorization: Bearer <token>
```
```json
{
  "phone": "9876543210",
  "cgpa": 8.7,
  "skills": ["Java", "Spring Boot", "MySQL"]
}
```

#### Get All Active Jobs
```http
GET /api/student/jobs
Authorization: Bearer <token>
```
**Response:** `200 OK`
```json
[
  {
    "jobId": 5,
    "title": "Software Engineer",
    "company": "TechCorp",
    "eligibleBranches": ["CSE", "IT"],
    "minCgpa": 7.5,
    "packageLPA": 12.0,
    "deadline": "2025-03-31",
    "status": "ACTIVE"
  }
]
```

#### Apply for a Job
```http
POST /api/student/jobs/{jobId}/apply
Authorization: Bearer <token>
```
**Response:** `200 OK`
```json
{
  "message": "Application submitted successfully",
  "applicationId": 34,
  "status": "APPLIED"
}
```

#### Get My Applications
```http
GET /api/student/applications
Authorization: Bearer <token>
```
**Response:** `200 OK`
```json
[
  {
    "applicationId": 34,
    "jobTitle": "Software Engineer",
    "company": "TechCorp",
    "appliedDate": "2025-02-15",
    "status": "SHORTLISTED"
  }
]
```

---

### 🏢 Recruiter Endpoints

#### Post a Job
```http
POST /api/recruiter/jobs
Authorization: Bearer <token>
```
```json
{
  "title": "Software Engineer",
  "description": "Backend development role using Java and Spring Boot.",
  "eligibleBranches": ["CSE", "IT", "ECE"],
  "minCgpa": 7.5,
  "packageLPA": 12.0,
  "deadline": "2025-03-31",
  "openings": 5
}
```
**Response:** `201 Created`
```json
{
  "message": "Job posted successfully",
  "jobId": 5
}
```

#### Get My Posted Jobs
```http
GET /api/recruiter/jobs
Authorization: Bearer <token>
```

#### Get Applicants for a Job
```http
GET /api/recruiter/jobs/{jobId}/applicants
Authorization: Bearer <token>
```
**Response:** `200 OK`
```json
[
  {
    "applicationId": 34,
    "studentName": "John Doe",
    "branch": "CSE",
    "cgpa": 8.5,
    "skills": ["Java", "Spring Boot"],
    "status": "APPLIED"
  }
]
```

#### Update Application Status
```http
PUT /api/recruiter/applications/{applicationId}/status
Authorization: Bearer <token>
```
```json
{
  "status": "SHORTLISTED"
}
```
> Valid values: `APPLIED` · `SHORTLISTED` · `INTERVIEW` · `SELECTED` · `REJECTED`

#### Auto-Shortlist Eligible Students
```http
POST /api/recruiter/jobs/{jobId}/auto-shortlist
Authorization: Bearer <token>
```
**Response:** `200 OK`
```json
{
  "message": "Auto-shortlisting complete",
  "shortlistedCount": 23
}
```

#### Create Coding Test
```http
POST /api/recruiter/jobs/{jobId}/test
Authorization: Bearer <token>
```
```json
{
  "title": "Java Coding Round",
  "duration": 60,
  "questions": [
    {
      "questionText": "Write a function to reverse a linked list.",
      "marks": 20
    }
  ]
}
```

---

### 🏫 Admin Endpoints

#### Get All Students
```http
GET /api/admin/students
Authorization: Bearer <token>
```

#### Get Student Detail
```http
GET /api/admin/students/{studentId}
Authorization: Bearer <token>
```

#### Get All Recruiters
```http
GET /api/admin/recruiters
Authorization: Bearer <token>
```

#### Approve / Reject Recruiter
```http
PUT /api/admin/recruiters/{recruiterId}/status
Authorization: Bearer <token>
```
```json
{
  "status": "APPROVED"
}
```
> Valid values: `APPROVED` · `REJECTED`

#### Get Placement Analytics
```http
GET /api/admin/analytics
Authorization: Bearer <token>
```
**Response:** `200 OK`
```json
{
  "totalStudents": 450,
  "totalPlaced": 312,
  "placementPercentage": 69.3,
  "branchWise": [
    { "branch": "CSE", "placed": 120, "total": 150 },
    { "branch": "IT",  "placed": 85,  "total": 110 }
  ],
  "topRecruiters": [
    { "company": "TechCorp", "hired": 45 }
  ]
}
```

#### Add Course / Resource
```http
POST /api/admin/courses
Authorization: Bearer <token>
```
```json
{
  "title": "Data Structures & Algorithms",
  "description": "Comprehensive DSA course for placement prep.",
  "link": "https://example.com/dsa-course",
  "type": "COURSE"
}
```

---

### ❗ Error Responses

| Status Code | Meaning |
|---|---|
| `400 Bad Request` | Invalid input or missing fields |
| `401 Unauthorized` | Missing or invalid JWT token |
| `403 Forbidden` | Insufficient role permissions |
| `404 Not Found` | Resource does not exist |
| `409 Conflict` | Duplicate entry (e.g., already applied) |
| `500 Internal Server Error` | Server-side error |

**Error Response Format:**
```json
{
  "timestamp": "2025-02-27T10:30:00Z",
  "status": 401,
  "error": "Unauthorized",
  "message": "JWT token is expired or invalid",
  "path": "/api/student/jobs"
}
```

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
| Shanti Priya | [@ShantiPr28-byte](https://github.com/ShantiPr28-byte) |
| Shashank Rai | [@Shashankrai30](https://github.com/Shashankrai30) |

---

## 📄 License

This project is licensed under the MIT License.

---

<div align="center">

Made with ❤️ for Campus Placement Management

</div>
