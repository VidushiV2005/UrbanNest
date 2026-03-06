# 🏠 UrbanNest — Real Estate Rental Platform

A full-stack rental platform connecting **property managers** and **tenants** — from listing to lease.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Next.js 15, React 18, TypeScript, Tailwind CSS |
| State | Redux Toolkit + RTK Query |
| Backend | Node.js, Express 5, TypeScript |
| Database | PostgreSQL + PostGIS (via Prisma ORM) |
| Auth | AWS Cognito + JWT |
| Storage | AWS S3 |
| Maps | Mapbox GL |

---

## Features

**Tenants**
- Search & filter properties by location, price, and amenities
- Save favorites, submit applications, track lease status

**Managers**
- Create and manage property listings (with image upload)
- Review tenant applications, manage leases and payments

---

## Project Structure

```
├── client/          # Next.js frontend (App Router)
│   ├── app/
│   │   ├── (auth)/          # AWS Cognito auth flow
│   │   ├── (dashboard)/     # Protected tenant & manager routes
│   │   └── (nondashboard)/  # Public pages (search, landing)
│   └── state/               # Redux store + RTK Query
│
└── server/          # Express backend
    ├── controllers/
    ├── routes/
    ├── middleware/   # JWT auth + role-based access
    └── prisma/       # DB schema & migrations
```

---

## Getting Started

### Prerequisites
- Node.js 18+, PostgreSQL with PostGIS
- AWS account (Cognito + S3)

### Setup

```bash
# Clone
git clone https://github.com/your-username/rentease.git

# Install dependencies
cd client && npm install
cd ../server && npm install

# Configure environment variables
cp client/.env.example client/.env.local
cp server/.env.example server/.env

# Run database migrations
cd server && npx prisma migrate dev

# Start development servers
cd client && npm run dev      # http://localhost:3000
cd server && npm run dev      # http://localhost:8000
```

---

## Environment Variables

**Client** (`.env.local`)
```
NEXT_PUBLIC_API_BASE_URL=
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_ID=
NEXT_PUBLIC_AWS_COGNITO_USER_POOL_CLIENT_ID=
NEXT_PUBLIC_MAPBOX_TOKEN=
```

**Server** (`.env`)
```
DATABASE_URL=
AWS_COGNITO_USER_POOL_ID=
AWS_S3_BUCKET_NAME=
AWS_REGION=
```

---

## API Overview

| Method | Endpoint | Access |
|---|---|---|
| GET | `/properties` | Public |
| GET | `/properties/:id` | Public |
| POST | `/applications` | Public |
| GET/PUT | `/tenants/:id` | Tenant |
| GET | `/tenants/:id/favorites` | Tenant |
| GET/POST | `/managers/:id/properties` | Manager |
| GET | `/managers/:id/applications` | Manager |

---

