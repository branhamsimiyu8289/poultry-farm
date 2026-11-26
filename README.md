# Kiambu Poultry Farm

**Live Demo:** [https://egg-production-tracker-v8w1.onrender.com/](https://egg-production-tracker-v8w1.onrender.com/)

A FastAPI application for recording egg production by shed, tracking totals,
calculating 30-egg trays, and preparing weekly summaries to share on WhatsApp.
Production records are stored in a local SQLite database.

## Features

- Responsive dashboard for logging and reviewing daily production
- Date filtering, running totals, and per-shed summaries
- Weekly reconciliation with tray counts and a WhatsApp share link
- REST API with input validation and interactive documentation

## Setup

Requires Python 3.10 or later. From this directory, create a virtual
environment and install dependencies:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Start the application:

```powershell
python -m uvicorn main:app --reload
```

Open the dashboard at <http://127.0.0.1:8000> or API docs at
<http://127.0.0.1:8000/docs>.

## API

| Method | Endpoint | Purpose |
|---|---|---|
| `POST` | `/api/eggs` | Add a record (`shed`, `date`, `count`) |
| `GET` | `/api/eggs` | List records and totals; optional `start` and `end` filters |
| `GET` | `/api/eggs/weekly-summary` | Summarize a 7-day period |
| `DELETE` | `/api/eggs/{record_id}` | Delete one record |
| `POST` | `/api/eggs/seed-sample` | Add sample records |
| `DELETE` | `/api/eggs` | **Delete all records** |

Example:

```powershell
curl.exe -X POST http://127.0.0.1:8000/api/eggs `
  -H "Content-Type: application/json" `
  -d '{"shed":"Shed 1","date":"2026-11-09","count":412}'
```

## Tests

```powershell
python -m unittest -v test_api
```

**Author:** [Branham Simiyu](https://github.com/branhamsimiyu8289)
