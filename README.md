# Profile Management System — Backend

A secure backend built using **FastAPI + SQLAlchemy + JWT Authentication** that powers the Profile Management System frontend.

This backend provides authentication, profile management, authorization, and database persistence.

> Part of a full-stack assignment demonstrating authentication, structured APIs, database CRUD operations, and clean architecture.

---------------------------------------------------------------------

## 📌 Table of Contents

- Project Goals
- Tech Stack
- Architecture Decisions
- API Features
- Setup Instructions
- Environment Configuration
- Running the Server
- API Endpoints
- Database Details
- Frontend Link
- Time Spent
- Limitations

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
- **Password Hashing** implemented using bcrypt for security.
- **Token validation** applied on protected endpoints to prevent unauthorized access.
- **CORS Middleware** added to allow communication from mobile clients, local browser, or Expo app.

---------------------------------------------------------------------

## API Features

- [x] User Registration (POST `/auth/signup`)
- [x] User Login with JWT return (POST `/auth/login`)
- [x] Token-protected routes
- [x] Retrieve authenticated user profile (GET `/profile/me`)
- [x] Update name/bio (PUT `/profile/me`)
- [x] Validation + structured error messaging

---------------------------------------------------------------------

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/sejalsharma2002/profile-management-backend.git
cd profile-management-backend
2. Create Virtual Environment
bash
Copy code
python -m venv venv
Windows:
bash
Copy code
venv\Scripts\activate
Mac/Linux:
bash
Copy code
source venv/bin/activate
3. Install Dependencies
bash
Copy code
pip install -r requirements.txt
Environment Configuration
Optional .env file values (defaults exist if file is missing):

bash
Copy code
SECRET_KEY="your-secret"
ALGORITHM="HS256"
ACCESS_TOKEN_EXPIRE_MINUTES=180
Running the Server
For Desktop / Browser Testing
bash
Copy code
uvicorn main:app --reload
For Mobile App Support (Expo / Physical Device)
bash
Copy code
uvicorn main:app --reload --host 0.0.0.0 --port 8000
Ensure your machine firewall allows access if using mobile.

API Endpoints
Method	Endpoint	Auth	Purpose
POST	/auth/signup	❌	Register new user
POST	/auth/login	❌	Authenticate user + return JWT token
GET	/profile/me	✔️	Get authenticated user's profile
PUT	/profile/me	✔️	Update authenticated user's name + bio

Swagger documentation is available at:

bash
Copy code
http://127.0.0.1:8000/docs
Database Details
Engine: SQLite (generated automatically as database.db)

Table(s):

users (id, name, email, password hash, bio)

Auto-increment ID enabled (respects deleted rows)

No manual setup required — database initializes on first run.

Frontend Link
The frontend application that consumes this API is available here:

bash
Copy code
https://github.com/sejalsharma2002/profile-management-frontend
Time Spent (Estimated)
Task	Duration
Initial setup + dependencies	1 hr
Authentication + JWT implementation	3 hrs
Profile CRUD development	2 hrs
Testing backend with mobile + web	3 hrs
Debugging + refinement	2 hrs
Final documentation	1 hr

Total Estimated Time: 12 hours

Limitations
Based on project scope and assignment requirements:

NativeWind/Tailwind not required in backend, so no styling engine involved.

No user roles or admin-level permissions (single user type).

No public deployment URL — backend runs locally only.

No password reset / email verification workflow.

Only JSON-based profile fields (no avatar upload support yet).

These items do not affect assignment correctness and are available for version upgrades.

Summary
✔ Secure
✔ Functional
✔ Mobile + Web compatible
✔ Meets assignment expectations

Backend successfully supports the full authentication and profile flow for the Profile Management System frontend.
