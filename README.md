# EyeGuard AI
 
**A web-based, AI-assisted Diabetic Retinopathy (DR) screening and referral platform**
 
![Status](https://img.shields.io/badge/status-MVP%20%2F%20Test%20Plan%20v1.0-blue)
![Course](https://img.shields.io/badge/course-Software%20Quality%20Assurance%20%26%20Testing-green)
![Test Plan](https://img.shields.io/badge/test%20plan-SQAT--C01-orange)
 
EyeGuard AI helps clinics screen diabetic patients for retinopathy, review AI-generated results, issue specialist referrals, and follow up with patients, all in one web platform. The AI output is **decision support only**. A clinician always confirms or overrides the final result.
 
This repository contains the project's **Software Test Plan (SQAT-C01)** together with the platform's requirement specification, test cases, and testing artifacts, developed for *Software Quality Assurance and Testing* at AIUB.
 
---
 
## Table of Contents
 
1. [Problem Background](#problem-background)
2. [Solution Overview](#solution-overview)
3. [Key Features](#key-features)
4. [User Roles](#user-roles)
5. [Quality Attributes](#quality-attributes)
6. [Project Constraints](#project-constraints)
7. [Testing Strategy](#testing-strategy)
8. [Out of Scope](#out-of-scope)
9. [Tech Stack](#tech-stack)
10. [Suggested Repository Structure](#suggested-repository-structure)
11. [Team](#team)
12. [Academic Information](#academic-information)
13. [Disclaimer](#disclaimer)
---
 
## Problem Background
 
Diabetic retinopathy damages the blood vessels of the retina and often progresses silently until treatment options are limited. Regular retinal screening and timely referral can prevent most of the resulting vision loss. In practice, the care pipeline breaks down:
 
- Retinal specialists are concentrated in cities, so rural patients wait long for results.
- Screening records live on paper or in disconnected systems, so patient history is hard to track.
- Referral letters are handwritten or informal and are easily lost or never followed up.
- There is no structured reminder system, so many referred patients never reach a specialist.
## Solution Overview
 
EyeGuard AI connects the whole pipeline: **register patient → capture screening encounter → upload and quality-check fundus images → AI screening → clinician review → referral → follow-up reminders → reporting and audit**.
 
## Key Features
 
| Area | Capabilities |
| --- | --- |
| **Authentication & Access** | Login with email/username and password, verification code after repeated failures, one-hour lockout after excessive attempts, password change and reset, logout and session termination |
| **User & Role Management** | Create, modify, activate, deactivate users; role-based permissions; profile management |
| **Patient Management** | Registration with unique Patient ID, validation, update with audit trail, search by ID, name, phone, or date range, full patient history |
| **Screening Encounters** | Encounter creation per patient, visit date, status workflow (Pending, In Review, Completed), clinical notes |
| **Retinal Imaging** | Separate left and right eye upload, format and size validation, automated image-quality assessment with a "Retake Recommended" prompt, upload traceability (timestamp, uploader, image hash) |
| **AI Screening** | Inference service call, DR category (No DR, Mild DR, Referable DR), confidence score, Green/Orange/Red risk indicator, explanation heatmap overlay, failure handling and retry without data loss |
| **Clinician Review** | Review AI result next to the original image, confirm or override with a mandatory override reason |
| **Referrals** | Referral creation with hospital or specialist selection, PDF referral letter, status tracking (Created, Sent, Visited, Closed), referral history |
| **Follow-up Reminders** | Configurable timing (7 days before, 1 day before, after a missed appointment), Email, SMS, or WhatsApp channels, communication log, opt-out support |
| **Dashboard & Reporting** | Screening counts, pending referrals, recent activity, report filtering, PDF/CSV export |
| **Administration** | Clinic management, audit logging, backup and recovery, subscription and billing summary (MVP) |
 
## User Roles
 
- Clinic Operator / Nurse
- Doctor / Ophthalmologist
- Clinic Admin
- Program Manager
- System Admin
## Quality Attributes
 
| Attribute | Target |
| --- | --- |
| Usability | Full screening encounter in about 6 minutes on average, 10 minutes maximum |
| Performance | AI result within 10 seconds for at least 90% of single-image requests |
| Availability | At least 99.5% uptime per month, excluding scheduled maintenance |
| Scalability | 200 concurrent users and 5,000 screening encounters per day |
| Recovery | Restore within 8 hours, with no more than 24 hours of data loss |
| Security & Privacy | Role- and organization-based access, TLS in transit, secure storage |
| Auditability | Login, record access, upload, inference, override, and export are traceable |
| AI Safety | Risk class, confidence score, and overlay shown, labeled as decision support |
| Data Integrity | Unique patient IDs and duplicate prevention via phone and date of birth |
| Compatibility | Latest stable Chrome, Edge, and Firefox on desktop, laptop, and tablet |
| Maintainability | AI model updates through a versioned inference API |
| Interoperability | REST APIs and CSV/PDF export |
| Fault Tolerance | Clear error messages and retry without losing screening data |
 
## Project Constraints
 
- **Budget:** BDT 1,80,000
- **Timeline:** 1 month (4 weeks)
- **Team:** 2 developers plus clinical/domain expert support
- **Scope:** MVP only
- **Limitations:** dataset availability, internet dependency, AI prediction uncertainty, mandatory clinician validation
## Testing Strategy
 
Test plan identifier: **SQAT-C01** (Version 1.0, 20/08/2026)
 
| Level | Owner | Focus |
| --- | --- | --- |
| **Unit** | Individual developers | Authentication, patient registration, database operations, image upload and quality checks, AI inference API, result processing, referral generation, reminders, reports |
| **System / Integration** | Test manager with team lead and developers | Frontend–backend communication, backend–database integration, web app–AI API integration |
| **Acceptance** | Stakeholders and clinical/domain experts | End-to-end screening, review, referral, and follow-up workflows |
 
Developers must provide test cases, expected vs. actual results, sample outputs, and defect records. Critical defects are fixed before a module moves to system/integration testing.
 
## Out of Scope
 
The following are **not** tested in this plan:
 
- Autonomous clinical diagnosis and treatment recommendation
- Full EMR integration with external hospital or clinic systems
- Insurance claim processing
- Offline-first operation and resynchronization
- Software independently operated by participating clinics (compatibility only via API and PDF/CSV export)
## Tech Stack
 
| Layer | Technology |
| --- | --- |
| Language | Python |
| Image processing / AI | OpenCV, NumPy, retinal fundus image dataset |
| Database | SQL Server |
| Dev environment | Windows/Linux, Visual Studio / VS Code |
| Version control | Git / GitHub |
| Deployment | Cloud or local server with web server, database, image storage, SSL, and AI inference API |
| Clients | Chrome, Edge, Firefox |
 

 
## Team
 
**Section C, Summer 25-26**
 
- Eva Jahan
- Shoham Podder
- Dewan Hasibul Karim
- Shanto Debnath
- Sheikh Risalat Sanjan
**Course Instructor:** Saikat Baul
 
## Academic Information
 
American International University-Bangladesh (AIUB)
Department of Computer Science, Faculty of Science & Technology (FST)
Course: Software Quality Assurance and Testing
 
## Disclaimer
 
EyeGuard AI is an academic project. It is a screening decision-support tool and not a medical device. It does not provide a final diagnosis, and every referral decision requires confirmation by a qualified clinician.
 
