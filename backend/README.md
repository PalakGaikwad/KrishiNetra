# KrishiNetra Backend API Guide

KrishiNetra is an AI-powered agricultural market and net-earning advisor. The backend provides APIs for authentication, market information, price analysis, net-earning calculations, and forecasting.

**Status:** Under development.

## 1. Setup

**Prerequisites:** Node.js (v20+) and MongoDB, if required by the current configuration.

```bash
cd backend
npm install
```

Copy `.env.example` to `.env` and configure the required environment variables, including database and JWT secrets.

Start the development server:

```bash
npm run dev
```

Default server URL: `http://localhost:5000`

## 2. API Overview

Base path: `/api/v1`

| Method | Endpoint | Description |
|---|---|---|
| POST | `/auth/register` | Register a user |
| POST | `/auth/login` | Authenticate a user |
| GET | `/users/me` | Get the current user's profile |
| GET | `/markets` | Retrieve and filter markets |
| GET | `/prices` | Retrieve market price history |
| POST | `/net-earning` | Calculate estimated net earnings |
| GET | `/forecast` | Get price forecast information |

## 3. Authentication and Errors

Authentication uses JWT-based tokens and cookies, according to the backend configuration. Protected endpoints require valid authentication.

Request validation uses Zod. Common response codes include:

- `200` – Request successful
- `201` – Resource created
- `400` – Invalid request or validation error
- `401` – Authentication required or invalid
- `404` – Resource not found
- `409` – Resource conflict, such as an existing email

## 4. Key API Parameters

- **Markets:** Optional latitude, longitude, radius, and state filters.
- **Prices:** Requires `marketId` and `commodity`.
- **Net Earnings:** Accepts commodity, quantity, farmer coordinates, and optional transport rate.
- **Forecast:** Requires `marketId` and `commodity`; forecast period may be configurable.

## 5. Notes

- Configure environment variables before running the backend.
- Use mock or seed data only when needed for development.
- Forecasts and recommendations depend on available data and the current implementation.
- Never commit actual environment files, credentials, or secrets.

**Repository:** [KrishiNetra on GitHub](https://github.com/PalakGaikwad/KrishiNetra)
