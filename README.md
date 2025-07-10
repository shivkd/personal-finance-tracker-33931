# Project Repository

**Personal Finance Tracker**

---

## Database Setup and Environment Management

### 1. **Production Database: Supabase PostgreSQL (Default/Recommended)**
- The primary/production database is fully managed on Supabase.
- **Supabase PostgreSQL connection string (TEMPLATE):**
  ```
  POSTGRES_URL="postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require"
  POSTGRES_USER="postgres"
  POSTGRES_PASSWORD="[YOUR_SECRET_PASSWORD]"
  POSTGRES_DB="postgres"
  POSTGRES_PORT="5432"
  ```
- **How to connect:**
    - Command line:  
      `psql postgresql://postgres:[YOUR_SECRET_PASSWORD]@db.xihtrwadyqfimillpxff.supabase.co:5432/postgres?sslmode=require`
    - Backend or tools:  
      Copy these values (or the full connection string) into your app’s `.env` as shown above.
    - Find `[YOUR_SECRET_PASSWORD]` in your Supabase dashboard (Project > Database > Connection info).

### 2. **Local Development Database (Dev Only, Optional)**
- If working offline or for hot-reloading/test dev, run a local PostgreSQL using the included helper:
  ```
  POSTGRES_URL="postgresql://appuser:dbuser123@localhost:5000/myapp"
  POSTGRES_USER="appuser"
  POSTGRES_PASSWORD="dbuser123"
  POSTGRES_DB="myapp"
  POSTGRES_PORT="5000"
  ```
- Run `bash finance_db/startup.sh` to set up (creates user/db and saves configs for you).

### 3. **Switching Environments (Dev/Prod)**
- **Primary method:**  
  - Edit `finance_db/db_visualizer/postgres.env`: comment/uncomment the section (Supabase for prod, local for dev).
  - Then: `source finance_db/db_visualizer/postgres.env` *or* set your `.env` in backend to match.
- **Backend/Any container:**  
  - Copy the desired block into your container’s `.env` file.
  - Make sure only real secret passwords are used locally. Never commit real passwords.

### 4. **Connecting the Backend (FastAPI, etc.)**
- The backend expects standard PostgreSQL connection URI/envs (works with SQLAlchemy, asyncpg, psycopg2, etc.):
  - Set `POSTGRES_URL` as shown above (in .env or your environment).
  - Everything else will autodetect (db name/user/password/port) from env variables.
- For local/development:  
  Just run `finance_db/startup.sh`, then `source finance_db/db_visualizer/postgres.env` **before** starting the backend.

### 5. **Developer Onboarding (Checklist)**
- Clone this repository.
- By default, connect to Supabase (preferred):
    - Get your credentials from your project lead/Supabase dashboard.
    - Update `.env` or `finance_db/db_visualizer/postgres.env` (export/secrets) accordingly.
- (Optional Dev) For local Postgres:
    - Run `bash finance_db/startup.sh` to autocreate DB, user, and settings.
    - Use resulting `.env` and `db_connection.txt` for psql/ORM access.
- Use `db_connection.txt` for quick psql connection.
- Scripts/tools (`db_visualizer`, backend, etc.) read from env files (see above).
- **Security Reminder:** Never commit secrets/real DB passwords to the repo! Always use `[YOUR_SECRET_PASSWORD]` for templates.

---

For further details, see `finance_db/supabase.md` (Supabase config), scripts in `finance_db`, and code comments.