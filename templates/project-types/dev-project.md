# Development Project Scaffolding Template

**For AI Assistants**: Follow these instructions to scaffold a development project with frontend and backend in an empty folder. The defaults are **Next.js** (frontend) and **FastAPI** (backend). Offer alternatives but don't require the user to configure everything.

---

## Step 1: Ask Follow-Up Questions

Present the defaults and let the user confirm or customize:

```
Great — a development project! Here's what I'll set up by default:

- **Frontend**: Next.js (React, TypeScript, Tailwind CSS)
- **Backend**: FastAPI (Python, uvicorn)
- **Database**: None by default (I can add PostgreSQL if you need one)

1. **Project name?** (e.g., "my-app", "task-manager")
2. **Use these defaults?** Or would you prefer a different stack?
   - Frontend alternatives: React (Vite), Vue, Angular, SvelteKit
   - Backend alternatives: Django, Express, NestJS, Go
3. **Need a database?** (PostgreSQL recommended — I'll add a docker-compose for it)
```

If the user says "yes" or "defaults are fine" or just gives a project name, proceed with Next.js + FastAPI.

---

## Step 2: Create Project Structure

### 2.1 Root Files

```
{project_root}/
├── README.md
├── .gitignore
├── docker-compose.yml      # only if database requested
├── frontend/               # Next.js app
└── backend/                # FastAPI app
```

### 2.2 Root README.md

```markdown
# {{PROJECT_NAME}}

{{PROJECT_DESCRIPTION}}

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js (React, TypeScript, Tailwind CSS) |
| Backend | FastAPI (Python) |
| Database | {{DATABASE or "None configured"}} |

## Getting Started

### Prerequisites

- Node.js 18+ and npm/pnpm
- Python 3.11+
- {{if DATABASE}} Docker (for database) {{/if}}

### Backend

```bash
cd backend
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

API docs: http://localhost:8000/docs

### Frontend

```bash
cd frontend
npm install
npm run dev
```

App: http://localhost:3000

{{if DATABASE}}
### Database

```bash
docker-compose up -d
```
{{/if}}

## Project Structure

```
├── frontend/          # Next.js application
│   ├── src/
│   │   ├── app/       # App Router pages and layouts
│   │   └── components/
│   └── package.json
├── backend/           # FastAPI application
│   ├── app/
│   │   ├── main.py    # FastAPI entry point
│   │   ├── routers/   # API route modules
│   │   └── models/    # Data models
│   └── requirements.txt
└── docs/              # Framework and project docs
```
```

### 2.3 Root .gitignore

```gitignore
# OS
.DS_Store
Thumbs.db

# Editors
.vscode/
.idea/
*.swp

# Node
node_modules/
.next/
out/

# Python
__pycache__/
*.pyc
*.pyo
venv/
.venv/
*.egg-info/

# Environment
.env
.env.local
.env.*.local

# Database
*.sqlite3
pgdata/
```

---

## Step 3: Scaffold Frontend (Next.js)

Run `npx create-next-app@latest` inside the project root to create the `frontend/` directory:

```bash
npx create-next-app@latest frontend --typescript --tailwind --eslint --app --src-dir --no-import-alias
```

If the command fails or is unavailable, create the frontend manually:

```
frontend/
├── package.json
├── tsconfig.json
├── next.config.ts
├── tailwind.config.ts
├── postcss.config.mjs
├── src/
│   └── app/
│       ├── layout.tsx
│       ├── page.tsx
│       └── globals.css
└── public/
```

**package.json** (minimal):
```json
{
  "name": "{{PROJECT_NAME}}-frontend",
  "version": "0.1.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "react": "^19",
    "react-dom": "^19",
    "next": "^15"
  },
  "devDependencies": {
    "typescript": "^5",
    "@types/react": "^19",
    "@types/react-dom": "^19",
    "tailwindcss": "^4",
    "@tailwindcss/postcss": "^4",
    "eslint": "^9",
    "eslint-config-next": "^15"
  }
}
```

**src/app/page.tsx** (starter):
```tsx
export default function Home() {
  return (
    <main className="flex min-h-screen flex-col items-center justify-center p-8">
      <h1 className="text-4xl font-bold mb-4">{{PROJECT_NAME}}</h1>
      <p className="text-lg text-gray-600">Frontend is running. Backend API at <code>http://localhost:8000/docs</code></p>
    </main>
  );
}
```

---

## Step 4: Scaffold Backend (FastAPI)

Create the `backend/` directory with:

```
backend/
├── requirements.txt
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── routers/
│   │   ├── __init__.py
│   │   └── health.py
│   └── models/
│       └── __init__.py
```

**requirements.txt**:
```
fastapi>=0.115
uvicorn[standard]>=0.34
pydantic>=2.0
python-dotenv>=1.0
```

**app/main.py**:
```python
from fastapi import FastAPI
from fastapi.middleware.cors import CORSMiddleware

from app.routers import health

app = FastAPI(title="{{PROJECT_NAME}} API")

app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost:3000"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

app.include_router(health.router)


@app.get("/")
async def root():
    return {"message": "{{PROJECT_NAME}} API is running"}
```

**app/routers/health.py**:
```python
from fastapi import APIRouter

router = APIRouter(prefix="/health", tags=["health"])


@router.get("")
async def health_check():
    return {"status": "healthy"}
```

---

## Step 5: Database (Optional — only if requested)

If the user asked for a database, create `docker-compose.yml` in the project root:

```yaml
services:
  db:
    image: postgres:17
    restart: unless-stopped
    environment:
      POSTGRES_USER: {{PROJECT_NAME}}
      POSTGRES_PASSWORD: localdev
      POSTGRES_DB: {{PROJECT_NAME}}
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data

volumes:
  pgdata:
```

Also add to `backend/requirements.txt`:
```
sqlalchemy>=2.0
psycopg2-binary>=2.9
alembic>=1.14
```

---

## Step 6: Alternative Stacks

If the user chose a different stack, adapt the scaffolding:

| Frontend Choice | What to do instead of Step 3 |
|----------------|------------------------------|
| React (Vite) | `npm create vite@latest frontend -- --template react-ts` |
| Vue | `npm create vue@latest frontend` |
| Angular | `npx @angular/cli new frontend` |
| SvelteKit | `npx sv create frontend` |

| Backend Choice | What to do instead of Step 4 |
|---------------|------------------------------|
| Django | `django-admin startproject backend` with DRF |
| Express | `mkdir backend && cd backend && npm init -y` with express + TypeScript |
| NestJS | `npx @nestjs/cli new backend` |
| Go | `mkdir backend` with `go mod init` and net/http or Gin |

Adapt the README, .gitignore, and docker-compose accordingly.

---

## Step 7: Handoff to Framework Setup

Tell the user:

```
Your development project is scaffolded! Here's what's ready:

- frontend/ — Next.js app (run with `cd frontend && npm install && npm run dev`)
- backend/ — FastAPI app (run with `cd backend && pip install -r requirements.txt && uvicorn app.main:app --reload`)
{{if DATABASE}}
- docker-compose.yml — PostgreSQL database (run with `docker-compose up -d`)
{{/if}}

Continuing with framework setup...
```

Then return control to `INSTALLATION.md` Step 1 to continue with framework initialization. The project information for Step 1 is:

- **Project Name**: `{{PROJECT_NAME}}`
- **Project Type**: Development project (frontend + backend)
- **Current Phase**: New — initial scaffolding complete
- **Tech Stack**: Next.js, React, TypeScript, Tailwind CSS, FastAPI, Python {{+ PostgreSQL if requested}}
- **Primary Language**: TypeScript (frontend), Python (backend)
- **Dev Command**: `cd frontend && npm run dev` / `cd backend && uvicorn app.main:app --reload`
- **Test Command**: `cd frontend && npm test` / `cd backend && pytest`
- **Build Command**: `cd frontend && npm run build`
