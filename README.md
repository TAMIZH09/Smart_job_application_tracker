# Smart Job Application Tracker API

A resume portfolio project demonstrating Python, FastAPI, REST APIs, SQL, SQLAlchemy ORM, MySQL, validation, password hashing, JWT authentication, filtering, pagination, and dashboard aggregation.

## 1. Requirements
- Python 3.10+
- MySQL Server
- pip

## 2. Create the database
Open MySQL Workbench or phpMyAdmin and run:

```sql
CREATE DATABASE job_tracker CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

## 3. Configure environment
Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
```

Edit `.env` and replace `YOUR_PASSWORD` with your MySQL password. Change `SECRET_KEY` to a long random secret.

If PowerShell blocks activation, you can run without activation:
```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m uvicorn app.main:app --reload
```

## 4. Run the API
```powershell
uvicorn app.main:app --reload
```

Open:
- Swagger UI: http://127.0.0.1:8000/docs
- Health check: http://127.0.0.1:8000/api/health

The two SQL tables are created automatically on first startup.

## 5. Test in Swagger
1. `POST /api/auth/register` with `full_name`, `email`, `password`.
2. Click **Authorize**. Use your email as `username` and your password as `password`. The token endpoint follows OAuth2 form conventions.
3. Create applications with `POST /api/jobs`.
4. Try filtering: `GET /api/jobs?status=Interview` or `GET /api/jobs?search=Python`.
5. View aggregate statistics using `GET /api/dashboard`.

## API endpoints
| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/api/health` | Health check |
| POST | `/api/auth/register` | Register |
| POST | `/api/auth/token` | Login and get JWT |
| GET | `/api/auth/me` | Current user |
| POST | `/api/jobs` | Create application |
| GET | `/api/jobs` | List/search/filter/paginate |
| GET | `/api/jobs/{job_id}` | Get one application |
| PATCH | `/api/jobs/{job_id}` | Update application |
| DELETE | `/api/jobs/{job_id}` | Delete application |
| GET | `/api/dashboard` | Status statistics |

## Resume description
**Smart Job Application Tracker API | Python, FastAPI, MySQL, SQLAlchemy, JWT**
- Built a RESTful backend to manage job applications, interview schedules, and application statuses using FastAPI and MySQL.
- Implemented JWT authentication, password hashing, request validation, and user-specific data access.
- Developed searchable, filterable, paginated endpoints and SQL aggregate queries for dashboard analytics.

## Before publishing
- Never commit `.env` or real API secrets.
- Replace the development secret key.
- Add automated tests, migrations (Alembic), logging, and deployment configuration as further enhancements.
