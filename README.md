Project Overview

This project is a full-stack CRUD application built using the MEAN stack:
MongoDB for database
Express.js and Node.js for backend REST APIs
Angular 15 for frontend
Docker for containerization
Docker Compose for multi-container orchestration
Nginx for serving the frontend and handling routing
GitHub Actions for CI/CD automation

The application allows users to create, retrieve, update, delete, and search tutorials.

Application Architecture
The system follows a containerized microservice-style architecture:
User → Nginx (Frontend) → Backend API → MongoDB
All services run as independent Docker containers and communicate via Docker networking.

Containerization
The application is containerized using Docker with separate Dockerfiles for frontend and backend.

Services include:
MongoDB container
Backend container (Node.js / Express)
Frontend container (Angular production build served via Nginx)

Build Containers
-docker compose build

Run Containers
-docker compose up

Application Access
Frontend: http://localhost
Backend API: http://localhost:8080

Database Configuration
MongoDB runs as a Docker container.
The backend connects using the Docker service name:
mongodb://mongo:27017/dd_db
Docker Compose networking ensures proper inter-container communication.

Nginx Configuration
Nginx is used to serve the Angular production build and handle client-side routing.
Key configuration:
location / {
  try_files $uri $uri/ /index.html;
}
The application is exposed via port 80.

CI/CD Pipeline
GitHub Actions is used to implement the CI/CD pipeline.
The pipeline performs the following tasks automatically on every push to the main branch:
Checkout repository
Authenticate with Docker Hub
Build backend Docker image
Build frontend Docker image
Push images to Docker Hub

Docker images:
dockerhubusername/backend:latest
dockerhubusername/frontend:latest
Registry: Docker Hub

Docker Image Build & Push
Docker images are built and pushed automatically via GitHub Actions.
This ensures consistent builds and reproducible deployments.

Deployment
The application is deployed using Docker Compose.

Containers include:
MongoDB
Backend API
Frontend (Angular + Nginx)

All services communicate over Docker’s internal network.

Screenshots
I was unable to take screenshots as i did it in a hurry, my apologies.

Infrastructure Details

Environment components:
Docker Engine
Docker Compose
MongoDB Container

Backend API Container
Frontend Container (Angular + Nginx)
GitHub Actions CI/CD Pipeline

Conclusion

This project demonstrates:
Full-stack containerization
Multi-container orchestration
Reverse proxy configuration
CI/CD automation
Docker registry integration
