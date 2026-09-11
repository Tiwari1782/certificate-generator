# Contributing Guide

## Prerequisites
- Node.js v18+
- Git installed
- Docker installed
- A code editor (VS Code recommended)

## Initial Setup
1. Clone the repo
   git clone https://github.com/Tiwari1782/certificate-generator.git
2. Move into the project
   cd certificate-generator
3. Switch to dev branch
   git checkout dev
4. Copy the env file
   cp .env.example .env
5. Ask the tech head for the actual env values

## Branch Naming Rules
Every person works on their own branch. Never work on main or dev directly.

Format:
feature/what-you-are-building
bugfix/issue-number-short-description

Examples:
feature/activity-submission-form
feature/certificate-generation-service
feature/email-integration
bugfix/42-email-not-sending

## Commit Message Format
Use this format for every commit:

feat: add certificate generation logic
fix: resolve email timeout issue
docs: update API documentation
style: format code with prettier
refactor: restructure worker service
test: add unit tests for email service

## Daily Workflow
1. Pull latest changes before starting work
   git checkout dev
   git pull origin dev
2. Create your branch from dev
   git checkout -b feature/your-feature-name
3. Make your changes
4. Stage and commit
   git add .
   git commit -m "feat: your message here"
5. Push your branch
   git push origin feature/your-feature-name
6. Go to GitHub and open a Pull Request to dev branch

## Pull Request Rules
- Every PR must be linked to an issue (write "Closes #issue-number" in the PR description)
- Every PR needs at least 1 approval before merging
- Do not merge your own PR
- Add screenshots if your change is UI related
- All conversations must be resolved before merging

## Code Style
- Use ESLint and Prettier (configs are already in the repo)
- Write comments for any logic that is not obvious
- No hardcoded secrets or API keys ever

## Folder Ownership
- frontend/         - Person 1, Person 2
- backend/routes    - Person 3, Person 4
- backend/workers   - Person 3, Person 4
- backend/services/certificate - Person 5
- backend/services/email       - Person 6
- backend/models and migrations - Person 7
- docker-compose and CI         - Person 8
- tests and docs                - Person 9

## What NOT to Do
- Do not push directly to main or dev
- Do not commit the .env file
- Do not merge without a review
- Do not work outside your assigned folder without informing the team
