# Roadmap

## Overview
Total Duration: 20 days
Team Size: 9 people
Goal: Build a system where a user completes an activity, submits a form, and receives a certificate on their email within 2 minutes.

---

## Week 1 - Days 1 to 7 - Foundation

### Day 1 to 2 - Project Setup
- [ ] All members clone the repo and run it locally
- [ ] Database schema designed and finalized
- [ ] .env.example filled with all required variable names
- [ ] Docker setup working on all machines
- [ ] All issues created and assigned on GitHub Projects board

### Day 3 to 4 - Core Backend
- [ ] POST /api/submit endpoint created
- [ ] Input validation added
- [ ] Database models created (User, Submission, Certificate)
- [ ] Basic error handling in place

### Day 5 to 7 - Core Frontend
- [ ] Activity form UI built
- [ ] Form connected to POST /api/submit
- [ ] Success screen after submission
- [ ] Basic styling done

---

## Week 2 - Days 8 to 14 - Core Features

### Day 8 to 10 - Certificate Engine
- [ ] Base certificate template added to /certificate-templates
- [ ] Certificate generation script working locally
- [ ] Name, date, and activity text placed correctly on template
- [ ] Certificate saved as PDF/PNG

### Day 11 to 12 - Email Service
- [ ] Resend or SendGrid account set up
- [ ] Email sends successfully with certificate attached
- [ ] Email template looks professional

### Day 13 to 14 - Queue and Async Flow
- [ ] BullMQ + Redis set up
- [ ] Certificate generation moved to background worker
- [ ] End to end flow working: submit -> queue -> generate -> email

---

## Week 3 - Days 15 to 20 - Polish and Ship

### Day 15 to 16 - Testing
- [ ] Unit tests for certificate generation
- [ ] Unit tests for email service
- [ ] End to end test for full submission flow
- [ ] Edge cases handled (invalid email, missing name, duplicate submission)

### Day 17 to 18 - Error Handling and Logging
- [ ] All API errors return proper status codes and messages
- [ ] Failed jobs in queue are retried automatically
- [ ] Basic logging added across backend

### Day 19 - Deployment
- [ ] App deployed to a server or cloud platform
- [ ] Environment variables set in production
- [ ] End to end flow tested on live deployment

### Day 20 - Final Review
- [ ] All PRs merged and reviewed
- [ ] README updated with final setup instructions
- [ ] Codebase cleaned up
- [ ] Project handed over and documented

---

## Milestone Checkpoints
| Day | Checkpoint |
|---|---|
| Day 7  | Form submits and saves to database |
| Day 14 | Certificate generated and emailed successfully |
| Day 19 | App live and working in production |
| Day 20 | Project complete and documented |
