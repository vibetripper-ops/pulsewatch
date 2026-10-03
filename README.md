# PulseWatch

PulseWatch is a full-stack website uptime and health monitoring application. It allows users to register accounts, add URLs to monitor, schedule background health checks, and view real-time latency and uptime logs on an interactive dashboard.

---

## Technical Stack

- Frontend: Next.js (App Router, React 19, Vanilla CSS with Flexbox)
- Backend: Node.js, Express.js (ES Modules)
- Database: PostgreSQL (Docker container)
- ORM: Sequelize
- In-Memory Cache: Redis via ioredis (Docker container)
- Background Queue: BullMQ (running on Redis)
- Validation: Zod
- Authentication: JSON Web Tokens (JWT) and bcryptjs
- HTTP Logger: Morgan

For a deep dive into how each part was built, the JavaScript concepts used, and dependency breakdowns, refer to [EXPLANATION.md](file:///c:/Users/harsh/OneDrive/Desktop/New%20folder%20(2)/EXPLANATION.md).

---

## Prerequisites

- Node.js (version 18 or higher recommended)
- Docker and Docker Compose

---

## Quick Start Guide

### 1. Start Infrastructure (PostgreSQL and Redis)

Open a terminal and start the database and cache containers:

```bash
cd backend
docker compose up -d
```

Verify that the containers are running:

```bash
docker compose ps
```

### 2. Run the Backend Server

From the `backend` directory, install dependencies and start the development server:

```bash
cd backend
npm install
npm run dev
```

The backend server will run on: `http://localhost:5000`
Healthcheck endpoint: `http://localhost:5000/health`

### 3. Run the Frontend Application

Open a second terminal window, navigate to the `frontend` directory, install dependencies, and start the Next.js development server:

```bash
cd frontend
npm install
npm run dev
```

The frontend application will run on: `http://localhost:3000`

---

## Project Structure

```text
├── .gitignore
├── README.md
├── EXPLANATION.md
├── backend/
│   ├── docker-compose.yml
│   ├── package.json
│   ├── .env
│   ├── .env.example
│   └── src/
│       ├── app.js
│       ├── auth.js
│       ├── db.js
│       ├── queue.js
│       ├── redis.js
│       └── routes/
│           ├── auth.js
│           └── monitors.js
└── frontend/
    ├── package.json
    ├── lib/
    │   └── api.js
    └── app/
        ├── layout.js
        ├── globals.css
        ├── page.js
        ├── login/page.js
        ├── register/page.js
        └── dashboard/page.js
```

---

## Default Endpoints

| Service | URL | Description |
|---|---|---|
| Frontend Web App | http://localhost:3000 | User interface (Landing, Auth, Dashboard) |
| Backend API | http://localhost:5000 | Express REST API |
| Health Check | http://localhost:5000/health | API server operational status |
| PostgreSQL | localhost:5432 | Port mapped from Docker container |
| Redis | localhost:6379 | Port mapped from Docker container |
