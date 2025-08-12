# HMCTS DTS Developer Challenge

**HMCTS DTS Developer Challenge** is a monorepo containing both the **frontend** and **backend** for the HMCTS Tasks application.  
It includes a root-level **Docker Compose** setup to run the entire application with a single command.

---

## 📂 Repository Structure

```

hmcts-dts-developer-challenge/
├── docker-compose.yml              # Runs backend + database together
├── .env.example                     # Example environment variables
├── hmcts-tasks-backend-api/         # Java Spring Boot backend
└── hmcts-tasks-frontend-client/     # Node/TypeScript frontend

````

---

## 🛠️ Tech Stack

| Component  | Tools / Frameworks                               |
|------------|--------------------------------------------------|
| Backend    | Java 21, Spring Boot, Gradle (wrapper), REST API, PostgreSQL |
| Frontend   | Node.js 18/20 LTS, TypeScript, Express, Nunjucks, GOV.UK Frontend |
| Container  | Docker, Docker Compose                           |
| Database   | PostgreSQL 16                                    |

---

## 📋 Prerequisites

Install the following before starting:

| Tool            | Required Version | Check Command                 |
|-----------------|------------------|--------------------------------|
| Docker Desktop  | 4.30+            | `docker --version`            |
| Docker Compose  | v2.24+           | `docker compose version`      |
| Java JDK        | 21               | `java -version`               |
| Gradle          | (wrapper)        | `./gradlew -v`                 |
| Node.js         | 18.x or 20.x     | `node -v`                     |
| npm             | 9+               | `npm -v`                      |
| Yarn            | **3.8.2**        | `yarn -v`                     |
| PostgreSQL      | 16               | (via Docker image)            |

> ⚠️ The frontend requires **Yarn 3.8.2** to execute correctly.

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

### 2️⃣ Set Environment Variables

#### Root `.env` (used by Docker Compose)

Create in the project root:

```env
SERVER_PORT=4000

DB_HOST=postgres
DB_PORT=5432
DB_NAME=tasks
DB_USER_NAME=app_user
DB_PASSWORD=super_secure_password_123

FRONTEND_ORIGIN=http://localhost:3100
```

#### Frontend `.env` (for local runs)

Create in `hmcts-tasks-frontend-client/`:

```env
PORT=3100
NODE_ENV=development
BACKEND_URL=http://localhost:4000
```

> If running the frontend in Docker, set `BACKEND_URL=http://backend:4000`.

---

### 3️⃣ Run with Docker Compose

```bash
docker compose up --build
```

This will:

* Start **PostgreSQL** on `localhost:5432`
* Start **backend API** on `http://localhost:4000`

Stop containers:

```bash
docker compose down
```

---

### 4️⃣ Running Services Individually

**Backend only (with DB in Docker):**

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

| Issue                                  | Cause                              | Fix                                                     |
| -------------------------------------- | ---------------------------------- | ------------------------------------------------------- |
| Port already in use                    | Another service is using the port  | Stop the service or change `.env` port                  |
| Frontend CORS errors                   | Wrong `FRONTEND_ORIGIN` in `.env`  | Update `.env` and restart backend                       |
| Frontend in Docker can’t reach backend | Using `localhost` inside container | Use `http://backend:4000`                               |
| DB connection failed                   | Wrong credentials or DB not ready  | Check `.env` and ensure `postgres` container is running |

---

## 📄 License

This project is licensed under the MIT License.

