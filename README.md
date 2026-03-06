# Life-Task-Manager — Full Stack Guide

A full-stack task management application built with **React + TypeScript** (frontend), **Express + TypeScript** (backend), and **MongoDB**.

This guide covers setup, local development, tests, and Dockerized execution in a single place.

## License

MIT License (see LICENSE in this repository)

## Repository Structure

| Folder / File         | Description                                        |
|-----------------------|----------------------------------------------------|
| backend/              | Express + TypeScript API for task management       |
| frontend/             | React + TypeScript SPA for user interface          |
| docker-compose.yml    | Docker Compose configuration for local development |

## Quick Start (Local Development)

Clone the repository:

```bash
git clone https://github.com/ozmerensky/TASK-MANAGER-FS.git
cd TASK-MANAGER-FS
```

## Backend Setup

1. Navigate to the backend directory:

   ```bash
   cd backend
   npm install
   ```

2. Create a local .env file (backend/.env), example values:

   ```
   PORT=5000
   MONGO_URI=mongodb://localhost:27017/tasky_dev
   ALLOWED_ORIGINS=http://localhost:3000
   API_PREFIX=/tasks
   ```

3. Start the backend server:

   ```bash
   npm run dev
   ```

4. Run tests:

   ```bash
   npm test
   ```

### Important Backend Files

- `src/startServer.ts` — server startup and MongoDB connection
- `src/app.ts` — Express app and routes registration
- `src/models/Task.ts` — Mongoose model
- `src/services/*` — business logic for tasks
- `tests/` — unit and integration tests

## Frontend Setup

1. Navigate to the frontend directory:

   ```bash
   cd frontend
   npm install
   ```

2. Start the Vite development server:

   ```bash
   npm run dev
   ```

3. Open the app in your browser: http://localhost:5173

### API

The frontend expects the backend to run at http://localhost:5000.  
All endpoints are available under /tasks.  

*Backend Base URL:* You can configure the backend base URL in src/services/taskService.ts.  
This allows you to point the frontend to a different backend instance if needed (e.g., for staging or production environments).

### Tests

Cypress E2E tests:

Interactive mode:

```bash
npx cypress open
```

Headless mode:

```bash
npx cypress run
```

### Important Frontend Files

- `src/` — React components and source code
- `cypress/` — fixtures and end-to-end tests
- `vite.config.ts` — Vite configuration
- `cypress.config.ts` — Cypress configuration

---

## Running with Docker Compose

You can run the entire app (frontend + backend + MongoDB) locally with Docker Compose.

1. Build all services:

   ```bash
   docker compose build
   ```

2. Start all services:

   ```bash
   docker compose up
   ```

3. Stop and remove containers:

   ```bash
   docker compose down
   ```

4. View logs:

   ```bash
   docker compose logs -f
   ```

5. Show running containers:

   ```bash
   docker compose ps
   ```

## Notes

Ports mapping:

- Backend: 5000
- Frontend: 3000
- MongoDB: 27017

Do not run local development servers (npm run dev / npm start) while Docker Compose is running to avoid port conflicts.

## Environment & CI

Keep secrets in .env files, do not commit them

CI pipelines run tests automatically and ensure code quality

Backend tests use mongodb-memory-server for CI-friendly integration

E2E tests use MongoDB 6 container