## DevOps Setup 

### Run Locally 
docker compose up --build -d 

Access the app on port 80: 
  -  http://localhost — React frontend 
  -  http://localhost/api/ping — .NET backend API 

### Services 
  -  frontend — React + Vite app served by Nginx 
  -  backend — .NET 10 minimal API with a /api/ping endpoint 
  -  nginx — Reverse proxy that routes / to the frontend and /api/ to the backend. Only this service exposes a port to the host (port 80). 

### CI/CD Pipeline 
On every push to main, GitHub Actions: 
1. Builds and pushes the frontend and backend Docker images to Docker Hub 
2. SSHes into the QA server 
3. Pulls the latest images and runs docker compose up -d 
