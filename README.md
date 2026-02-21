
# Life-Task-Manager

Short guide: run the whole app locally with Docker Compose from the repository root.

Docker (local)
- Build all services
  ```sh
  docker compose build
  ```
- Start all services:
  ```sh
  docker compose up
  ```
- Stop and remove containers:
  ```sh
  docker compose down
  ```
- View logs:
  ```sh
  docker compose logs -f
  ```
- Show status:
  ```sh
  docker compose ps
  ```
- Notes:
  - The compose file maps ports: backend 5000, frontend 3000, mongo 27017.
  - Do NOT run local dev servers (e.g. `npm run dev` / `npm start`) for the backend or frontend while Docker is using the same ports — stop those local processes first to avoid port conflicts.

