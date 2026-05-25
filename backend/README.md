# CV_Analayser — Backend

> A concise backend service for parsing, scoring and managing CVs (resumes).

## Project Overview

CV_Analayser is the backend component of a CV/resume analysis system. It exposes routes for user authentication, application submission, job posting, and automated CV scoring using prepared machine learning models and data processing pipelines.

## Key Features

- CV parsing and scoring pipeline
- User signup / login and token-based authentication
- Job and application management endpoints
- Utilities for preparing training data and building models

## Repository Structure

- `main.py` — application entry point
- `requirments.txt` — Python dependencies
- `apply/` — endpoints and DB helpers for applications
- `general/` — shared utilities (encryption, token handling, prediction, DB helpers)
- `home/` — home route(s)
- `job/` — job-related routes and DB access
- `login/` — authentication routes and helpers
- `preparing_data/` — scripts to prepare data, create CSVs and train models
- `signup/` — signup routes and helpers

## Requirements

- Python 3.8+
- See [requirments.txt](requirments.txt) for full dependency list

## Quickstart (Development)

1. Create and activate a virtual environment:

```bash
python -m venv .venv

# On Windows
.venv\\Scripts\\activate

# On Unix / macOS
source .venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r requirments.txt
```

3. Run the application:

```bash
python main.py
```

The server should start and expose the configured HTTP routes.

## Configuration

- Environment variables: configure any DB connection strings, secret keys, or other runtime settings using environment variables. Typical variables:
  - `SECRET_KEY` — token/encryption secret
  - `DATABASE_URL` — database connection string (if used)

Check the code in `general/sql.py` and the `sql.py` files in other modules for DB usage.

## API Endpoints (overview)

The backend organizes endpoints by feature folder. Notable route files:

- `apply/route.py` — application submission endpoints
- `home/route.py` — root/home endpoints
- `job/route.py` — job posting and listing endpoints
- `login/route.py` — authentication endpoints
- `signup/route.py` — user registration endpoints

Open these files to see exact routes and request/response formats.

## Data Preparation & Model Training

Scripts for preparing training data and creating models are in `preparing_data/`:

- `create_csv.py` — export/prepare CSV datasets
- `calculate_score.py` — scoring helpers
- `create_model.py` — model creation/training flow

Use these scripts to rebuild or update prediction models. See `general/predict.py` for how models are loaded and used at runtime.

## Development Notes

- Follow existing patterns in `general/` for DB access and token handling.
- Keep secrets out of source control; use environment variables or a secrets manager.

## Testing

There are no automated tests included by default. To add tests, create a `tests/` folder and use `pytest`.

## Contributing

Contributions are welcome. Please open issues or pull requests and include clear descriptions of changes and rationale.

## License

Add a license to this repository (for example, MIT) by creating a `LICENSE` file.

## Contact

For questions about this backend, inspect the code or reach out to the project maintainer.
