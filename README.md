### INF601 - Advanced Programming in Python
### Samuel Amoateng

# Mini Project 3 — Flask Blog Application (Flaskr)

Simple Flask web app built for the Mini Project 3 assignment. The app includes user authentication (register/login), a SQLite database with related tables, multiple pages using Jinja2 templates, and Bootstrap styling (includes a modal).

## What this project is

This repository contains a small Flask application demonstrating:

- User registration and login with password hashing
- A SQLite database (schema in `flaskr/schema.sql`) with at least two tables linked by a foreign key
- Templates using a base layout (Bootstrap included)
- HTML forms with GET/POST handling
- A minimal set of tests (if present in `tests/`)

## Database schema (excerpt)
The database includes a `user` table and a `post` table linked by a foreign key. Example excerpt (full schema in `flaskr/schema.sql`):

```sql
CREATE TABLE user (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  username TEXT UNIQUE NOT NULL,
  password TEXT NOT NULL
);

CREATE TABLE post (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  author_id INTEGER NOT NULL,
  created TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  title TEXT NOT NULL,
  body TEXT NOT NULL,
  FOREIGN KEY (author_id) REFERENCES user (id)
);
```

## Pages / routes (5+ pages)
This project follows the tutorial structure and includes the following pages (templates):

- `/` — `index.html` (list posts)
- `/create` — `create.html` (create post form)
- `/<int:id>` — `post_detail.html` (view post details)
- `/auth/register` — `auth/register.html` (registration)
- `/auth/login` — `auth/login.html` (login)

## Bootstrap & modal
Bootstrap v4 is included in `flaskr/templates/base.html`. A Bootstrap modal is used in the navigation bar as an "Info" modal. See the modal markup in `base.html`.

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
