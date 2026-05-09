# Acquisitions-API
Based on the sources, here is a comprehensive **GitHub README.md** file for the **Acquisitions API** project developed in the course.

***

# Acquisitions API: Production-Ready DevOps Project

**Acquisitions** is a real-world API designed for **buying and selling SAS businesses**. This project demonstrates a complete DevOps lifecycle, moving from local development fundamentals to a production-ready backend that is automated, scalable, and secure.

## 🚀 Features

*   **Authentication & Authorization:** Secure JWT-based auth with Role-Based Access Control (RBAC) for admins and users.
*   **Business Management:** Full CRUD functionality for business listings and deal management to track transactions from pending to completed.
*   **Security:** Real-time protection against bots, spam, and common attacks using **Arkjet**.
*   **Validation:** Strict request validation using **Zod**.
*   **Logging:** Structured logging with **Winston** and request monitoring with **Morgan**.
*   **Database:** Serverless Postgres powered by **Neon DB** and type-safe queries with **Drizzle ORM**.
*   **Containerisation:** Fully dockerised environment for consistent development and production.
*   **Orchestration:** Local Kubernetes setup using **MiniKube** for scaling and self-healing.
*   **CI/CD:** Automated pipelines for linting, testing, and Docker builds via **GitHub Actions**.

## 🛠️ Tech Stack

*   **Runtime:** Node.js
*   **Framework:** Express.js
*   **Database:** Postgres (Neon DB)
*   **ORM:** Drizzle ORM
*   **Security:** Arkjet
*   **Containerisation:** Docker & Docker Compose
*   **Orchestration:** Kubernetes (K8s)
*   **Testing:** Jest & Supertest
*   **Environment:** Warp AI Terminal

## 📁 Project Structure

The project follows a **Model-View-Controller (MVC)** paradigm for clean separation of concerns:

```text
src/
├── config/       # Database, logger, and security configurations
├── controllers/  # Request handling logic
├── middleware/   # Auth, logging, and security middlewares
├── models/       # Database schemas and Drizzle models
├── routes/       # API endpoint definitions
├── services/     # Database interaction logic
├── utils/        # Utility functions (JWT, cookies, formatting)
└── validations/  # Zod validation schemas
tests/            # Jest test suites
```

## ⚙️ Getting Started

### Prerequisites
*   **Node.js** installed.
*   **Docker Desktop** for containerisation.
*   **MiniKube** and **kubectl** for Kubernetes features.
*   Accounts for **Neon DB** and **Arkjet**.

### Installation
1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd acquisitions
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Set up environment variables:
   Create a `.env` file in the root and add your keys for `DATABASE_URL`, `JWT_SECRET`, and `ARCJET_KEY`.

4. Run database migrations:
   ```bash
   npm run db:generate
   npm run db:migrate
   ```

## 📜 Available Scripts

*   `npm run dev`: Starts the local development server with hot-reload.
*   `npm run dev:docker`: Starts the app and a local Neon proxy in Docker containers.
*   `npm run test`: Executes the Jest test suite.
*   `npm run lint`: Checks for code quality and formatting issues.
*   `npm run lint:fix`: Automatically fixes linting errors.
*   `npm run db:studio`: Opens the Drizzle GUI to explore your database.

## 🚢 Deployment

### Docker
To build and run the production container:
```bash
docker build -t acquisitions-api .
docker run -p 3000:3000 acquisitions-api
```

### Kubernetes (Local)
1. Start MiniKube: `minikube start`.
2. Apply manifests: `kubectl apply -f k8s/`.
3. Access service: `minikube service acquisitions-api`.

## 🧪 CI/CD
This project uses **GitHub Actions** to automate workflows on every push to `main`:
*   **Lint & Format:** Ensures code style consistency.
*   **Testing:** Runs the automated test suite and generates coverage reports.
*   **Build & Push:** Packages the application into a Docker image and pushes it to Docker Hub.
