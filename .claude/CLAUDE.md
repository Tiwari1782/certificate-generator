# CLAUDE.md - Project Context for AI Assistant

## What This Project Does
A certificate generation system. When a user completes an activity and submits a form, a personalized certificate is automatically generated and sent to their email within 2 minutes.

## Full Flow
1. User fills out the activity submission form on the frontend
2. Frontend sends POST /api/submit with name, email, activityId
3. Backend validates the input and saves the submission to the database
4. Backend pushes a job to the BullMQ queue
5. A background worker picks up the job
6. Worker generates a certificate using the base template image
7. Worker sends the certificate as an email attachment via Resend
8. User receives the certificate in their inbox

## Tech Stack
- Frontend: Next.js (lives in /frontend)
- Backend: Node.js with Express (lives in /backend)
- Certificate Generation: Canvas or PDFKit
- Email: Resend API
- Database: PostgreSQL
- Queue: BullMQ with Redis
- Containerization: Docker and docker-compose

## Folder Structure and What Each Folder Does
- /frontend                        - All UI code, pages, components
- /backend/routes                  - Express API route definitions
- /backend/controllers             - Route handler logic
- /backend/services/certificate    - Certificate generation logic
- /backend/services/email          - Email sending logic
- /backend/workers                 - BullMQ background job workers
- /backend/models                  - Database models and schema
- /backend/middlewares             - Auth, validation, error handling
- /certificate-templates           - Base PNG or PDF template files and fonts
- /generated-certificates          - Temporary storage for generated certificates
- /docs                            - API docs, architecture, database schema
- /.github                         - PR template, issue templates, CI workflow

## API Endpoints
- POST /api/submit      - Receives form submission, queues certificate job
- GET  /api/health      - Health check endpoint
- GET  /api/status/:id  - Check status of a certificate job

## Database Tables
- users         - id, name, email, created_at
- submissions   - id, user_id, activity_id, submitted_at
- certificates  - id, submission_id, status, generated_at, sent_at

## Key Rules for This Project
- Never generate certificates synchronously on the request thread, always use the queue
- Never hardcode API keys or secrets, always use environment variables from .env
- Never push directly to main or dev branch, always use a feature branch and PR
- All API responses must follow this format:
  { success: true/false, data: {}, message: "string", error: "string if failed" }
- Certificate generation must complete within 30 seconds
- Email must be sent within 60 seconds of certificate generation

## Environment Variables Reference
See .env.example for all required variables and what they are for

## How to Run Locally
1. Clone the repo and switch to dev branch
2. Copy .env.example to .env and fill in values
3. Run docker-compose up
4. Frontend runs on http://localhost:3000
5. Backend API runs on http://localhost:4000

## Common Issues and Fixes
- If Redis connection fails, make sure Docker is running
- If certificate is not generated, check CERTIFICATE_TEMPLATE_PATH in .env
- If email is not sending, verify RESEND_API_KEY is correct in .env
- If database connection fails, check DATABASE_URL format in .env

## Team Ownership
- Frontend pages and components       - Person 1, Person 2
- Backend routes and controllers      - Person 3, Person 4
- Certificate generation service      - Person 5
- Email service                       - Person 6
- Database models and migrations      - Person 7
- Docker and CI/CD setup              - Person 8
- Tests and documentation             - Person 9

## What to Always Do When Helping a Team Member
- Follow the folder structure above strictly
- Use async/await, never callbacks
- Add input validation on every API endpoint
- Write a comment above every function explaining what it does
- Match the existing code style in the file you are editing
