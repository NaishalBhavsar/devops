# MEAN App Deployment

This repository contains a containerized MEAN (MongoDB, Express, Angular, Node.js) application with CI/CD and cloud deployment.

## Prerequisites
- Docker and Docker Compose installed.
- A Docker Hub account.
- An Ubuntu VM on AWS/Azure (e.g., EC2 t2.micro for free tier).
- GitHub account for CI/CD.
- SSH access to the VM.

## Step-by-Step Setup and Deployment

### 1. Repository Setup
- Create a new GitHub repository (e.g., `mean-app-deployment`).
- Extract `crud-dd-task-mean-app.zip` and push the code to the repo, including the files provided here.

### 2. Containerization
- Dockerfiles are in `backend/` and `frontend/`.
- Build locally: `docker-compose build`.
- Run locally: `docker-compose up`.

### 3. Cloud VM Setup
- Launch an Ubuntu VM (e.g., AWS EC2).
- SSH in and install Docker: `sudo apt update && sudo apt install docker.io docker-compose`.
- Clone the repo: `git clone https://github.com/yourusername/mean-app-deployment.git`.
- Run: `docker-compose up -d`.

### 4. Database
- MongoDB is containerized via Docker Compose.

### 5. CI/CD
- Push to GitHub triggers the workflow in `.github/workflows/ci-cd.yml`.
- It builds/pushes images and SSHs to VM to restart containers.

### 6. Nginx Reverse Proxy
- On VM, install Nginx: `sudo apt install nginx`.
- Copy `nginx.conf` to `/etc/nginx/nginx.conf` and reload: `sudo nginx -t && sudo systemctl reload nginx`.
- App accessible at VM's public IP on port 80.

## Screenshots
- **CI/CD Configuration**: GitHub Actions tab showing workflow runs (e.g., successful build on push).
- **Docker Build/Push**: Docker Hub showing pushed images (e.g., `mean-backend:latest` and `mean-frontend:latest`).
- **Deployment**: VM terminal showing `docker-compose up` output and app running.
- **Working UI**: Browser screenshot of the app at `http://<VM-IP>` (e.g., Angular CRUD interface).
- **Nginx Setup**: Nginx config file and `curl http://<VM-IP>` showing proxied responses.

## Notes
- Adjust ports, DB credentials, and paths as per your app.
- For HTTPS/domain, add SSL certs (not required here).
- Original app README: [Link to original README.md from zip].
