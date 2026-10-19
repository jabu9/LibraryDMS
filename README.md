# LibraryDMS

A library database management system built with **Flask** and **MySQL**. Members can register, browse and search the catalog by genre, check out and return books, and manage their account. Admins get a separate login for editing books and members.

Built as the Computer Science capstone project for CMSC 495 (Group 3).

## Features

- Member registration and login with **bcrypt**-hashed passwords
- Home page carousel of books, plus browsing by genre
- Book checkout and return
- Account page with profile editing and account deletion
- Admin dashboard for editing book and member records
- Seed data (books, copies, checkouts) loaded from CSV

## Tech stack

| Layer    | Tools                         |
|----------|-------------------------------|
| Backend  | Python, Flask                 |
| Database | MySQL (`mysql-connector-python`) |
| Frontend | Jinja2 templates, HTML, CSS   |
| Data     | pandas (CSV seeding)          |

## Getting started

**Prerequisites:** Python 3.9+ and a running MySQL server.

```bash
git clone https://github.com/jabu9/LibraryDMS.git
cd LibraryDMS
python -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Set your database credentials as environment variables (see `.env.example`):

```bash
export LIBRARY_DB_PASSWORD=your_mysql_password
export FLASK_SECRET_KEY=some-long-random-string
```

Create the database and load the seed data, then add an admin account:

```bash
python create_db.py
python admin_registration.py
```

Run the app and open http://127.0.0.1:5000:

```bash
python library_app.py
```

## Project structure

```
LibraryDMS/
├── library_app.py          # Flask app: routes, auth, checkout logic
├── create_db.py            # Creates tables and loads CSV seed data
├── admin_registration.py   # CLI script to add an admin user
├── bookdata.csv            # Seed data: books
├── bookcopydata2.csv       # Seed data: book copies
├── checkout2.csv           # Seed data: checkouts
├── resources/              # Stored SQL queries
├── static/                 # CSS and book cover images
└── templates/              # Jinja2 HTML templates
```

## Configuration

| Variable              | Default     | Description                 |
|-----------------------|-------------|-----------------------------|
| `LIBRARY_DB_HOST`     | `localhost` | MySQL host                  |
| `LIBRARY_DB_USER`     | `root`      | MySQL user                  |
| `LIBRARY_DB_PASSWORD` | *(empty)*   | MySQL password              |
| `LIBRARY_DB_NAME`     | `library`   | Database name               |
| `FLASK_SECRET_KEY`    | random      | Flask session signing key   |

> If `FLASK_SECRET_KEY` isn't set, a random key is generated on startup, so sessions reset every restart.

## License

[MIT](LICENSE) © 2023 Jordan Abuhantash and the CMSC 495 Group 3 contributors
