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
