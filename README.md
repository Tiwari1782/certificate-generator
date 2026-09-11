# 🎓 Certificate Generator

A system that automatically generates and emails certificates to users after they complete an activity.

## 🔄 How It Works

**User fills form → Submits activity → Certificate generated → Emailed within 2 minutes**

## 🛠️ Tech Stack

| Part | Technology |
|---|---|
| Frontend | React / Next.js |
| Backend | Node.js / Express |
| Certificate Generation | Canvas / PDFKit |
| Email Service | Resend |
| Database | PostgreSQL |
| Queue | BullMQ + Redis |

## 📁 Folder Structure

```text
certificate-generator/
├── backend/                    # API, workers, and services
├── frontend/                   # UI pages and components
├── certificate-templates/      # Base PNG/PDF templates
├── docs/                       # Architecture and API documentation
├── .github/                    # PR templates, issue templates, and CI
├── .claude/                    # AI assistant context
├── .env.example                # Environment variable template
├── docker-compose.yml          # Docker services configuration
└── README.md                   # Project documentation
```
## Step 4: Create `README.md`

Go to your repo → find the existing `README.md` (it was auto-created) → click the **pencil icon** to edit it → **delete everything** and paste this:

```markdown

```
# 🎓 Certificate Generator

A system that automatically generates and emails certificates to users after they complete an activity.

## 🔄 How it works
User fills form → Submits activity → Certificate generated → Emailed within 2 minutes
```
## 🛠️ Tech Stack
```
| Part | Technology |
|---|---|
| Frontend | React / Next.js |
| Backend | Node.js (Express) |
| Certificate | Canvas / PDFKit |
| Email | Resend |
| Database | PostgreSQL |
| Queue | BullMQ + Redis |
```
## 📁 Folder Structure
```
certificate-generator/
├── backend/          → API, workers, services
├── frontend/         → UI pages and components
├── certificate-templates/ → Base PNG/PDF templates
├── docs/             → Architecture and API docs
├── .github/          → PR templates, issue templates, CI
└── .claude/          → AI assistant context
```

## 🚀 How to Run Locally
```
1. Clone the repo
   ```bash
   git clone https://github.com/Tiwari1782/certificate-generator.git
   cd certificate-generator
   ```
2. Copy env file
   ```bash
   cp .env.example .env
   ```
3. Fill in your `.env` values
4. Run with Docker
   ```bash
   docker-compose up
   ```
5. Visit `http://localhost:3000`

## 👥 Team
| Role | Person |
|---|---|
| Tech Head | @Tiwari1782 |
| Frontend | @person1, @person2 |
| Backend | @person3, @person4 |
| Certificate Engine | @person5 |
| Email Service | @person6 |
| Database | @person7 |
| DevOps | @person8 |
| QA & Docs | @person9 |

## 📌 Important Links
- [Project Board](../../projects)
- [Contributing Guide](CONTRIBUTING.md)
- [Roadmap](ROADMAP.md)
- [API Docs](docs/API.md)
```

---
