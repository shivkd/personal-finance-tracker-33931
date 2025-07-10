# Supabase Configuration for finance_db

## Supabase Project Details
- **Supabase URL:** https://xihtrwadyqfimillpxff.supabase.co
- **Supabase Key:** (see project secrets or environment for secure access)
- **Postgres Connection String (Production):**
    ```
    postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require
    ```
  Where `[YOUR_SECRET_PASSWORD]` is found in the Supabase dashboard.

---

## Usage for Production
- All backend, visualization tools, and user services should use the Supabase connection as primary database (see example connection string above).
- Environment variable templates updated in `db_visualizer/postgres.env`.
- `db_connection.txt` also provides a ready-to-use command.

## Usage for Local Development
- Local Postgres setup is available for development only.
- Script: `finance_db/startup.sh` automates the creation of a compatible local developer environment.
- Switch environment variables in `db_visualizer/postgres.env` as needed.

## Connecting from Backend/Tools
1. For production: use Supabase credentials.
2. For local dev: use local credentials (see above and script).
3. FastAPI/ORM: use the same `POSTGRES_URL` string as your `DATABASE_URL` or equivalent variable.

### Security Note
- Never commit the actual database password to the repository.
- Use placeholders (`[YOUR_SECRET_PASSWORD]`) and provide secure distribution of secrets.

---

## Quick Start (Onboarding Checklist)
1. Review updated docs in `README.md`.
2. For production, fetch credentials from Supabase dashboard.
3. (Dev Only) For local setup, run the script: `bash finance_db/startup.sh`.
4. Source the environment: `source finance_db/db_visualizer/postgres.env`.
5. Connect any backend or tooling to the DB using the environment configuration.

---

Task completed: Supabase PostgreSQL integration documented, onboarding clarified, and development option preserved.
