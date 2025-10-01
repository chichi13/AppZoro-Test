# Problem 5: DevOps Engineer Challenge - Docker Containerization

## Disclaimer

`.env` files have been pushed for testing purposes only. In production, DO NOT PUSH `.env` files.

## Objective

Containerize the full application stack (Frontend, Backend, Database) using Docker and Docker Compose to make the development environment reproducible and easy to launch with a single command.

## Requirements

- Docker and Docker Compose installed
- All services must communicate within Docker network
- Database automatically seeded on first run
- Launch entire application with `docker compose up`

## Usage

### Launch the Application

```bash
# From project root
docker compose up --build
```

### Access the Application

- **Frontend:** http://localhost:5173
- **Backend API:** http://localhost:5007
- **Database:** localhost:5432

**Login Credentials:**
- Email: `admin@school-admin.com`
- Password: `3OU4zn3q6Zh9`

### Stop the Application

```bash
docker compose down
```

### Clean Up (Remove volumes)

```bash
docker compose down -v
```

## Inspect Docker Configuration

### View Resolved Configuration

To see the final configuration that Docker Compose will apply (after processing environment variables and extends):

```bash
docker compose config
```
