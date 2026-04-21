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

### 🏗️ [docker-jenkins](./docker-jenkins)
Template to run a Jenkins CI/CD server locally, ready for pipelines and integrations.

- **Image**: Jenkins (`jenkins/jenkins:latest`).
- **Persistence**: Employs a Docker volume (`jenkins_data`) to ensure all data, plugins, and job history are saved across container restarts.
- **Customizable**: Includes a `Dockerfile` switching to `root` briefly to install additional useful packages (like `curl`, `git`, `unzip`) before switching back to the default `jenkins` user.

**How to use:**
```bash
# Navigate to the directory
cd docker-jenkins

# Build the image and start the container in background
docker compose up -d --build

# Retrieve the initial admin password from logs
docker logs jenkins-server

# Stop the service (preserves your data and plugins)
docker compose down
```
> **Access:** Once running, navigate to `http://localhost:8080`, and paste the admin password found in the logs to complete the first-time setup!

---

*Add new folders here as you expand the project (e.g., `docker-mysql`, `docker-redis`, `docker-node-app`, etc).*
