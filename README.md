# Task Manager — Full Stack Starter (Java Spring Boot + React)

A minimal, working full-stack CRUD app: React frontend talks to a Spring Boot
REST API, which stores tasks in an in-memory H2 database. Good as a first
end-to-end project.

## Folder structure

```
task-manager-app/
├── backend/     Spring Boot REST API (Java)
└── frontend/    React UI
```

## Prerequisites

- Java 17+ and Maven (or use the included `mvnw` if you add one — this
  project assumes you have Maven installed: `mvn -v` to check)
- Node.js 18+ and npm

## Running the backend

```bash
cd backend
mvn spring-boot:run
```

- API runs at `http://localhost:8080`
- Endpoints:
  - `GET    /api/tasks`
  - `GET    /api/tasks/{id}`
  - `POST   /api/tasks`
  - `PUT    /api/tasks/{id}`
  - `DELETE /api/tasks/{id}`
- H2 console (view the DB in browser): `http://localhost:8080/h2-console`
  (JDBC URL: `jdbc:h2:mem:taskdb`, user: `sa`, no password)

## Running the frontend

In a separate terminal:

```bash
cd frontend
npm install
npm start
```

- Opens at `http://localhost:3000`
- Already configured to call the backend at `http://localhost:8080`

## What to try next (once it's running)

1. **Switch H2 → MySQL/PostgreSQL** — instructions are commented in
   `backend/src/main/resources/application.properties`. This is the natural
   next step once you're comfortable with the basics.
2. **Add authentication** — Spring Security + JWT, so users have to log in
   before managing tasks.
3. **Add validation feedback** — show field-level errors in the React form
   instead of a generic error message.
4. **Deploy it** — backend to Render/Railway, frontend to Vercel/Netlify.
5. **Write a couple of tests** — a `TaskControllerTest` on the backend is a
   good first testing exercise.

## Why this stack (quick recap)

- **Spring Boot** — exposes the REST API and business logic
- **Spring Data JPA + H2** — persistence layer (swap H2 for a real DB later)
- **React (with axios)** — frontend that consumes the REST API
- This mirrors the "Java FSD" pattern discussed: frontend and backend are
  fully decoupled and only communicate over HTTP/JSON, the same pattern
  you'd use to plug in a data-science/ML microservice later on.
