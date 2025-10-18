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

## Requirements

- Python 3.10+ recommended
- Virtual environment recommended

## Install dependencies (Windows PowerShell)

```powershell
python -m venv venv
.\venv\Scripts\Activate
pip install -r requirements.txt
```

## Initialize the database

The project includes a Flask CLI command to initialize the database. This will create the `instance/flaskr.sqlite` database using `flaskr/schema.sql`.

If your app package is `flaskr` (recommended):

```powershell
flask --app flaskr init-db
```


Note: `instance/flaskr.sqlite` is environment-specific and should NOT be committed. `.gitignore` excludes `instance/`.

## Run the development server

Using the `flaskr` package:

```powershell
flask --app flaskr run --debug
```


Open http://127.0.0.1:5000 in your browser.



## Notes

- Keep secrets out of the repo (do not commit `instance/config.py` with real `SECRET_KEY` or the `instance/` DB).
- If `instance/flaskr.sqlite` was previously committed, untrack it with:

```powershell
git rm --cached instance/flaskr.sqlite
git commit -m "Untrack local SQLite DB"
```


---

Project created by: Samuel Amoateng
