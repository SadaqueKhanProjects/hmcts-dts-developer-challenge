# HMCTS DTS Developer Challenge

**HMCTS DTS Developer Challenge** is a monorepo containing both the **frontend** and **backend** for the HMCTS Tasks application.  
It includes a root-level **Docker Compose** setup to run the entire application with a single command.

---

## 📂 Repository Structure

```

hmcts-dts-developer-challenge/
├── docker-compose.yml              # Runs backend + database together
├── hmcts-tasks-backend-api/        # Java Spring Boot backend
└── hmcts-tasks-frontend-client/    # Node/TypeScript frontend

````

---

## 🛠️ Tech Stack

| Component  | Tools / Frameworks                               |
|------------|--------------------------------------------------|
| Backend    | Java 21, Spring Boot, Gradle, REST API, PostgreSQL |
| Frontend   | Node.js, TypeScript, Nunjucks, GOV.UK Design System |
| Container  | Docker, Docker Compose                           |
| Database   | PostgreSQL 16                                    |

---

## 🚀 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/SadaqueKhanProjects/hmcts-dts-developer-challenge.git
cd hmcts-dts-developer-challenge
````

---

### 2️⃣ Install Prerequisites

Ensure the following are installed on your system:

* **[Docker](https://docs.docker.com/get-docker/)** (includes Docker Compose)
* **[Java 21 JDK](https://adoptium.net/temurin/releases/)** (for local backend runs)
* **[Gradle](https://gradle.org/install/)** (optional, backend has wrapper)
* **[Node.js 18+](https://nodejs.org/en)** & **Yarn** (for local frontend runs)

Check versions:

```bash
docker --version
docker compose version
java -version
node -v
yarn -v
```

---

### 3️⃣ Set Environment Variables

#### Root `.env` (used by Docker Compose)

Create a `.env` in the root directory:

```bash
SERVER_PORT=4000

DB_HOST=postgres
DB_PORT=5432
DB_NAME=tasks
DB_USER_NAME=app_user
DB_PASSWORD=super_secure_password_123

FRONTEND_ORIGIN=http://localhost:3100
```

#### Frontend `.env` (for local runs)

Create a `.env` inside `hmcts-tasks-frontend-client/`:

```bash
PORT=3100
NODE_ENV=development
BACKEND_URL=http://localhost:4000
```

> If running frontend in Docker, set:
> `BACKEND_URL=http://backend:4000`

---

### 4️⃣ Run with Docker Compose

```bash
docker compose up --build
```

This will:

* Start **PostgreSQL** on `localhost:5432`
* Start **backend API** on `http://localhost:4000`

---

### 5️⃣ Stopping the App

```bash
docker compose down
```

---

## 🧪 Running Services Individually

Run **only the backend**:

```bash
cd hmcts-tasks-backend-api
./gradlew bootRun
```

Run **only the frontend**:

```bash
cd hmcts-tasks-frontend-client
yarn install
yarn start
```

---

## 🔍 Verifying Services

Check backend health:

```bash
curl http://localhost:4000/actuator/health
```

Test API:

```bash
curl http://localhost:4000/tasks
```

---

## 🛠 Troubleshooting

| Issue                                  | Cause                                     | Fix                                           |
| -------------------------------------- | ----------------------------------------- | --------------------------------------------- |
| Port already in use                    | Another service is using `4000`/`3100`    | Stop the service or change `.env` ports       |
| Frontend CORS errors                   | Wrong `FRONTEND_ORIGIN` in `.env`         | Update `.env` and restart backend             |
| Frontend in Docker can’t reach backend | Using `localhost` instead of service name | Use `http://backend:4000`                     |
| DB connection failed                   | Wrong credentials or DB not ready         | Check `.env` and ensure `postgres` is running |

---

## 📄 License

This project is licensed under the MIT License.

```