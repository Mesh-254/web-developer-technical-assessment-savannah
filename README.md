# Project Name: Web Developer Technical Assessment

## Overview

This project is an assessment for evaluating frontend skills with a **React** frontend and a **Django** backend. The application consists of a landing page, user authentication, and multiple pages to display users, albums, and photos. The backend serves as an API with endpoints for users, albums, and photos.

The goal is to ensure clean, maintainable, and well-documented code, with separation between the development and production environments. The application will be deployed on a free-tier platform, and it includes unit tests, linting, and a pipeline to run tests and deploy automatically.

## Table of Contents

1. [Prerequisites](#prerequisites)
2. [Branching Strategy](#branching-strategy)
3. [Project Setup](#project-setup)
    - [Frontend](#frontend)
    - [Backend](#backend)
4. [Environment Variables](#environment-variables)
5. [Testing](#testing)
6. [CI/CD Pipeline](#cicd-pipeline)
7. [Deployment](#deployment)
8. [Linting and Formatting](#linting-and-formatting)
9. [Contributing](#contributing)

---

## Prerequisites

Before starting, make sure you have the following installed:

- **Node.js** (for the React frontend)
- **npm** (Node package manager)
- **Python** (for the Django backend)
- **pip** (Python package manager)
- **PostgreSQL** (or your preferred database for Django)
- **Git** (for version control)
- **Docker** (optional, for containerized deployment)

## Branching Strategy

This repository uses a Git branching model to separate development and production environments.

### Main Branches:
- **`main`**: Represents the production-ready code.
- **`development`**: Active development branch, used for testing new features and bug fixes.

### Feature and Bugfix Branches:
- **`feature/<feature-name>`**: Branches for new features, created from `development`.
- **`bugfix/<bug-name>`**: Branches for fixing bugs, created from `development`.

### Workflow:
1. Create a feature branch from `development` for new features.
2. Once the feature is complete, submit a pull request (PR) to merge into `development`.
3. After testing in `development`, merge into `main`.
4. Use semantic versioning for releases (e.g., `v1.0.0`).

---

## Project Setup

### Frontend (React)

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/assessment-repo.git
   cd assessment-repo/frontend
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Run the development server:

   ```bash
   npm start
   ```

   The app will run at [http://localhost:3000](http://localhost:3000).

4. Build for production:

   ```bash
   npm run build
   ```

   This will generate the production build in the `build/` directory.

### Backend (Django)

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/assessment-repo.git
   cd assessment-repo/backend
   ```

2. Set up a virtual environment (optional but recommended):

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install backend dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Set up your database (ensure PostgreSQL or your preferred database is running):

   ```bash
   python manage.py migrate
   ```

5. Run the Django development server:

   ```bash
   python manage.py runserver
   ```

   The backend will run at [http://localhost:8000](http://localhost:8000).

---

## Environment Variables

### Frontend (React)

- Create `.env.development` for development environment variables.
- Create `.env.production` for production environment variables.

Example `.env.development`:
```env
REACT_APP_API_URL=http://localhost:8000/api
NODE_ENV=development
DEBUG=true
```

Example `.env.production`:
```env
REACT_APP_API_URL=https://api.production-url.com/api
NODE_ENV=production
DEBUG=false
```

### Backend (Django)

Create a `.env` file or use environment variables to manage different settings for `development` and `production` environments.

1. **Create two settings files** in `backend/settings/`:
    - `development.py` for development.
    - `production.py` for production.

2. **In `settings.py`**:
   ```python
   import os
   if os.getenv('DJANGO_ENV') == 'production':
       from .production import *
   else:
       from .development import *
   ```

---

## Testing

Unit tests ensure the correctness of the software in both development and production environments.

1. **Frontend Testing**:
   - Install **Jest** for testing React components.
   - Run tests with:
     ```bash
     npm test
     ```

2. **Backend Testing**:
   - Install **pytest** for testing Django.
   - Run tests with:
     ```bash
     python manage.py test
     ```

---

## CI/CD Pipeline

The CI/CD pipeline runs automated tests and deploys the application when certain checks pass.

1. **CI Pipeline**:
   - Configure **GitHub Actions** or **GitLab CI** to automatically run tests on every push to the `development` and `main` branches.
   
2. **CD Pipeline**:
   - After successful tests, deploy the application to a free-tier hosting provider like **Heroku**, **Vercel**, or **Netlify**.

Example pipeline tasks:
- Install dependencies.
- Run unit tests.
- Deploy to production after successful tests.

---

## Deployment

### Frontend

Deploy the React application to platforms like **Vercel** or **Netlify**:
- Connect your GitHub repository to Vercel or Netlify.
- Configure build settings, ensuring the app builds correctly for production.

### Backend

Deploy the Django backend to a platform like **Heroku** or **DigitalOcean**:
- Create a **Heroku app** or use Docker for containerization.
- Configure your environment variables on the platform for production.

---

## Linting and Formatting

The project includes linting to enforce consistent code style and best practices.

1. **Frontend Linting**:
   - Install ESLint for JavaScript and JSX linting.
   - Run the linter with:
     ```bash
     npm run lint
     ```

2. **Backend Linting**:
   - Use **flake8** for Python linting.
   - Run the linter with:
     ```bash
     flake8 .
     ```

---