# Shared Postgres + pgAdmin Infrastructure

## Prerequisites
- Docker & Docker Compose installed
- An existing Docker network named `backend`: 
    $ docker network create backend

## Quick Start (Development)
1. Copy `.env.example` → `.env`:
     $ cd postgres
     $ cp .env.example .env
     # Edit `.env` with your own credentials/ports

2. Launch containers:
     $ docker-compose up -d

3. Postgres is available at:
     Host: <docker-host>
     Port: <POSTGRES_PORT>      (default 5432)

   pgAdmin is available at:
     http://<docker-host>:<PGADMIN_PORT>  (default 8080)
   Login with PGADMIN_DEFAULT_EMAIL / PGADMIN_DEFAULT_PASSWORD.

4. To tear down:
     $ docker-compose down
   To wipe data:
     $ docker volume rm common-infra_postgres_pgdata

## Production Overrides (Optional)
1. Copy `docker-compose.prod.yml` if needed:
     $ cp docker-compose.prod.yml.example docker-compose.prod.yml
     # Edit with production-specific settings (e.g., no host-port binding).

2. Bring up in prod-like mode:
     $ docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d

