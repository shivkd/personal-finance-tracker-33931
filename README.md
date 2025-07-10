# Project Repository

This is the initial README file for the project.

---

## Personal Finance Tracker - Database Setup

### 1. **Production Database (Supabase PostgreSQL)**
- The production database is managed by Supabase.
- Connection details (example):
  ```
  POSTGRES_URL="postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require"
  POSTGRES_USER="postgres"
  POSTGRES_PASSWORD="[YOUR_SECRET_PASSWORD]"
  POSTGRES_DB="postgres"
  POSTGRES_PORT="5432"
  ```
- **How to connect:**
  - From psql:
    ```
    psql postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require
    ```
  - From backend, mobile apps, or tools, substitute the values as per above.

- Get your `[YOUR_SECRET_PASSWORD]` from the Supabase dashboard under Project > Database > Connection info.

### 2. **Local Development Database (optional)**
- For offline development and testing, you can use a local PostgreSQL setup.
- Default local config:
  ```
  POSTGRES_URL="postgresql://appuser:dbuser123@localhost:5000/myapp"
  POSTGRES_USER="appuser"
  POSTGRES_PASSWORD="dbuser123"
  POSTGRES_DB="myapp"
  POSTGRES_PORT="5000"
  ```
- See `finance_db/startup.sh` for automated local setup.

### 3. **Switching Environments**
- Update `finance_db/db_visualizer/postgres.env`: uncomment the section you want to use and `source` the file.
- Update application `.env` files as appropriate.

### 4. **Connecting the Backend**
- In `finance_backend`, set environment variables or config to point to Supabase (for production) or local Postgres as above.
- FastAPI and most ORMs accept the STANDARD Postgres connection URI.

### 5. **Developer Onboarding**
- Clone the repository.
- Use Supabase as your primary backend (recommended).
  - Get credentials from the team lead/project manager/Supabase dashboard.
- For local testing, optionally run `finance_db/startup.sh` (see inside the script for details).
- Use the `db_connection.txt` file for ready-to-use connection commands.
- All developer tools (scripts, db_visualizer, etc.) read from `db_visualizer/postgres.env`.