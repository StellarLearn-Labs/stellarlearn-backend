# stellarlearn-backend

> A Node.js + PostgreSQL REST API powering authentication, course management, enrollment, and progress tracking for StellarLearn.

---

## About

StellarLearn is an open-source Web3 course platform built on the Stellar blockchain. This repository contains the backend REST API responsible for user authentication, course and lesson management, enrollment, progress tracking, and certificate records.

---

## Tech Stack

- **Runtime:** Node.js 18+
- **Framework:** Express.js
- **Language:** TypeScript
- **Database:** PostgreSQL
- **ORM:** Prisma
- **Auth:** JWT
- **File Storage:** Cloudinary
- **Validation:** Zod

---

## Getting Started

### Prerequisites

- Node.js >= 18
- pnpm >= 8
- PostgreSQL >= 15

### Installation

```bash
git clone https://github.com/StellarLearn-Labs/stellarlearn-backend.git
cd stellarlearn-backend
pnpm install
cp .env.example .env
```

### Environment Variables

```env
DATABASE_URL=postgresql://user:password@localhost:5432/stellarlearn
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=7d
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
PORT=5000
```

### Database Setup

```bash
pnpm prisma migrate dev
pnpm prisma db seed
```

### Running Locally

```bash
pnpm dev
```

Server runs at [http://localhost:5000](http://localhost:5000).

---

## Project Structure

```
stellarlearn-backend/
├── src/
│   ├── modules/
│   │   ├── auth/               # Registration, login, JWT
│   │   ├── users/              # User profile management
│   │   ├── courses/            # Course CRUD
│   │   ├── lessons/            # Lesson management
│   │   ├── enrollments/        # Enrollment and progress
│   │   └── certificates/       # Certificate records
│   ├── middleware/             # Auth guard, error handler
│   ├── lib/                    # Prisma client, Cloudinary
│   ├── utils/                  # Helpers and validators
│   └── app.ts                  # Express app entry point
├── prisma/
│   ├── schema.prisma           # Database schema
│   └── seed.ts                 # Seed data
└── .env.example
```

---

## API Endpoints

| Method | Route | Description |
|--------|-------|-------------|
| POST | `/auth/register` | Register a new user |
| POST | `/auth/login` | Login and receive JWT |
| GET | `/courses` | List all published courses |
| GET | `/courses/:id` | Get course detail |
| POST | `/courses` | Create a course (creator) |
| POST | `/enrollments` | Enroll in a course |
| PATCH | `/enrollments/:id/progress` | Update lesson progress |
| GET | `/certificates/:address` | Get certificates by Stellar address |

---

## Contributing

Please read [CONTRIBUTING.md](./CONTRIBUTING.md) before opening a pull request.

1. Fork the repository
2. Create a feature branch: `git checkout -b feat/your-feature`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push and open a pull request targeting `main`

---

## Related Repositories

| Repo | Description |
|------|-------------|
| [stellarlearn-frontend](https://github.com/StellarLearn-Labs/stellarlearn-frontend) | Next.js web application |
| [stellarlearn-contracts](https://github.com/StellarLearn-Labs/stellarlearn-contracts) | Soroban smart contracts |

---

## License

MIT © [StellarLearn-Labs](https://github.com/StellarLearn-Labs)