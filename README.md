# FitLife

A personal fitness tracking web app built with Angular 19 and Spring Boot 3.4. Tracks workouts, nutrition, water intake, weight, and goals. No third-party integrations, no email required everything runs locally with a MySQL database.

## Features

- **Workouts** - Log exercises with sets, reps, weight, and duration. Manually enter calories burned from your fitness device.
- **Nutrition** - Log meals with full macro breakdown (calories, protein, carbs, fat). Supports custom entries.
- **Water** - Track daily water intake against a goal calculated from body weight.
- **Goals** - Set and track weight, workout frequency, and custom goals.
- **History** - Weekly/monthly charts for calories, workouts, and macros using Chart.js.
- **Profile** - Calculates BMI, BMR, and TDEE from your stats and suggests calorie/macro targets.

## Tech Stack

| Layer    | Technology                          |
|----------|-------------------------------------|
| Frontend | Angular 19, TypeScript, SCSS        |
| Backend  | Spring Boot 3.4.1, Java 21, JPA     |
| Database | MySQL 8                             |
| Charts   | Chart.js via ng2-charts             |

## Getting Started

### Prerequisites

- Node.js 18+
- Java 21+
- MySQL 8+

### Backend

```bash
cd fitlife-backend
```

Set the following environment variables (or let the defaults kick in for local dev):

| Variable              | Default                              | Description                     |
|-----------------------|--------------------------------------|---------------------------------|
| `DATASOURCE_URL`      | `jdbc:mysql://localhost:3306/fitlife`| MySQL JDBC URL                  |
| `DATASOURCE_USER`     | `root`                               | MySQL username                  |
| `DATASOURCE_PASSWORD` | `root`                               | MySQL password                  |
| `FRONTEND_URL`        | `http://localhost:4200`              | Allowed CORS origin             |
| `SERVER_PORT`         | `8090`                               | Port the API listens on         |

Then run:

```bash
./mvnw spring-boot:run
```

The API will be available at `http://localhost:8090`. The database schema is managed by Hibernate (`ddl-auto=update`) and seed data is applied via `data.sql` on startup.

### Frontend

```bash
cd fitlife-frontend
npm install
ng serve
```

Open `http://localhost:4200`. The dev proxy (`proxy.conf.json`) forwards `/api` requests to the backend.

## Project Structure

```
fitLife/
├── fitlife-backend/
│   └── src/main/java/com/fitlife/
│       ├── controller/    # REST endpoints
│       ├── service/       # Business logic
│       ├── model/         # JPA entities
│       ├── dto/           # Request/response objects
│       ├── repository/    # Spring Data repositories
│       └── config/        # CORS, security config
├── fitlife-frontend/
│   └── src/app/
│       ├── pages/         # One component per route
│       ├── services/      # HTTP clients and state
│       ├── layout/        # Header, sidebar, shell
│       ├── shared/        # Reusable UI components
└── README.md
```

## License

MIT

