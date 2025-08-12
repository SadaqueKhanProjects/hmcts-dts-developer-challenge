# HMCTS DTS Developer Challenge

The **HMCTS DTS Developer Challenge** is a full-stack task management application built to HMCTS design standards.  
It features a **Java Spring Boot backend** for secure, REST-based task operations and a **Node.js/Express frontend** styled with the GOV.UK Design System for an accessible, user-friendly interface.  
The system supports **listing, creating, viewing, updating, and deleting tasks**, with validation and date handling aligned to HMCTS best practices.

This repository is designed for quick setup in local development environments using **Docker Compose**, ensuring consistent builds and eliminating dependency conflicts.  
Developers can run the backend, frontend, and database together in containers, or start each service individually for debugging and feature work.

---

## ✨ Features

- **Task Management** – Create, list, view, update, and delete tasks.
- **Form Validation** – Enforces required fields, maximum description length, and due date rules.
- **Accessible Design** – GOV.UK Design System styling for compliance with accessibility guidelines.
- **Due Date Highlighting** – Visual indicators for tasks due today.
- **Containerised Deployment** – Run backend and database via Docker Compose for a consistent environment.
- **Flexible Development Setup** – Run services together or individually to suit development workflows.
- **Environment Configurable** – Ports, database settings, and API URLs managed via `.env` files.

---

## 📂 Repository Structure

```

hmcts-dts-developer-challenge/
├── docker-compose.yml              # Orchestrates backend and database
├── .env.example                     # Template for environment variables
├── hmcts-tasks-backend-api/         # Java Spring Boot backend service
└── hmcts-tasks-frontend-client/     # Node.js/TypeScript frontend client

````

---

## 🛠 Tech Stack

| Component  | Tools / Frameworks                               |
|------------|--------------------------------------------------|
| Backend    | Java 21, Spring Boot, Gradle (wrapper), REST API, PostgreSQL |
| Frontend   | Node.js 18/20 LTS, TypeScript, Express, Nunjucks, GOV.UK Frontend |
| Container  | Docker, Docker Compose                           |
| Database   | PostgreSQL 16                                    |

---

## 📋 Prerequisites

Ensure the following tools are installed before starting:

| Tool            | Required Version | Check Command                 |
|-----------------|------------------|--------------------------------|
| Docker Desktop  | 4.30+            | `docker --version`            |
| Docker Compose  | v2.24+           | `docker compose version`      |
| Java JDK        | 21               | `java -version`               |
| Gradle          | (wrapper)        | `./gradlew -v`                |
| Node.js         | 18.x or 20.x     | `node -v`                     |
| npm             | 9+               | `npm -v`                      |
| Yarn            | **3.8.2**        | `yarn -v`                     |
| PostgreSQL      | 16               | (Docker image)                 |

> **Note:** The frontend requires **Yarn 3.8.2** for compatibility.

---

## 🚀 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/SadaqueKhanProjects/hmcts-dts-developer-challenge.git
cd hmcts-dts-developer-challenge
````

If using submodules:

```bash
git submodule update --init --recursive
```

---

### 2️⃣ Configure Environment Variables

1. Copy the provided example file to `.env` in the project root:

   ```bash
   cp .env.example .env
   ```
2. Update the values as required for your local environment.
3. For local frontend runs, also create a `.env` file inside `hmcts-tasks-frontend-client/` using the provided example in that directory.

---

### 3️⃣ Run with Docker Compose

To start the backend API and database together:

```bash
docker compose up --build
```

* Backend API: `http://localhost:<SERVER_PORT>`
* PostgreSQL: `localhost:<DB_PORT>`

To stop all containers:

```bash
docker compose down
```

---

### 4️⃣ Running Services Individually

**Backend only (with database in Docker):**

```bash
docker compose up postgres
cd hmcts-tasks-backend-api
./gradlew bootRun
```

**Frontend only:**

```bash
cd hmcts-tasks-frontend-client
yarn install
yarn start
```

---

## 🔍 Verifying Services

**Check backend health:**

```bash
curl http://localhost:<SERVER_PORT>/actuator/health
```

**Test API endpoint:**

```bash
curl http://localhost:<SERVER_PORT>/tasks
```

---

## 🛠 Troubleshooting

| Issue                                   | Possible Cause                          | Solution                                                |
| --------------------------------------- | --------------------------------------- | ------------------------------------------------------- |
| Port already in use                     | Another process is using the port       | Stop the conflicting process or change port in `.env`   |
| Frontend CORS errors                    | Incorrect `FRONTEND_ORIGIN` value       | Update `.env` and restart backend                       |
| Frontend in Docker cannot reach backend | Using `localhost` inside container      | Use backend service name from `docker-compose.yml`      |
| Database connection failed              | Incorrect configuration or DB not ready | Check `.env` and ensure `postgres` container is running |

---

## 📄 License

This project is licensed under the MIT License.
