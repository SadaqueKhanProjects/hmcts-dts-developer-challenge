Got it — here’s your monorepo README in the same clean, copy-pasteable syntax style as your PostcodeEats example.

# HMCTS Developer Challenge – Monorepo

**HMCTS Developer Challenge – Monorepo** is a combined project containing:

- **Backend API** – Java Spring Boot application for managing tasks  
- **Frontend Client** – Node/TypeScript + GOV.UK Frontend interface for task management  
- **Docker Compose** – to run both services together in one command

The backend and frontend are maintained as **separate GitHub repos** but are included here as **Git submodules** for unified execution.

---

## 🔍 Features

- Create, update, delete, and view tasks
- Status tracking with **Pending**, **In Progress**, and **Completed** states
- Tasks automatically sorted by due date
- Red due date flag when a task is due today
- GOV.UK Frontend design system integration
- Flash banner notifications for success and error events

---

## 🧱 Architecture

| Component   | Purpose                                 | Tech Stack                               |
|-------------|-----------------------------------------|-------------------------------------------|
| Frontend    | User interface for task management      | Node.js, TypeScript, Nunjucks, GOV.UK UI |
| Backend     | REST API to store & manage tasks        | Java 17, Spring Boot, Gradle              |
| Database    | Task persistence                        | In-memory / Configurable DB               |
| Container   | Unified local development environment   | Docker, Docker Compose                    |

📎 Related repos:  
- [Frontend Client](https://github.com/SadaqueKhanProjects/hmcts-tasks-frontend-client)  
- [Backend API](https://github.com/SadaqueKhanProjects/hmcts-tasks-backend-api)  

---

## 🛠️ Tech Stack

| Category       | Tools / Frameworks                   |
|----------------|--------------------------------------|
| Language       | Java 17, TypeScript                  |
| Backend        | Spring Boot, Gradle                  |
| Frontend       | Node.js, Nunjucks, GOV.UK Frontend   |
| Container      | Docker, Docker Compose               |
| Testing        | Jest, CodeceptJS                     |
| Build System   | Gradle (backend), Yarn (frontend)    |
| Version Control| Git + Submodules                     |

---

## 🚀 Getting Started

### 1️⃣ Clone with submodules
```bash
git clone --recurse-submodules https://github.com/SadaqueKhanProjects/hmcts-dts-developer-challenge.git
cd hmcts-dts-developer-challenge

If you forgot --recurse-submodules:

git submodule update --init --recursive

2️⃣ Configure environment (optional)

Create a .env in the root:

FRONTEND_PORT=3000
BACKEND_PORT=4000
BACKEND_URL=http://backend:4000

3️⃣ Run with Docker Compose

docker compose up --build

	•	Frontend → http://localhost:3000
	•	Backend  → http://localhost:4000

Stop services:

docker compose down


⸻

🧪 Smoke Test

Create a task:

curl -X POST http://localhost:4000/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Example","description":"Demo task","status":"PENDING","caseNumber":"CN-001"}'

List tasks:

curl http://localhost:4000/tasks


⸻

🔄 Updating Submodules

Pull latest main repo and submodules:

git pull --rebase
git submodule update --remote --merge

Commit updated pointers:

git add hmcts-tasks-frontend-client hmcts-tasks-backend-api
git commit -m "chore: bump submodules to latest SHAs"
git push


⸻

📂 Project Structure

/docker-compose.yml
/.env.example
/hmcts-tasks-backend-api/          # Java Spring Boot API
/hmcts-tasks-frontend-client/      # Node/TS GOV.UK Frontend client


⸻

👤 Author

Sadaque Khan – GitHub

If you want, I can now **also make matching README.md files** for the **frontend** and **backend** repos so the examiner sees setup instructions no matter which repo they open first. That will make the exam run smoother.