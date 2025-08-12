# HMCTS Developer Challenge – Monorepo
#
# Combined project containing:
# - Backend API (Java Spring Boot)
# - Frontend Client (Node/TypeScript + GOV.UK Frontend)
# - Docker Compose for running both services together

# -----------------------------------
# 🔍 Features
# -----------------------------------
# - Create, update, delete, and view tasks
# - Status tracking: Pending, In Progress, Completed
# - Auto-sort by due date
# - Red due date flag for tasks due today
# - GOV.UK Frontend integration
# - Flash banner notifications for success and error

# -----------------------------------
# 🧱 Architecture
# -----------------------------------
# | Component   | Purpose                                 | Tech Stack                               |
# |-------------|-----------------------------------------|-------------------------------------------|
# | Frontend    | Task management UI                      | Node.js, TypeScript, Nunjucks, GOV.UK UI |
# | Backend     | REST API for tasks                      | Java 17, Spring Boot, Gradle              |
# | Database    | Task persistence                        | In-memory / Configurable DB               |
# | Container   | Unified dev environment                 | Docker, Docker Compose                    |
#
# Related repos:
# https://github.com/SadaqueKhanProjects/hmcts-tasks-frontend-client
# https://github.com/SadaqueKhanProjects/hmcts-tasks-backend-api

# -----------------------------------
# 🛠️ Tech Stack
# -----------------------------------
# | Category       | Tools / Frameworks                   |
# |----------------|--------------------------------------|
# | Language       | Java 17, TypeScript                  |
# | Backend        | Spring Boot, Gradle                  |
# | Frontend       | Node.js, Nunjucks, GOV.UK Frontend   |
# | Container      | Docker, Docker Compose               |
# | Testing        | Jest, CodeceptJS                     |
# | Build System   | Gradle (backend), Yarn (frontend)    |
# | Version Control| Git + Submodules                     |

# -----------------------------------
# 🚀 Getting Started
# -----------------------------------

# 1️⃣ Clone with submodules
git clone --recurse-submodules https://github.com/SadaqueKhanProjects/hmcts-dts-developer-challenge.git
cd hmcts-dts-developer-challenge

# If you forgot --recurse-submodules:
git submodule update --init --recursive

# 2️⃣ Configure environment (optional)
# Create a .env file in the root:
cat <<EOL > .env
FRONTEND_PORT=3000
BACKEND_PORT=4000
BACKEND_URL=http://backend:4000
EOL

# 3️⃣ Run with Docker Compose
docker compose up --build
# Frontend → http://localhost:3000
# Backend  → http://localhost:4000

# Stop services
docker compose down

# -----------------------------------
# 🧪 Smoke Test
# -----------------------------------
# Create a task
curl -X POST http://localhost:4000/tasks \
  -H "Content-Type: application/json" \
  -d '{"title":"Example","description":"Demo task","status":"PENDING","caseNumber":"CN-001"}'

# List tasks
curl http://localhost:4000/tasks

# -----------------------------------
# 🔄 Updating Submodules
# -----------------------------------
git pull --rebase
git submodule update --remote --merge

# Commit updated pointers
git add hmcts-tasks-frontend-client hmcts-tasks-backend-api
git commit -m "chore: bump submodules to latest SHAs"
git push

# -----------------------------------
# 📂 Project Structure
# -----------------------------------
# /docker-compose.yml
# /.env.example
# /hmcts-tasks-backend-api/       # Java Spring Boot API
# /hmcts-tasks-frontend-client/   # Node/TS GOV.UK Frontend client

# -----------------------------------
# 👤 Author
# -----------------------------------
# Sadaque Khan – https://github.com/SadaqueKhanProjects