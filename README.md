<div align="center">

# NU SEED Facility Management

A full-stack project tracking and facility management platform built with React, Node.js, and PostgreSQL.

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![React](https://img.shields.io/badge/React_18-61DAFB?logo=react&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?logo=vite&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?logo=tailwindcss&logoColor=white)

</div>

---

## What is this?

NU SEED is a comprehensive facility and project management platform designed for Naresuan University. It helps manage university events, track project tasks, handle participant registrations, and collect post-event feedback all in one place.

It's not just a simple task tracker. It features a full role-based access control (RBAC) system with completely separate portals for Executives (to see the big picture), Employees/Project Managers (to manage tasks and teams), and Participants (to submit documents and feedback).

We built this as a university software engineering project to learn how a real full-stack web application is built end-to-end: handling complex relational databases, JWT authentication, role management, and creating a scalable frontend architecture.

## 📸 Platform Showcase

### 📊 Executive Overview
The core dashboard for executives to track overall university events, budgets, and feedback ratings.
<div align="center">
  <img src="docs/screenshots/executive-dashboard.png" width="800" alt="Executive Dashboard" />
</div>

<br/>

**Project & Event Management**
| Employee Dashboard | Task Board |
|:-:|:-:|
| <img src="docs/screenshots/employee-dashboard.png" width="400" alt="Employee Dashboard"/> | <img src="docs/screenshots/task-board.png" width="400" alt="Task Board"/> |
| *Track all ongoing events and urgent tasks.* | *Assign and track progress of sub-tasks.* |

### 🎯 Participant Experience
Where students and participants interact with their registered events.

| My Projects | Document Hub |
|:-:|:-:|
| <img src="docs/screenshots/participant-projects.png" width="400" alt="My Projects"/> | <img src="docs/screenshots/document-hub.png" width="400" alt="Document Hub"/> |
| *View current event status and team details.* | *Upload required documents for the event.* |

### ⚙️ Management & Operations
Robust tools for team management, document verification, and feedback collection.

| Team & Roles | Feedback & Reports |
|:-:|:-:|
| <img src="docs/screenshots/team-management.png" width="400" alt="Team"/> | <img src="docs/screenshots/feedback-reports.png" width="400" alt="Feedback"/> |
| *Granular RBAC for team members.* | *View and analyze post-event feedback.* |


## Features

### For Employees (Project Managers)
- **Dashboard** — Real-time metrics showing active projects, total participants, and pending tasks.
- **Event Management** — Create, edit, and track events with budgets, timelines, and status updates.
- **Task Tracking** — Break down events into tasks, assign them to teams, and set priorities (High, Medium, Low).
- **Document Management** — System to verify documents uploaded by participants.
- **Team Management** — Manage participant groups, approve members, and assign roles.

### For Participants
- **My Dashboard** — View all registered events and their current progress.
- **Task Board** — See what needs to be done, submit work, and update task statuses.
- **Document Upload** — Securely upload requested files (like ID cards or consent forms).
- **Feedback System** — Fill out evaluation forms after an event finishes.

### For Executives
- **Executive Dashboard** — High-level overview of university-wide events, total budget usage, and participant counts.
- **Feedback Insights** — Aggregated satisfaction scores and comments from participants.

## Tech Stack

| Layer | Tech |
|-------|------|
| Frontend | React 18, Vite, React Router |
| Styling | Tailwind CSS, Lucide Icons |
| Backend | Node.js, Express.js |
| Database | PostgreSQL (running via Docker) |
| Auth & Security| JWT (JSON Web Tokens), bcryptjs |

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                    Frontend (React + Vite)           │
│  ┌──────────┐  ┌──────────┐  ┌───────────────────┐  │
│  │  Pages   │  │ Contexts │  │    Components     │  │
│  └────┬─────┘  └────┬─────┘  └───────────────────┘  │
│       │              │                               │
│       └──────┬───────┘                               │
│              ▼                                       │
│          Axios API Client                            │
└──────────────┬───────────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────────┐
│              Backend (Express.js)                   │
│  ┌──────────┐  ┌──────────┐  ┌──────────────────┐  │
│  │  Routes  │  │ Services │  │   Middlewares    │  │
│  └────┬─────┘  └────┬─────┘  └────────┬─────────┘  │
│       │             │                 │            │
│       └─────────────┼─────────────────┘            │
│                     ▼                              │
│                  pg (node-postgres)                │
└─────────────────────┬───────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────┐
│                 PostgreSQL Database                  │
│       (Events, Tasks, Users, Roles, Documents)       │
└─────────────────────────────────────────────────────┘
```

## Role-Based Access Control

The system separates users into 3 distinct roles, each with its own workspace:

| Role | Access | Description |
|------|--------|-------------|
| **Executive** | `/executive/*` | High-level view for university management. Can see everything but cannot edit tasks. |
| **Employee** | `/employee/*` | Project managers and staff who organize events and manage participants. |
| **Participant** | `/participant/*` | Students or external users who join the events. |

Access is enforced at two levels:
1. **Frontend** — Route guards that check the user's role before rendering a page.
2. **Backend** — API endpoints verify the JWT token and user role before executing queries.

## Getting Started

### Prerequisites
- Node.js 18+
- Docker Desktop (for the PostgreSQL database)

### Setup

```bash
# Clone the repo
git clone https://github.com/Nokpednam/nu-seed-facility-management.git
cd nu-seed-facility-management

# The easiest way to start the entire stack (Database, Backend, Frontend)
./start.sh
```

### Manual Setup (Without script)

If you prefer to run things manually:

```bash
# 1. Start the database
docker compose up -d

# 2. Setup Backend
cd backend
cp .env.example .env
npm install
node scripts/init-demo-db.js  # Seeds the database with demo data
npm run start                 # Starts API on port 5000

# 3. Setup Frontend
cd ../frontend
cp .env.example .env
npm install
npm run dev                   # Starts React app on port 5173
```

### Demo Accounts

The database seed script creates the following demo accounts (Password for all is `password123`):
- **Executive**: `exec@demo.nu.seed`
- **Employee**: `somchai@demo.nu.seed`
- **Participant**: `piya@demo.nu.seed`

## What I Learned

Building this project taught me a lot about real-world software engineering:
- **Complex Relational Database Design** — Creating a schema that handles multiple roles, mapping events to tasks, and linking documents to specific users.
- **Role-Based UIs** — Structuring a React application to serve completely different layouts and features depending on the logged-in user.
- **Full-Stack Integration** — Connecting a React frontend to a custom Express backend and handling CORS, JWT authentication, and error states gracefully.

---

## Team

Built by students at Naresuan University.

| Name | GitHub |
|------|--------|
| Natthawut Wanma | [@Nokpednam](https://github.com/Nokpednam) |
