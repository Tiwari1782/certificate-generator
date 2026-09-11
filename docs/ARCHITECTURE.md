# Architecture

## System Overview

User (Browser)
      |
      | HTTP POST /api/submit
      v
Frontend (Next.js - Port 3000)
      |
      | HTTP Request
      v
Backend API (Express - Port 4000)
      |
      |-- Validates input
      |-- Saves submission to PostgreSQL
      |-- Pushes job to BullMQ Queue
      |
      v
BullMQ Queue (Redis - Port 6379)
      |
      v
Background Worker
      |
      |-- Picks up job from queue
      |-- Generates certificate using template
      |-- Saves certificate temporarily
      |-- Sends email with certificate via Resend
      |
      v
User receives email with certificate attached


## Services Breakdown

### Frontend
- Built with Next.js
- Runs on port 3000
- Responsible for the activity form UI and success screen
- Communicates with backend via REST API
- Environment variable: NEXT_PUBLIC_API_URL

### Backend API
- Built with Node.js and Express
- Runs on port 4000
- Handles all incoming requests
- Validates input, saves to database, pushes to queue
- Does not generate certificates directly, that is handled async by the worker

### Certificate Worker
- Runs as a background process
- Listens to the certificate-generation queue
- Uses Canvas or PDFKit to draw text on the base template
- Saves generated certificate temporarily in /generated-certificates
- Passes file path to email service

### Email Service
- Uses Resend API
- Receives certificate file path and user email
- Attaches certificate and sends email
- Logs success or failure back to the job

### PostgreSQL Database
- Stores users, submissions, and certificate records
- Runs on port 5432
- Managed via migrations

### Redis
- Used only as the queue backend for BullMQ
- Runs on port 6379
- Stores pending, active, and failed jobs


## Key Design Decisions

### Why a Queue?
Certificate generation and email sending can take a few seconds.
If we did this synchronously, the user would have to wait and stare at a loading screen.
With a queue, the user gets an instant response and receives the email in the background.

### Why BullMQ?
BullMQ handles retries automatically if a job fails.
It also gives visibility into job status such as pending, active, completed, and failed.

### Why Resend?
Simple API, generous free tier, reliable delivery, and easy attachment support.


## Folder to Service Mapping

- /frontend                        - Frontend service
- /backend/routes                  - API route definitions
- /backend/controllers             - Request handling logic
- /backend/services/certificate    - Certificate generation
- /backend/services/email          - Email sending
- /backend/workers                 - BullMQ job processors
- /backend/models                  - Database models
- /backend/migrations              - Database migration files
- /certificate-templates           - Base template image and fonts
- /generated-certificates          - Temporary certificate storage
