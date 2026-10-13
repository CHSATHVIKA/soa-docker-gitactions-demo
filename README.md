# Student API full-stack application

This project contains:

- A React/Vite frontend
- A Spring Boot backend
- A PostgreSQL database

Docker Compose runs all three services on the same network.

## Run everything with Docker

From the repository root (`docker-git-actions-demo`), run:

```powershell
docker compose up --build
```

The first run builds the frontend and backend images, so it can take a few
minutes. Leave this terminal running.

Open these URLs in a browser:

- Frontend: http://localhost:3000
- Backend health endpoint: http://localhost:2025/studentapi/
- Backend API: http://localhost:2025/studentapi/all
- Swagger UI: http://localhost:2025/swagger-ui/index.html

The frontend uses `VITE_API_URL=http://localhost:2025`, because API requests
are made by the browser. Inside the Compose network, the backend connects to
PostgreSQL using the service name `postgresdb`.

## Useful commands

```powershell
# Stop and remove the containers (keep the database volume)
docker compose down

# Stop containers and delete the PostgreSQL data volume
docker compose down -v

# Run in the background
docker compose up --build -d

# View service logs
docker compose logs -f frontend
docker compose logs -f backend
docker compose logs -f postgresdb
```

If port `3000`, `2025`, or `5432` is already in use, change the number on the
left side of the corresponding port mapping in `docker-compose.yml`.
