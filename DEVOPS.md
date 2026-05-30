# DSA Pro Tracker — Simple Docker & CI/CD Setup

A simple, direct setup for running the application using Docker and setting up automated testing pipelines.

---

## 1. Local Run Instructions

### Step 1: Prepare Environment Files
Copy the development environment parameters:
```bash
cp backend/.env.production backend/.env
cp frontend/.env.production frontend/.env
```

### Step 2: Build & Start Stack
Run the following single command to build and launch the backend and frontend:
```bash
docker compose up --build -d
```

### Step 3: Access the Application
* **Frontend Application**: [http://localhost:3000](http://localhost:3000)
* **Backend API**: [http://localhost:5000](http://localhost:5000)

To stop running:
```bash
docker compose down
```

---

## 2. CI/CD Pipeline

We have configured an automated GitHub Action inside `.github/workflows/ci.yml`.

### A. Continuous Integration (CI) — Automatic
Every time you **push** code to the `main` or `master` branch:
1. GitHub automatically starts a clean container.
2. It installs dependency packages.
3. It compiles the React application to verify build issues.
4. It dry-runs both the **Frontend Dockerfile** and **Backend Dockerfile** builds.

If everything passes, you get a green checkmark on your commit!

### B. Continuous Delivery (CD) — Manual Pull
For deployment, you will SSH into your production server and run:
```bash
# Pull the latest changes from GitHub
git pull origin main

# Rebuild and restart the containers silently
docker compose up -d --build
```
This is the most reliable, secure, and straightforward CD pipeline for small/medium applications!
