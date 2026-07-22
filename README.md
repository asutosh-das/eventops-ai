<div align="center">

<img src="https://img.shields.io/badge/EventOps-AI-6366f1?style=for-the-badge&logoColor=white" alt="EventOps AI"/>

# EventOps AI

**An intelligent event operations platform powered by Google Gemini.**  
Manage events, registrations, venues, speakers, sponsorships, and incidents — all in one place, with a conversational AI assistant at the core.

<br/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-3.x-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Gemini](https://img.shields.io/badge/Google%20Gemini-2.5%20Flash-4285F4?style=flat-square&logo=google&logoColor=white)](https://ai.google.dev/)
[![SQLite](https://img.shields.io/badge/SQLite-SQLAlchemy-003B57?style=flat-square&logo=sqlite&logoColor=white)](https://www.sqlalchemy.org/)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=flat-square)](./LICENSE)

</div>

---

## Overview

EventOps AI is a full-stack, AI-augmented event management system designed for teams that run conferences, hackathons, and corporate events. It combines robust operational tooling with a Gemini-powered conversational assistant that understands natural language queries like *"show me my registrations"* or *"remind me about the AI Summit tomorrow."*

---

## ✨ Features

| | Feature | Description |
|---|---|---|
| 🤖 | **AI Assistant** | Conversational interface powered by Gemini 2.5 Flash for event queries, reminders, and data retrieval |
| 🗓️ | **Event Management** | Full CRUD for events with status tracking (upcoming, ongoing, completed) |
| 🎟️ | **Registrations** | User self-registration with ticket type selection and real-time check-in tracking |
| 🏛️ | **Venue Management** | Venue capacity and utilization monitoring across multiple locations |
| 🎤 | **Speaker Management** | Speaker profiles, session scheduling, and availability tracking |
| 💼 | **Sponsorship Tracking** | Sponsor commitments, deliverables, visibility scores, and ROI metrics |
| 🚨 | **Incident Management** | Prioritized incident logging and resolution tracking for on-site issues |
| 🔔 | **Smart Reminders** | AI-scheduled, background-processed reminder notifications via APScheduler |
| 🛡️ | **Role-Based Access** | Separate user and admin portals with route-level authorization |
| 📊 | **Analytics Dashboard** | Aggregated stats across all operational dimensions |

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Python 3.10+, Flask 3.x |
| **AI / LLM** | Google Gemini 2.5 Flash (`google-genai`) |
| **ORM / Database** | Flask-SQLAlchemy, SQLite (dev) / PostgreSQL (prod) |
| **Auth** | Flask-Login, Werkzeug password hashing |
| **Scheduling** | APScheduler (BackgroundScheduler) |
| **Frontend** | Jinja2 templates, Bootstrap, Vanilla JS |
| **Config** | python-dotenv |

---

## ⚡ Quick Start

> Get up and running in under 30 seconds.

```bash
# 1. Clone the repository
git clone https://github.com/your-username/event-ops-ai.git
cd event-ops-ai

# 2. Create and activate a virtual environment
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # macOS / Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure environment variables (see table below)
cp .env.example .env

# 5. Run the development server
python app.py
```

Open [http://127.0.0.1:5000](http://127.0.0.1:5000) in your browser.

---

## 🔑 Environment Variables

Create a `.env` file in the project root. The app auto-seeds a default admin and sample data on first run.

| Variable | Required | Default | Description |
|---|---|---|---|
| `SECRET_KEY` | ✅ | `your-secret-key-here` | Flask session signing key. Use a long random string in production. |
| `GEMINI_API_KEY` | ✅ | — | Google Gemini API key. Get one at [ai.google.dev](https://ai.google.dev/). |
| `DATABASE_URL` | ❌ | `sqlite:///instance/eventops.db` | SQLAlchemy database URI. Switch to PostgreSQL for production. |

```env
# .env
SECRET_KEY=your-super-secret-key-change-me
GEMINI_API_KEY=your_google_gemini_api_key
# DATABASE_URL=postgresql://user:pass@localhost/eventops  # optional
```

> [!IMPORTANT]
> Never commit your `.env` file. It is included in `.gitignore` by default.

---

## 📁 Project Structure

```
event-ops-ai/
├── app.py                  # Application entry point — models, routes, AI logic
├── requirements.txt        # Python dependencies
├── .env                    # Environment variables (git-ignored)
├── instance/
│   └── eventops.db         # SQLite database (auto-created)
├── static/
│   ├── css/
│   │   └── styles.css      # Global stylesheet
│   ├── js/                 # Frontend scripts
│   └── img/                # Static assets
└── templates/
    ├── base.html           # Base layout with navigation
    ├── index.html          # Landing page
    ├── dashboard.html      # User dashboard
    ├── admin_events.html   # Admin event management
    ├── browse_events.html  # Public event listing
    ├── event_detail.html   # Single event view
    ├── profile.html        # User profile & stats
    └── ...                 # 13 templates total
```

---

## 🔌 API Reference

All API endpoints are authenticated via session cookie (Flask-Login required).

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/assistant` | Send a message to the Gemini AI assistant |

### `POST /api/assistant`

**Request**
```json
{
  "message": "Show me my registrations"
}
```

**Response**
```json
{
  "reply": "• AI Summit 2026 (Ticket: VIP) - Checked in: ✅\n• Hackathon Night (Ticket: Standard) - Checked in: ❌"
}
```

**Supported assistant intents:**

| Intent | Example Query |
|---|---|
| `get_events` | *"What events are coming up?"* |
| `get_my_registrations` | *"Show me my tickets"* |
| `get_event_details` | *"Tell me about the Hackathon Night"* |
| `schedule_reminder` | *"Remind me about AI Summit tomorrow at 8am"* |
| `get_venues` | *"Which venues are available?"* |
| `get_speakers` | *"Who is speaking at the summit?"* |

---

## 👤 Default Credentials

The database is auto-seeded with two accounts on first launch:

| Role | Email | Password |
|---|---|---|
| Admin | `admin@eventops.com` | `admin123` |
| User | `user@eventops.com` | `user123` |

> [!WARNING]
> Change these credentials immediately before any production or shared deployment.

---

## 🗺 Roadmap

- [x] Gemini AI conversational assistant
- [x] Role-based admin portal
- [x] Background reminder scheduler
- [x] Incident management module
- [ ] Email/SMS delivery for notifications (SendGrid / Twilio)
- [ ] QR code check-in via mobile
- [ ] Multi-tenant support for event agencies
- [ ] Real-time dashboard with WebSocket updates
- [ ] REST API with JWT authentication
- [ ] Docker & Docker Compose setup
- [ ] CI/CD pipeline (GitHub Actions)

---

## 🤝 Contributing

Contributions are welcome and appreciated.

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feat/your-feature`
3. **Commit** your changes: `git commit -m "feat: add your feature"`
4. **Push** to your branch: `git push origin feat/your-feature`
5. **Open** a Pull Request

Please follow [Conventional Commits](https://www.conventionalcommits.org/) for commit messages and ensure your changes don't break existing routes.

> [!NOTE]
> For major changes, please open an issue first to discuss what you would like to change.

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](./LICENSE) for more information.

---

## 👨‍💻 Author

Built with ❤️ at **Infosys**.

<div align="center">

---

*EventOps AI — Intelligent Operations for Modern Events*

</div>
