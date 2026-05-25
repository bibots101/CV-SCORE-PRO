# CV Analyser Frontend

Frontend application for the CV Analyser platform, built with React, TypeScript, and Vite.

This project provides:

- authentication (login and signup)
- protected routing using token-based access
- job listing pages for user and admin views
- CV analysis request flow via backend API

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Available Scripts](#available-scripts)
- [Application Routes](#application-routes)
- [API Integration](#api-integration)
- [Authentication Flow](#authentication-flow)
- [Build and Deployment](#build-and-deployment)
- [Known Limitations](#known-limitations)

## Overview

The frontend is a single-page application that communicates with a backend running on:

- `http://127.0.0.1:8000`

Main responsibilities of this frontend:

- handle user authentication UI and token persistence
- enforce route access control for authenticated and unauthenticated users
- render job-related pages for end users and administrators
- submit CV analysis payloads to the backend prediction endpoint

## Tech Stack

- React 18
- TypeScript
- Vite 5
- React Router DOM 6
- Tailwind CSS
- Bootstrap 5
- Headless UI and Heroicons

## Project Structure

```text
frontend/
|-- public/
|-- src/
|   |-- App.tsx                # Router and top-level route configuration
|   |-- main.tsx               # App bootstrap entry
|   |-- pageRoute.tsx          # Route guards (private/public logic)
|   |-- function.tsx           # Shared backend API calls
|   |-- components/
|   |   |-- login.tsx          # Login screen
|   |   |-- signup.tsx         # Registration screen
|   |   |-- home.tsx           # Authenticated user jobs page
|   |   |-- admin.tsx          # Admin dashboard page
|   |   |-- adminJobs.tsx      # Admin-specific job cards
|   |   |-- addJob.tsx         # Add job UI
|   |   |-- job.tsx            # User-facing job card
|   |   |-- attachments.tsx    # CV attachment and upload-related UI
|   |   |-- nav.tsx            # Shared navigation
|   |   |-- error.tsx          # Fallback error/not found page
|-- index.html
|-- package.json
|-- vite.config.ts
|-- tailwind.config.js
```

## Getting Started

### 1. Prerequisites

- Node.js 18+
- npm 9+
- Backend API running at `http://127.0.0.1:8000`

### 2. Install Dependencies

```bash
npm install
```

### 3. Start Development Server

```bash
npm run dev
```

The app will start with Vite's local dev server (usually `http://localhost:5173`).

## Available Scripts

- `npm run dev`: start development server with hot reload
- `npm run build`: type-check and create production build
- `npm run preview`: preview the built app locally
- `npm run lint`: run ESLint across TypeScript/TSX files

## Application Routes

Current route behavior:

- `/` -> login page
- `/login` -> login page
- `/signup` -> signup page
- `/home` -> protected user page (requires token)
- `/admin` -> protected admin page (requires token)
- `*` -> fallback error page

Access control summary:

- unauthenticated users are redirected to `/login` when visiting protected routes
- authenticated users are redirected to `/home` when visiting auth pages

## API Integration

API helpers are centralized in `src/function.tsx`.

Configured backend base URL:

- `http://127.0.0.1:8000`

Endpoints used by the frontend:

- `POST /login` -> user login
- `POST /signup` -> create user account
- `POST /home` -> fetch authenticated user information
- `GET /get_jobs` -> fetch available jobs
- `POST /predict` -> submit CV analysis request

## Authentication Flow

1. User submits credentials on login.
2. On success, backend returns a token.
3. Token is stored in `localStorage` under key `token`.
4. Route guards in `src/pageRoute.tsx` enforce page access based on token presence.
5. Authorized API requests include `Authorization: Bearer <token>`.

## Build and Deployment

Create a production build:

```bash
npm run build
```

Preview production build locally:

```bash
npm run preview
```

Deploy the generated `dist/` directory to your static hosting provider.

## Known Limitations

- Backend URL is currently hardcoded in `src/function.tsx` and component fetch calls.
- Environment-based API configuration is not yet centralized.
- Automated test suites are not configured in the current frontend setup.

