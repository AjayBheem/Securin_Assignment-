# 🍲 Securin Recipe App

A full-stack application built for the **Securin Assessment**.  
It parses a large JSON dataset of US recipes, stores it in PostgreSQL, exposes RESTful APIs, and provides a React + Material-UI frontend for browsing and filtering recipes.

---

## 📌 Features

- Parse `US_recipes.json` and clean `NaN` values → stored as `NULL`
- PostgreSQL schema with JSONB for nutrients
- RESTful API (Node.js + Express)
  - `GET /api/recipes` → paginated, sorted by rating
  - `GET /api/recipes/search` → filter by title, cuisine, rating, calories, total_time
- React + Material-UI frontend
  - Table view with pagination & filters
  - Drawer detail view with nutrients
- Dockerized setup (Postgres + backend + frontend)
- Importer script (`scripts/import_recipes.js`) to load JSON data

---

## 🛠 Tech Stack

- **Frontend**: React (Vite) + Material-UI
- **Backend**: Node.js + Express + pg
- **Database**: PostgreSQL (JSONB for nutrients)
- **Containerization**: Docker & Docker Compose

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/your-username/securin-recipe-app.git
cd securin-recipe-app
```

### 2. Run with Docker (recommended)
```bash
docker-compose up --build
```
- Backend → [http://localhost:4000](http://localhost:4000)
- Frontend → [http://localhost:5173](http://localhost:5173)

### 3. Import dataset
```bash
cd backend
node scripts/import_recipes.js US_recipes.json
```

### 4. Local development (without Docker)
```bash
# Backend
cd backend
cp .env.example .env
psql "$DATABASE_URL" -f sql/schema.sql
npm install
npm run dev

# Frontend
cd ../frontend
cp .env.example .env
npm install
npm run dev
```

---

## 📡 API Examples

### Get paginated recipes
```
GET /api/recipes?page=1&limit=10
```

### Search recipes
```
GET /api/recipes/search?title=pie&cuisine=Italian&rating=>=4.5&total_time=<=60&calories=<=400&page=1&limit=10
```

---

## 📷 Screenshots (to be added)
- Recipe table view
- Drawer detail view

---

## 👨‍💻 Development Notes
- Code structured in **backend/**, **frontend/**, and **sql/**
- Importer handles both dict and list JSON formats
- `NaN` values automatically converted to `NULL` in DB

---

## 📝 License
This project was created as part of the **Securin interview assessment**.
