# TalentGraph
### AI-Powered Job Application and Recruitment Intelligence Platform

TalentGraph is a recruitment management platform designed to streamline
the hiring process by connecting recruiters, companies, and candidates
through a centralized backend system.

The platform enables recruiters to manage job openings, review
applications, schedule interviews, maintain candidate records, and
track recruitment progress.

The initial phase focuses on developing a robust backend using
Node.js, Express.js, PostgreSQL, and Prisma ORM. Future development
will introduce Generative AI, resume intelligence, explainable
candidate-job matching, and AI-assisted interview preparation.

---

## 1. Problem Statement

Recruitment involves several interconnected activities, including
job creation, candidate applications, resume management, interview
scheduling, and evaluation.

Managing these activities across separate tools can result in
fragmented candidate information, inefficient workflows, and
difficulty tracking recruitment progress.

TalentGraph aims to address these challenges through a centralized
recruitment management platform with a structured relational database,
secure APIs, and well-defined application workflows.

The project will initially establish the core recruitment backend
and later evolve into an AI-powered recruitment intelligence system.

---

## 2. Project Objectives

The primary objectives of TalentGraph are:

- Develop a RESTful backend using Node.js and Express.js.
- Design a relational database using PostgreSQL.
- Use Prisma ORM for database modeling and migrations.
- Implement authentication and role-based authorization.
- Support company and job management.
- Manage candidate profiles and resume metadata.
- Implement job applications and application status transitions.
- Support interview scheduling and recruiter feedback.
- Provide searching, filtering, pagination, and analytics.
- Establish an extensible architecture for future AI integration.

---

## 3. Technology Stack

### Backend
- Node.js
- Express.js
- JavaScript or TypeScript

### Database
- PostgreSQL
- Prisma ORM

### Authentication and Validation
- JWT or secure session-based authentication
- Zod for request validation
- Role-based access control

### Development Tools
- Git and GitHub
- Postman for API testing
- Swagger / OpenAPI for API documentation
- Docker for containerization

### Future AI Technologies
- Large Language Model APIs
- Resume parsing and information extraction
- Embeddings and semantic search
- PostgreSQL with pgvector
- Retrieval-Augmented Generation (RAG)
- Agentic AI workflows

The AI technologies are planned extensions and are not considered
implemented features of the initial phase.

---

## 4. Core Features

### 4.1 User Authentication and Authorization

- User registration and login.
- Candidate and recruiter roles.
- Protected API endpoints.
- Role-based access control.
- Secure password hashing.
- User profile management.

### 4.2 Company Management

- Create and manage company profiles.
- Associate recruiters with companies.
- Update company information.
- Manage company-specific job openings.

### 4.3 Job Management

- Create job openings.
- Update and close job listings.
- Define job descriptions and requirements.
- Specify required skills and experience.
- Search and filter available jobs.
- Support pagination for job listings.

### 4.4 Candidate Management

- Create and update candidate profiles.
- Maintain educational and professional information.
- Manage candidate skills.
- Upload and manage resume files.
- Search candidate profiles where authorized.

### 4.5 Application Management

- Apply for available job openings.
- Track application status.
- View applications submitted by a candidate.
- Review applications as an authorized recruiter.
- Prevent duplicate applications for the same job.
- Maintain application history.

### 4.6 Interview Management

- Schedule interviews for applications.
- Record interview dates and times.
- Assign interviewers.
- Update interview status.
- Store recruiter feedback.
- Track interview history.

### 4.7 Recruitment Analytics

- Total number of job openings.
- Number of applications received.
- Applications grouped by status.
- Interview scheduling statistics.
- Recruitment activity summaries.

Analytics will be generated from the application's stored data
using PostgreSQL queries.

---

## 5. Database Design

TalentGraph will use PostgreSQL as its primary relational database
and Prisma ORM to define models, relationships, and migrations.

### Proposed Entities

| Entity | Responsibility |
|--------|----------------|
| User | Stores account and authentication information |
| Company | Stores company details |
| CompanyMember | Associates recruiters with companies |
| CandidateProfile | Stores candidate-specific information |
| Job | Stores job openings and requirements |
| Skill | Maintains a reusable list of skills |
| CandidateSkill | Associates candidates with skills |
| JobSkill | Associates jobs with required skills |
| Resume | Stores resume metadata and file references |
| Application | Connects candidates with job openings |
| Interview | Stores interview scheduling information |
| InterviewFeedback | Stores interview evaluation and feedback |

Additional tables may be introduced as the system evolves.

### Important Relationships

- A company can have multiple recruiters.
- A company can publish multiple jobs.
- A candidate can possess multiple skills.
- A skill can belong to multiple candidates.
- A job can require multiple skills.
- A candidate can apply for multiple jobs.
- A job can receive applications from multiple candidates.
- An application can have multiple interviews.
- An interview can have associated feedback records.

### Database Concepts Demonstrated

- One-to-one relationships.
- One-to-many relationships.
- Many-to-many relationships.
- Primary and foreign keys.
- Unique constraints.
- Database indexes.
- Prisma schema migrations.
- Transactions using Prisma.
- Relational queries and joins.
- Aggregation and filtering.

### Data Integrity

The database will enforce important constraints, including:

- Unique user email addresses.
- Unique candidate applications per job.
- Valid relationships between companies, jobs, candidates,
  applications, and interviews.
- Required fields for essential entities.
- Valid application status transitions enforced by the
  application layer.

Database transactions will be used where multiple related
operations must succeed or fail together.

---

## 6. Application Architecture

TalentGraph will initially follow a modular backend architecture.

                  Client Application
                          |
                          v
                    Express Server
                          |
                          v
                   Route Handlers
                          |
                          v
                   Authentication
                    & Validation
                          |
                          v
                    Controllers
                          |
                          v
                     Services
                          |
                          v
                      Prisma ORM
                          |
                          v
                      PostgreSQL
