# Claims Core

Claims Core is a full-stack application built using Java 21, Spring Boot 4.2.0, React 18, and TypeScript. The project is structured around modular backend features and a React-based frontend to provide a scalable foundation for claims-related business operations.

The application uses PostgreSQL for relational data storage, Redis for caching, and RabbitMQ for asynchronous messaging. Docker Compose provides a consistent local development environment for the infrastructure services.

## Technology Stack

### Backend
- Java 21
- Spring Boot 4.2.0
- Spring Web
- Spring Data JPA
- Spring Security
- Spring Boot Validation
- Spring Data Redis
- Flyway Database Migration
- Lombok
- Maven

### Frontend
- React 18
- TypeScript
- Vite
- HTML5
- CSS3
- JavaScript

### Database & Infrastructure
- PostgreSQL
- Redis
- RabbitMQ
- Docker
- Docker Compose

### Testing & CI/CD
- JUnit 5
- Mockito
- Testcontainers
- GitHub Actions

## Project Structure

```text
Claims Core/
│
├── .github/
│   └── workflows/
│       └── ci.yml
│
├── docker-compose.yml
│
├── backend/
│   └── backend/
│       ├── .mvn/
│       │   └── wrapper/
│       ├── .settings/
│       ├── mvnw
│       ├── mvnw.cmd
│       ├── pom.xml
│       │
│       └── src/
│           ├── main/
│           │   ├── java/com/example/backend/
│           │   │   ├── BackendApplication.java
│           │   │   ├── auth/
│           │   │   ├── customer/
│           │   │   ├── invoice/
│           │   │   ├── numbering/
│           │   │   └── tax/
│           │   │
│           │   └── resources/
│           │       ├── application.properties
│           │       ├── db/migration/
│           │       │   └── V1__init.sql
│           │       ├── static/
│           │       └── templates/
│           │
│           └── test/java/com/example/backend/
│               ├── BackendApplicationTests.java
│               ├── TestBackendApplication.java
│               └── TestcontainersConfiguration.java
│
├── frontend/
│   └── frontend/
│       ├── public/
│       ├── src/
│       │   ├── assets/
│       │   ├── components/
│       │   ├── features/
│       │   │   ├── auth/
│       │   │   ├── customer/
│       │   │   ├── invoice/
│       │   │   └── numbering/
│       │   ├── hooks/
│       │   ├── services/
│       │   ├── types/
│       │   ├── utils/
│       │   ├── App.tsx
│       │   ├── App.css
│       │   ├── index.css
│       │   └── main.tsx
│       ├── package.json
│       ├── package-lock.json
│       └── vite.config.ts
│
└── README.md
```

## Prerequisites

Make sure the following tools are installed:

- JDK 21
- Maven
- Node.js and npm
- Docker Desktop
- Git
- Spring Tool Suite (STS) or IntelliJ IDEA
- Visual Studio Code

## Getting Started

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

Navigate to the project root:

```bash
cd "Claims Core"
```

### 2. Start Infrastructure Services

Start PostgreSQL, Redis, and RabbitMQ using Docker Compose:

```bash
docker compose up -d
```

Check container status:

```bash
docker compose ps
```

View service logs:

```bash
docker compose logs
```

### 3. Run the Backend

Navigate to the Spring Boot application directory:

```bash
cd backend/backend
```

Run the application on Windows:

```bash
mvnw.cmd spring-boot:run
```

Run on Linux/macOS:

```bash
./mvnw spring-boot:run
```

Backend application URL:

```text
http://localhost:8080
```

### 4. Run the Frontend

Open another terminal from the repository root.

Navigate to the React application directory:

```bash
cd frontend/frontend
```

Install dependencies:

```bash
npm install
```

Start the Vite development server:

```bash
npm run dev
```

Frontend application URL:

```text
http://localhost:5173
```

## Infrastructure Services

| Service | Port | Purpose |
|---|---:|---|
| PostgreSQL | 5432 | Relational database |
| Redis | 6379 | Caching |
| RabbitMQ | 5672 | Message broker |
| RabbitMQ Management | 15672 | Management dashboard |
| Spring Boot | 8080 | Backend API |
| React + Vite | 5173 | Frontend application |

## Backend Modules

The backend follows a feature-based package structure.

| Module | Responsibility |
|---|---|
| auth | Authentication and security |
| customer | Customer management |
| invoice | Invoice management |
| numbering | Invoice numbering management |
| tax | Tax management |

Each feature maintains its own relevant controllers, services, repositories, entities, and DTOs.

## Database Migration

Flyway manages database schema migrations.

Migration directory:

```text
backend/backend/src/main/resources/db/migration/
```

Example migration files:

```text
db/migration/
├── V1__init.sql
├── V2__create_customers.sql
├── V3__create_invoices.sql
└── V4__create_tax_tables.sql
```

Migration scripts are executed by Flyway according to the configured database connection and migration settings.

## Testing

Run backend tests on Windows:

```bash
cd backend/backend
mvnw.cmd test
```

Run frontend build:

```bash
cd frontend/frontend
npm run build
```

Backend testing uses JUnit and Testcontainers for unit and integration testing.

## Docker Commands

Start infrastructure:

```bash
docker compose up -d
```

Stop infrastructure:

```bash
docker compose down
```

View running containers:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs -f
```

Stop containers and remove database volumes:

```bash
docker compose down -v
```

**Warning:** The `-v` option deletes persisted database data.

## Git Workflow

Create a feature branch:

```bash
git checkout -b feature/your-feature-name
```

Stage changes:

```bash
git add .
```

Commit changes:

```bash
git commit -m "Add your feature description"
```

Push changes:

```bash
git push origin feature/your-feature-name
```

Create a Pull Request on GitHub for review and integration.

## CI/CD

GitHub Actions configuration is maintained at:

```text
.github/workflows/ci.yml
```

The CI workflow is intended to automate backend builds, backend tests, and frontend validation.

## Contribution Guidelines

1. Follow the existing project folder structure.
2. Work on separate feature branches.
3. Write clean, maintainable, and reusable code.
4. Add appropriate unit and integration tests.
5. Follow meaningful Git commit messages.
6. Never commit passwords, API keys, or sensitive configuration.
7. Submit Pull Requests for code review.

## License

Internal project. All rights reserved.

## Note on Spring Boot Version Selection

**Spring Boot Version: 4.2.0**

I selected Spring Boot 4.2.0 because Spring Boot 3.0.0 was not available in the Spring Initializr version options in my Spring Tool Suite (STS) environment when I created the project. Therefore, I selected Spring Boot 4.2.0, which was available as a stable release option.

This version was selected to proceed with the project setup while using the available Spring Boot tooling.

**Note:** The original task specifies Spring Boot 3. Please confirm with the project manager that Spring Boot 4.2.0 is acceptable, as it is a different major version and may have compatibility differences.
