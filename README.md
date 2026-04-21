# Docker Environments

This repository serves as a collection of different Docker configurations (`docker-compose` and `Dockerfile`) designed for various purposes. It's ideal for having templates at hand to quickly spin up development environments, databases, caches, etc.

## 🗂️ Environment Structure

Each folder in this repository represents an independent environment. Below is the detail for each one:

### 🐘 [docker-postgresql](./docker-postgresql)
Template to initialize a local PostgreSQL database, ready to use.

- **Image**: PostgreSQL (official).
- **Persistence**: Employs a Docker volume (`postgres_data_vol`) to ensure data is not lost upon restart.
- **Auto-seed**: Contains an `initdb/` folder with `.sql` files configured to run the first time the container starts. When spun up from scratch, it automatically creates a `users` test table with some initial records.

**How to use:**
```bash
# Navigate to the directory
cd docker-postgresql

# Start the database in background
docker-compose up -d

# View startup logs
docker logs local_postgres

# Stop the service (preserves your data)
docker-compose down

# Completely remove volume and force re-initialization of init.sql
docker-compose down -v
```

---

*Add new folders here as you expand the project (e.g., `docker-mysql`, `docker-redis`, `docker-node-app`, etc).*
