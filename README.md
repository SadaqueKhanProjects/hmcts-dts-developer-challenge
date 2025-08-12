# HMCTS DTS Developer Challenge

**HMCTS DTS Developer Challenge** is a monorepo containing both the **frontend** and **backend** for the HMCTS Tasks application.  
It includes a root-level **Docker Compose** setup to run the entire application in one command.

---

## 📂 Repository Structure

```
hmcts-dts-developer-challenge/
├── docker-compose.yml              # Runs frontend + backend together
├── hmcts-tasks-backend-api/        # Java Spring Boot backend
└── hmcts-tasks-frontend-client/    # Node/TypeScript frontend
```

---

## 🛠️ Tech Stack

| Component  | Tools / Frameworks                               |
|------------|--------------------------------------------------|
| Backend    | Java 17, Spring Boot, Gradle, REST API           |
| Frontend   | Node.js, TypeScript, Nunjucks, GOV.UK Design System |
| Container  | Docker, Docker Compose                           |

---

## 🚀 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/SadaqueKhanProjects/hmcts-dts-developer-challenge.git
cd hmcts-dts-developer-challenge
```

---

### 2️⃣ Set Environment Variables

Create a `.env` file in the root directory (next to `docker-compose.yml`).  
Example:

```bash
# Example environment variables
SPRING_PROFILES_ACTIVE=dev
BACKEND_PORT=8080
FRONTEND_PORT=3000
```

---

### 3️⃣ Run with Docker Compose

```bash
docker-compose up --build
```

This will:
- Build and run the **backend API** on `http://localhost:8080`
- Build and run the **frontend** on `http://localhost:3000`

---

### 4️⃣ Stopping the App

```bash
docker-compose down
```

---

## 🧪 Running Services Individually

If you want to run **only the backend**:

```bash
cd hmcts-tasks-backend-api
./gradlew bootRun
```

If you want to run **only the frontend**:

```bash
cd hmcts-tasks-frontend-client
yarn install
yarn start
```

---

## 📄 License

This project is licensed under the MIT License.
