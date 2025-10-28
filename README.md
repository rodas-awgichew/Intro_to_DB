# Intro_to_DB

A teaching / demo repository that contains examples, exercises, and utilities for learning the fundamentals of relational databases and SQL. This repository provides schema examples, SQL scripts, sample data, notebooks, and helper scripts to practice schema design, CRUD operations, joins, indexing, transactions, and basic performance tuning.

## Project overview
Intro_to_DB is intended to be a small, easy-to-follow collection of resources for learners and instructors:
- Hands-on SQL scripts for creating schemas and loading sample data
- Example queries and exercises ordered by difficulty
- Small Python utilities for connecting to databases and running migrations
- Tests and validation scripts for exercises

## Features
- Schema creation scripts (DDL) and sample data (DML)
- Index and explain plan examples
- Interactive Jupyter notebooks for guided walkthroughs
- Utilities to reset and seed the local database

## Prerequisites
- Git
- Python 3.8+ (if using the Python utilities / notebooks)
- One of the supported database engines: SQLite (no server), PostgreSQL, or MySQL
- (optional) Docker — to run the database locally in a container

Install Python dependencies (if needed):
```bash
python -m venv .venv
source .venv/bin/activate        # macOS / Linux
.venv\Scripts\activate           # Windows (PowerShell)
pip install --upgrade pip
pip install -r requirements.txt  # if this file exists
```

## Quickstart
1. Clone the repository:
```bash
git clone https://github.com/rodas-awgichew/Intro_to_DB.git
cd Intro_to_DB
```

2. Pick a database engine:
- SQLite (quickest, file-based):
  - Many example SQL scripts will run directly in sqlite3:
    ```bash
    sqlite3 demo.db < sql/init_schema.sql
    sqlite3 demo.db < sql/seed_data.sql
    ```
- PostgreSQL:
  - Create database and run SQL scripts:
    ```bash
    psql -h localhost -U youruser -d yourdb -f sql/init_schema.sql
    psql -h localhost -U youruser -d yourdb -f sql/seed_data.sql
    ```
  - Or use a provided helper script (if present):
    ```bash
    python scripts/setup_db.py --engine postgres --db-name intro_db
    ```

3. Run notebooks:
```bash
# If notebooks exist
jupyter lab
# or
jupyter notebook
```
Open the notebooks under `notebooks/` to follow interactive lessons.

4. Run example queries from Python (example using environment variable):
```bash
export DATABASE_URL="postgresql://user:password@localhost:5432/intro_db"
python scripts/run_example_queries.py
```


## Running tests
If there are tests in `tests/`, run them with pytest:
```bash
pip install -r requirements.txt  # if tests require packages
pytest -q
```
If tests require a running database, ensure the test database is available and environment variables point to it (e.g., TEST_DATABASE_URL).

## Contributing
Contributions are welcome. A suggested workflow:
1. Fork the repository and create a branch for your change:
   ```bash
   git checkout -b feature/your-feature
   ```
2. Make changes and add tests or documentation as appropriate.
3. Run tests locally.
4. Open a pull request with a clear description of the change.

Guidelines:
- Keep exercises small and focused.
- Add example answers in a separate folder (e.g., `solutions/`) and clearly mark them.
- If adding data, prefer small, synthetic datasets that are easy to load.

## License
This repository does not include a license file by default. Consider adding a LICENSE (for example, MIT) to clarify usage and contributions.

Suggested: add a LICENSE file with MIT license if you want permissive reuse.

## Authors and contact
Maintainer: rodas-awgichew
For issues and questions, open an issue in this repository: https://github.com/rodas-awgichew/Intro_to_DB/issues

---

If you want, I can:
- Inspect the repository and update this README with exact filenames and commands (I can scan the repo for `sql/`, `notebooks/`, and `scripts/`).
- Add a sample LICENSE file and a CONTRIBUTING.md.
- Generate example data-loading scripts tailored to a specific DB engine.
