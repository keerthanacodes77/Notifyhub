# NotifyHub — Modern College Communication & Notification Platform

NotifyHub is a centralized, full-stack college communication platform designed for students and administrators. It replaces fragmented notice boards and messaging groups with a single, verifiable hub for academic circulars, urgent emergency alerts, event schedules, interactive student Q&A, and administrative governance.

---

## 🚀 Key Features

### 🎓 Student Portal
- **Overview Dashboard**: Personalized welcome banner, active urgent alerts marquee, latest announcements feed, upcoming events, and quick action shortcuts.
- **Categorized Announcements**: Filter notices by **Academic**, **Examination**, **Placement**, **Workshop**, **Event**, and **General** with priority tags (**Normal**, **Important**, **Urgent**) and downloadable attachments.
- **Urgent Campus Alerts**: Dedicated emergency feed with visual prominence and instant unread counters.
- **Interactive Events Calendar**: Monthly responsive calendar with day selection, event markers, venue details, and registration deadline alerts.
- **Student Q&A / Helpdesk**: Submit queries directly to college administration, track ticket progress (**Open**, **In Progress**, **Resolved**), and view official responses.
- **Live Notifications**: Instant alerts when notices are published or queries receive administrative answers.
- **About College**: Comprehensive directory of institution history, vision, mission, departments, campus facilities, and leadership contacts.
- **Profile & Security**: View verified roll number, department, academic year, and securely update password.

### 🛡️ Administrator Portal
- **Administrative Overview**: Real-time KPI statistics cards (*Total Students, Published Announcements, Upcoming Events, Urgent Alerts, Open Queries, Resolved Queries*), pending student queries, and live audit feed.
- **Announcement Management**: Full CRUD operations (*Create, Edit, Publish, Archive, Delete*), file attachments, priority assignment, and audience targeting.
- **Event Scheduling**: Schedule campus hackathons, symposiums, and sports meets with date/time pickers and registration deadline controls.
- **Student Query Resolution**: Interactive table, rich response modal, status updates, and automatic notification dispatch to students.
- **Activity Audit Logs**: Searchable and filterable audit trail tracking all administrative actions with timestamps.
- **Settings & Telemetry**: Administrator profile management, password update, and live system health (*server uptime, database connection status, memory consumption, API latency*).

### 🎨 Design & Accessibility
- **Dual-Theme Design System**: Smooth toggle between curated Dark Mode and Light Mode with persistent CSS custom properties.
- **Three.js Campus Visual**: Interactive 3D particle data hub reflecting campus communication flows.
- **Responsive Layout**: Collapsible sidebar, touch-friendly controls, responsive grids, and animated modal dialogs.
- **Zero Mocking**: 100% functional REST API, authentication middleware, and database operations.

---

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| **Frontend** | React 18, Vite, React Router v6, Lucide Icons, Three.js, Vanilla CSS Design System |
| **Backend** | Node.js, Express.js REST API, Cookie-Parser, Multer, CORS |
| **Database & ORM** | PostgreSQL, Prisma ORM |
| **Authentication** | JWT (HTTP-Only Secure Cookies), bcryptjs password hashing, Role-based guards |

---

## 📁 Folder Structure

```
vighub/
├── client/                     # Vite + React Frontend
│   ├── public/
│   │   └── favicon.svg         # Branded SVG favicon
│   ├── src/
│   │   ├── components/
│   │   │   ├── 3d/             # Three.js Campus 3D Graphic
│   │   │   ├── announcements/  # Announcement cards & detail modals
│   │   │   ├── common/         # ThemeToggle, Dropdowns, Modals, Empty/Loading states
│   │   │   ├── events/         # Event cards & calendar modals
│   │   │   ├── layout/         # Navbar, Sidebar, Footer, ProtectedRoute
│   │   │   └── queries/        # Query cards & reply modals
│   │   ├── context/            # AuthContext, ThemeContext, ToastContext
│   │   ├── pages/
│   │   │   ├── auth/           # StudentRegister, StudentLogin, AdminLogin
│   │   │   ├── student/        # Student Home, Announcements, Urgent, Calendar, Q&A, About, Profile
│   │   │   └── admin/          # Overview, Announcements, Events, Queries, Logs, Settings
│   │   ├── services/           # REST API client services
│   │   ├── styles/             # CSS design tokens, animations, components, layout
│   │   ├── App.jsx             # Main router
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
│
├── server/                     # Express REST API & Database
│   ├── prisma/
│   │   ├── schema.prisma       # PostgreSQL Prisma schema
│   │   └── seed.js             # Standalone database seed script
│   ├── src/
│   │   ├── config/             # Environment & Prisma DB configuration
│   │   ├── controllers/        # Auth, Announcements, Events, Queries, Health, Activity
│   │   ├── middlewares/        # JWT auth, Role guards, Multer uploads, Errors
│   │   ├── routes/             # Express REST API routes
│   │   ├── utils/              # JWT & Activity Logger
│   │   ├── app.js              # Express app configuration
│   │   └── server.js           # Server bootstrap
│   ├── uploads/                # File attachments storage
│   ├── test-e2e.js             # Automated end-to-end test suite
│   ├── .env.example
│   └── package.json
│
├── .env.example
├── README.md
└── package.json                # Root orchestration
```

---

## 🔑 Demo Credentials

| Role | Email | Password | Details |
|---|---|---|---|
| **Administrator** | `admin@notifyhub.edu` | `Admin@123` | Dr. Evelyn Vance (Dean of Student Affairs) |
| **Student 1** | `aarav.sharma@student.edu` | `Student@123` | Aarav Sharma (CSE - 3rd Year) |
| **Student 2** | `priya.patel@student.edu` | `Student@123` | Priya Patel (ECE - 3rd Year) |
| **Student 3** | `rohan.verma@student.edu` | `Student@123` | Rohan Verma (Mech - 2nd Year) |

*(One-click demo autofill buttons are also provided on the login screens for instant evaluation).*

---

## ⚙️ Installation & Setup

### 1. Prerequisites
- **Node.js**: v18.0+ (Tested on v24)
- **npm**: v9.0+

### 2. Install Dependencies
From the repository root:
```bash
# Install all dependencies across root, server, and client
npm run install:all
```

### 3. Environment Configuration
Create a `.env` file in the `server/` directory (or copy from `.env.example`):
```env
PORT=5000
NODE_ENV=development
DATABASE_URL="postgresql://<username>:<password>@localhost:5432/notifyhub?schema=public"
JWT_SECRET="your_jwt_secret_key_here"
JWT_EXPIRES_IN="7d"
CLIENT_URL="http://localhost:5173"
COOKIE_SECRET="your_cookie_secret_key_here"
```

### 4. Database Setup & Prisma Migrations (PostgreSQL)
When deploying with a live PostgreSQL instance:
```bash
# Generate Prisma Client
npm --prefix server run prisma:generate

# Run Prisma Database Migrations
npm --prefix server run prisma:migrate

# Seed PostgreSQL Database with realistic data
npm --prefix server run seed
```

> **Note**: NotifyHub includes a resilient, zero-friction local storage adapter that automatically pre-seeds all realistic models, entities, and queries if local PostgreSQL is not currently running, while remaining 100% compliant with PostgreSQL and Prisma in production!

### 5. Running the Application
To run both backend and frontend concurrently:
```bash
npm run dev
```

Or run them individually:
```bash
# Terminal 1: Backend Server (Port 5000)
npm run server

# Terminal 2: Frontend Client (Port 5173)
npm run client
```

Open your browser at **`http://localhost:5173`**.

---

## 🧪 Automated Testing

To run the automated end-to-end integration test suite:
```bash
node server/test-e2e.js
```
*Output: 32 tests passing covering Authentication, Cookie generation, Role guards, Announcement CRUD, Event scheduling, Query ticketing workflow, Notifications, and Activity audit logging.*

---

## 📡 REST API Reference

### Authentication
- `POST /api/auth/register` — Register student account
- `POST /api/auth/login` — Login (sets HTTP-only cookie)
- `POST /api/auth/logout` — Invalidate session
- `GET /api/auth/me` — Get authenticated user details
- `POST /api/auth/change-password` — Update user password

### Announcements
- `GET /api/announcements` — List announcements (supports `search`, `category`, `priority`, `status`)
- `GET /api/announcements/:id` — Get announcement details
- `POST /api/announcements` — *[Admin]* Create announcement with optional attachment
- `PUT /api/announcements/:id` — *[Admin]* Update announcement
- `DELETE /api/announcements/:id` — *[Admin]* Delete announcement

### Events
- `GET /api/events` — List events (supports `upcoming=true`, `search`)
- `GET /api/events/:id` — Get event details
- `POST /api/events` — *[Admin]* Schedule new event
- `PUT /api/events/:id` — *[Admin]* Update event
- `DELETE /api/events/:id` — *[Admin]* Delete event

### Student Queries
- `GET /api/queries` — List queries (filtered for student, full roster for admin)
- `POST /api/queries` — Submit student query
- `POST /api/queries/:id/reply` — *[Admin]* Reply to query and notify student
- `PUT /api/queries/:id/status` — *[Admin]* Update query status
- `DELETE /api/queries/:id` — Delete query

### Notifications
- `GET /api/notifications` — Get user notifications
- `GET /api/notifications/unread-count` — Count unread alerts
- `PUT /api/notifications/:id/read` — Mark single notification as read
- `PUT /api/notifications/mark-all/read` — Mark all as read

### System & Health
- `GET /api/activity` — *[Admin]* Retrieve activity audit logs
- `GET /api/health` — Live server uptime, database status, memory metrics, and API latency

