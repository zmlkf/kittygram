# Kittygram - A Social Network for Cat Lovers
[![Main Kittygram workflow](https://github.com/zmlkf/kittygram_final/actions/workflows/main.yml/badge.svg?branch=main)](https://github.com/zmlkf/kittygram_final/actions/workflows/main.yml)

## Description
Kittygram is an online platform designed for cat owners. Here, pet owners can share their furry friends, add their birth year, photos, and achievements. You can also admire other cats that are already on the platform.

## Contributions
This project was created by [Roman Zemliakov](https://github.com/zmlkf). My contributions to this project include:
1. Writing the GitHub Actions workflow file (`kittygram_workflow.yml`) which includes:
   - Running tests and code style checks (flake8 and Django tests).
   - Building and pushing Docker images for the backend, frontend, and gateway to DockerHub.
   - Deploying the project to a remote server using docker-compose.
   - Sending notifications to Telegram about deployment results.
2. Creating Dockerfiles for the backend and nginx.
3. Creating the `docker-compose.yml` file to run all project services.

## Cloning and Running the Project

### Cloning the Repository
First, clone the repository to your local machine:
```bash
git clone git@github.com:zmlkf/kittygram_final.git
cd kittygram_final
```

### Setting Up Environment Variables
Create a `.env` file in the root directory of the project and set the necessary environment variables. For example:
```
POSTGRES_USER=your_postgres_user
POSTGRES_PASSWORD=your_postgres_password
POSTGRES_DB=your_postgres_db
```

### Building and Running the Project with Docker Compose
Ensure you have Docker and Docker Compose installed on your machine. Then, run the following commands:
```bash
docker-compose up --build
```

This will build the Docker images and start the containers for the database, backend, frontend, and nginx gateway.


## Deploying the Project
The project is set up for continuous deployment using GitHub Actions. On every push to the main branch, the following steps are performed automatically:
1. Tests and linting are run.
2. Docker images are built and pushed to DockerHub.
3. The project is deployed to a remote server using docker-compose.
4. A notification is sent to Telegram about the deployment status.

To deploy the project manually, you can use the provided GitHub Actions workflow or copy the `docker-compose.production.yml` file to your server and run:
```bash
sudo docker compose -f docker-compose.production.yml pull
sudo docker compose -f docker-compose.production.yml down
sudo docker compose -f docker-compose.production.yml up -d
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```

## Author
This project was created by [Roman Zemliakov](https://github.com/zmlkf).
```

This `README.md` file provides a comprehensive overview of the project, your contributions, and instructions for cloning and running the project.