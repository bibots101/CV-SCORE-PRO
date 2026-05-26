**CV Analyser (CV Score Pro)**

CV Analyser is a full-stack application that scores and analyzes CVs/resumes to help match candidates with job requirements. This repository contains two primary submodules: the backend (FastAPI) and the frontend (Vite + React / TypeScript). The root repository ties the two submodules together and provides top-level guidance for development and deployment.

**Repository**
- **Backend**: API, ML model loading, data preparation, authentication and job application logic — located in the `backend/` folder. See [backend/README.md](backend/README.md).
- **Frontend**: Vite + React/TypeScript web app — located in the `frontend/` folder. See [frontend/README.md](frontend/README.md).

**Submodule repositories**
This repository is intended to include the backend and frontend as git submodules. Add them using your own remote URLs. Example:

```bash
git submodule add <BACKEND_REPO_URL> backend
git submodule add <FRONTEND_REPO_URL> frontend
git commit -m "Add backend and frontend submodules"
```

To clone this repository including submodules:

```bash
git clone --recurse-submodules <ROOT_REPO_URL>
# or if already cloned
git submodule update --init --recursive
```

Replace `<BACKEND_REPO_URL>`, `<FRONTEND_REPO_URL>`, and `<ROOT_REPO_URL>` with your actual repository URLs.

Getting started (development)
-----------------------------

Backend (basic)

1. Create and activate a Python virtual environment:

```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
```

2. Install dependencies (from repository root or inside `backend/`):

```bash
pip install -r backend/requirments.txt
```

3. Run the API (example using Uvicorn):

```bash
cd backend
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

4. Open the API docs at `http://localhost:8000/docs`.

Frontend (basic)

1. From the `frontend/` directory install node dependencies:

```bash
cd frontend
npm install
# or: pnpm install | yarn
```

2. Run the dev server:

```bash
npm run dev
# or: pnpm dev | yarn dev
```

3. Open the application in the browser (Vite will show the local URL).

Environment and configuration
-----------------------------
- Backend: configure database credentials and secret keys via environment variables (check `backend/const.py` or similar files). Use a `.env` or your deployment secrets manager.
- Frontend: configure API base URL in the environment (for Vite use `VITE_API_URL` in `.env` files).

Project structure (top-level)

- `backend/` — FastAPI app, ML model code, data preparation and SQL helpers. See [backend/README.md](backend/README.md).
- `frontend/` — Vite + React TypeScript app. See [frontend/README.md](frontend/README.md).
- `preparing_data/` — scripts used to process data, train and export models.
- `cvscorepro.sql` — SQL schema or example dump used by the project.

Testing
-------
- Backend: run Python tests from `backend/` (e.g., `pytest backend/`), and use test databases where possible.
- Frontend: run `npm test` or the configured test runner in `frontend/`.

Deployment notes
----------------
- Containerize the backend and frontend separately (Docker) and use a reverse proxy (NGINX) or cloud provider routing to serve the frontend and proxy API calls to the backend.
- Use CI to run tests and build artifacts. For submodules, ensure CI checks initialize submodules (e.g., `git submodule update --init --recursive`).

Contributing
------------
- Please open issues or pull requests against the appropriate submodule repo for changes specific to backend or frontend.
- For cross-cutting changes (e.g., API contract changes), open an issue in this root repository and link the submodule PRs.

Licensing
---------
This project is provided under the MIT License. See the [LICENSE](LICENSE) file.

Contact
-------
For questions, feature requests, or help getting started, open an issue or contact the maintainers via the repository contact info.

Acknowledgements
----------------
Built with FastAPI, Vite, React, and common ML/data-processing libraries.

---

If you want, I can also:
- add the two submodule remote URLs into the repo and initialize them
- create or update `backend/README.md` and `frontend/README.md` with tailored instructions
Tell me which option you prefer and provide the remote URLs if you'd like me to add them.
