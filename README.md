### INF601 - Advanced Programming in Python
### Samuel Amoateng

# Mini Project 3 — Flask Web Application

Simple Flask web app built for the Mini Project 3 assignment. The app includes user authentication (register/login), a SQLite database with related tables, multiple pages using Jinja2 templates, and Bootstrap styling (includes a modal).

## What this project is

This repository contains a small Flask application demonstrating:

- User registration and login with password hashing
- A SQLite database (schema in `flaskr/schema.sql`) with at least two tables linked by a foreign key
- Templates using a base layout (Bootstrap included)
- HTML forms with GET/POST handling
- A minimal set of tests (if present in `tests/`)

## Database schema (excerpt)
The database includes a `user` table plus related tables demonstrating foreign keys. Example excerpt (full schema in `flaskr/schema.sql`):

```sql
CREATE TABLE user (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	username TEXT UNIQUE NOT NULL,
	password TEXT NOT NULL
);

CREATE TABLE project (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	title TEXT NOT NULL,
	description TEXT,
	created_by INTEGER NOT NULL,
	FOREIGN KEY (created_by) REFERENCES user (id)
);

CREATE TABLE task (
	id INTEGER PRIMARY KEY AUTOINCREMENT,
	project_id INTEGER NOT NULL,
	title TEXT NOT NULL,
	due_date TEXT,
	done INTEGER NOT NULL DEFAULT 0,
	created_by INTEGER NOT NULL,
	FOREIGN KEY (project_id) REFERENCES project (id),
	FOREIGN KEY (created_by) REFERENCES user (id)
);
```

## Pages / routes (5+ pages)
This project follows the tutorial structure and includes the following pages (templates):

- `/` — `index.html` (list projects)
- `/project/<id>` — `project_detail.html` (project tasks + quick add form/modal)
- `/project/create` — `create_project.html` (create project form)
- `/auth/register` — `auth/register.html` (registration)
- `/auth/login` — `auth/login.html` (login)
- Optional: `/profile` — `profile.html` (user profile)

## Bootstrap & modal
Bootstrap v4 is included in `flaskr/templates/base.html`. A Bootstrap modal is used on the project detail page as a "Quick Add Task" form (or as a delete confirmation). See the modal markup in `base.html` or `project_detail.html`.

## Install dependencies (Windows PowerShell)

```powershell
python -m venv venv
.\venv\Scripts\Activate
pip install -r requirements.txt
```

## Initialize the database

```powershell
flask --app flaskr init-db
```

## Run the development server

```powershell
flask --app flaskr run --debug
```

Open http://127.0.0.1:5000 in your browser.

## Assignment requirements checklist

- [ ] Header comments with name, class, and project at top of `main.py` (required)
- [x] `requirements.txt` present
- [x] `README.md` present with install/init/run instructions
- [x] Register/login system implemented
- [x] Bootstrap + modal used in templates
- [x] SQLite DB with ≥2 tables and a foreign key (see `flaskr/schema.sql`)
- [ ] 5+ pages/templates using a base layout
- [ ] At least one page with a GET and POST form handler
- [ ] Minimum 5 commits on `main` branch

## Verify commit count
To check commits on the main branch:

```powershell
git rev-list --count main
```


---

Project created by: Samuel Amoateng
