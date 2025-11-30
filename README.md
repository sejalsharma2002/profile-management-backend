# Profile Management System — Backend

A secure backend built using **FastAPI + SQLAlchemy + JWT Authentication** that powers the Profile Management System frontend.

This backend provides authentication, profile management, authorization, and database persistence.

> Part of a full-stack assignment demonstrating authentication, structured APIs, database CRUD operations, and clean architecture.

---------------------------------------------------------------------

## 📌 Table of Contents

- [Project Goals](#project-goals)
- [Tech Stack](#tech-stack)
- [Architecture Decisions](#architecture-decisions)
- [API Features](#api-features)
- [Setup Instructions](#setup-instructions)
- [Environment Configuration](#environment-configuration)
- [Running the Server](#running-the-server)
- [API Endpoints](#api-endpoints)
- [Database Details](#database-details)
- [Frontend Link](#frontend-link)
- [Time Spent](#time-spent)
- [Limitations](#limitations)
- [Summary](#summary)

---------------------------------------------------------------------

## Project Goals

This backend fulfills the required assignment expectations:

- Create and authenticate users securely.
- Manage user profiles (read + update).
- Persist user credentials and profile details in a database.
- Support JWT token handling for protected routes.
- Provide API communication that works across Web + Mobile environments.

---------------------------------------------------------------------

## Tech Stack

| Component | Technology |
|----------|------------|
| Backend Framework | FastAPI |
| Language | Python |
| ORM | SQLAlchemy |
| Database | SQLite |
| Authentication | OAuth2 + JWT |
| Password Security | Passlib + bcrypt |
| Schema Validation | Pydantic |
| Server Runtime | Uvicorn |

---------------------------------------------------------------------

## Architecture Decisions

- **JWT Token Authentication** chosen for mobile and web session handling.
- **SQLite Database** used for simplicity and local development.
- **Password Hashing** implemented using bcrypt for security through Passlib hashing.
- **Token validation** applied on protected endpoints to prevent unauthorized access.
- **CORS Middleware** added to allow communication from mobile clients, local browser, or Expo app.

---------------------------------------------------------------------

## API Features

- [x] User Registration (POST `/auth/signup`)
- [x] User Login with JWT return (POST `/auth/login`)
- [x] Retrieve authenticated user profile (GET `/profile/me`)
- [x] Update name and bio (PUT `/profile/me`)
- [x] Validation, structured error messaging

---------------------------------------------------------------------

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/sejalsharma2002/profile-management-backend.git
cd profile-management-backend
```
2. Create Virtual Environment
```bash
python -m venv venv
```
Windows:
```bash
venv\Scripts\activate
```
3. Install Dependencies
```bash
pip install -r requirements.txt
```

---
## Environment Configuration
Optional .env file values (defaults exist if file is missing):
```bash
SECRET_KEY="your-secret"
ALGORITHM="HS256"
ACCESS_TOKEN_EXPIRE_MINUTES=180
```

---
## Running the Server
### For Desktop / Browser Testing
```bash
uvicorn main:app --reload
```
### For Mobile App Support (Expo / Physical Device)
```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```
Ensure your machine firewall allows access if using mobile.

---
### API Endpoints

| Method | Endpoint       | Purpose                                   |
|--------|---------------|--------------------------------------------|
| POST   | /auth/signup  | Register new user                          |
| POST   | /auth/login   | Authenticate user and return JWT token     |
| GET    | /profile/me   | Fetch authenticated user's profile         |
| PUT    | /profile/me   | Update authenticated user's name and bio   |

Swagger documentation is available at:

```bash
http://127.0.0.1:8000/docs
```
---
## Database Details
### Engine: SQLite (generated automatically as database.db)

### Table(s):

- users (id, name, email, password hash, bio)

### Auto-increment ID enabled (respects deleted rows)

> No manual setup required — database initializes on first run.

---
## Frontend Link
The frontend application that consumes this API is available here:
https://github.com/sejalsharma2002/profile-management-frontend

---
## Time Spent
| Task                                   | Duration |
|----------------------------------------|----------|
| Initial setup + dependencies           | 4 hr     |
| Authentication + JWT implementation    | 3 hrs    |
| Profile CRUD development               | 2 hrs    |
| Testing backend with mobile + web      | 3 hrs    |
| Debugging + refinement                 | 3 hrs    |
| Final documentation                    | 3 hr     |

Total Estimated Time: **18 hours**

---
## Limitations

This backend implements the core requirements of Task #1 from the assignment
(secure signup, login with JWT, and protected profile read/update), but a few
points from the original specification are either simplified or not included.

### 1. Database Migrations (Alembic)

- The assignment recommends using a migration tool like **Alembic** for schema
  versioning and evolution.
- In this implementation, the MySQL schema is created directly using
  SQLAlchemy’s `Base.metadata.create_all()`.
- There are **no versioned Alembic migration scripts**, so database changes
  would currently need to be applied manually or by recreating the schema.

### 2. Password Strength Validation

- The spec asks for server-side validation of both **email format** and
  **password strength**.
- Email format is validated via Pydantic schemas, and passwords are securely
  hashed before storage.
- However, password-strength checks are **minimal** (e.g., basic length checks)
  and do not enforce advanced rules such as:
  - required mix of uppercase/lowercase/digits/special characters
  - checking against common / compromised passwords
  - progressive strength scoring

---

These limitations do **not impact the core Task #1 flow**:

- secure registration with hashed password
- JWT-based authentication
- protected access to `/profile/me` for reading and updating profile data

---
## Summary
✔ Secure
✔ Functional
✔ Mobile + Web compatible
✔ Meets assignment expectations

Backend successfully supports the full authentication and profile flow for the Profile Management System frontend.

---
