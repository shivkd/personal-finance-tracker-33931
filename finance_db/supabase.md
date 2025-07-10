# Supabase Configuration for finance_db

---
**Quick Reference: Dual Environment Setup (Supabase Production & Local Dev)**

| Step   | Production (Supabase)                                                               | Local Development (offline, optional)                |
|--------|------------------------------------------------------------------------------------|------------------------------------------------------|
| 1.     | Copy the "Supabase" export block from `db_visualizer/postgres.env`                | Run `bash finance_db/startup.sh` once                |
| 2.     | Replace `[YOUR_SECRET_PASSWORD]` with the real value from Supabase dashboard      | Check or copy the env vars from generated file        |
| 3.     | Set these as `.env` for backend/tools or `source db_visualizer/postgres.env`      | `source db_visualizer/postgres.env` or use .env      |
| 4.     | Start backend/services normally                                                   | Start backend/services normally                       |
| Switch | Edit/comment/uncomment blocks in `db_visualizer/postgres.env`; always avoid real creds in committed files |

For full onboarding and switching details, see `README.md`, or refer to documentation below.

---

## Supabase Project Details
- **Supabase URL:** https://xihtrwadyqfimillpxff.supabase.co
- **Supabase Key:** (keep private; obtain from project secrets or authorized team personnel)
- **Postgres Connection String (Supabase/Production):**
    ```
    postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require
    ```
  `[YOUR_SECRET_PASSWORD]` is visible in the Supabase dashboard: Project > Database > Connection info.

---

## Environment Variable Usage (Backend/Tools)
- Always set Supabase credentials in environment variables for the backend (`POSTGRES_URL`, etc.) and in tooling configs.
- Example `.env` for FastAPI or Node backend:
    ```
    POSTGRES_URL="postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require"
    POSTGRES_USER="postgres"
    POSTGRES_PASSWORD="[YOUR_SECRET_PASSWORD]"
    POSTGRES_DB="postgres"
    POSTGRES_PORT="5432"
    ```
- For local development, substitute with local connection string as shown in onboarding/README.

---

## Usage for Production (Supabase)
- All backend/api tooling should, by default, use the Supabase Postgres connection string.
- Ensure `.env`/exported variables are populated accordingly.
- Templates for environment variables are in `finance_db/db_visualizer/postgres.env`.
- `db_connection.txt` has a ready-to-paste connection command for psql/CLI use.

## Usage for Local Development (Offline Option)
- Use the helper script `finance_db/startup.sh` to spin up/dev a local Postgres instance.
- This script generates a local `.env` (useful for backend) and updates `db_connection.txt`.
- Switch modes by editing/commenting the proper env vars in `finance_db/db_visualizer/postgres.env` or your backend `.env`.

## Backend Development Workflow
- For typical FastAPI/Python (or Node.js, etc.) simply set `POSTGRES_URL` in `.env`.
- The backend code should read the connection string from `.env` (dev loads local, prod loads Supabase).
- To switch: update `.env`, or `source finance_db/db_visualizer/postgres.env` before starting backend/tooling.

### Security Note
- **Never commit real database passwords or Supabase service keys to version control.**
- Use `[YOUR_SECRET_PASSWORD]` (or similar) in committed files and share secrets via secure means.

---

## Quick Start (Developer Onboarding)
1. Read onboarding steps in `README.md`.
2. **Production:** Use Supabase; set real credentials from dashboard.
3. **Dev (offline):** Optionally run `bash finance_db/startup.sh` and use the generated local settings.
4. Before using backend/tools, ensure env vars are correct (`source db_visualizer/postgres.env` or update `.env`).
5. Use `db_connection.txt` for copy-paste CLI access.

---

Task completed: Dual-mode PostgreSQL instructions (Supabase + local) clarified across configuration, onboarding, and scripts.

Task completed: Supabase PostgreSQL integration documented, onboarding clarified, and development option preserved.
