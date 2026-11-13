# Expense Tracker

React + Vite frontend, Express + SQLite backend.

## Requirements
- Node.js 18.18+ (LTS 20 or 22 recommended) and npm
- VS Code

## Run it
Open the `expense-tracker` folder in VS Code, open a terminal (Ctrl+`) and run:

```bash
npm install
npm run install-all
npm run dev
```

- Frontend: http://localhost:5173 (opens automatically)
- Backend API: http://localhost:5000

Optional, development only: `npm run seed` adds 7 sample expenses. The database starts empty otherwise.

## Data
SQLite file: `backend/database/expenses.db` (created on first start). Delete it to start fresh.

## API
Expenses: `GET /api/expenses`, `GET /api/expenses/summary`, `GET|PUT|DELETE /api/expenses/:id`, `POST /api/expenses`
Categories: `GET|POST /api/categories`, `PUT|DELETE /api/categories/:id` (`DELETE ...?reassignTo=Name` moves expenses first)

## Troubleshooting
- `better-sqlite3` install errors on Windows: use a Node LTS version (prebuilt binaries), then re-run `npm run install-all`.
- Port in use: stop other apps on 5000/5173.

## Deploy (single server)
Express serves the built React app, so you deploy one service.

- Build command: `npm run build`
- Start command: `npm start`
- Environment: `PORT` (set by most hosts) and `DB_PATH` pointing at a persistent disk, e.g. `/data/expenses.db`
- Needs Node 18.18+ and a persistent disk/volume, or data is lost on every redeploy.
- The app has no login: anyone with the URL can view and edit data.
