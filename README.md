# Evently

An event discovery and booking app built with React, TypeScript, Express, and MongoDB.

## Features

- Event discovery landing page and upcoming event listing
- Search by event name or category, plus category filtering
- Event details with date, time, venue, availability, and registration
- Account registration, sign-in, and sign-out
- Personal booking list
- Admin dashboard with event creation, editing, deletion, and simple totals
- MongoDB models for users, events, and bookings

## Requirements

- Node.js 20.19+ (Node.js 24 recommended)
- MongoDB local instance or MongoDB Atlas database

## Run locally

1. Configure the API:

   ```powershell
   cd server
   Copy-Item .env.example .env
   ```

   Update `MONGODB_URI`, set `JWT_SECRET` to a random secret of at least 32 characters, and set a strong `ADMIN_PASSWORD`. The admin credentials in this file are used only when creating the initial admin account.

2. Install dependencies and create the initial admin account and demo events:

   ```powershell
   npm install
   npm run seed
   ```

   Run this from the `server` directory. The seed operation creates demo events only if they do not already exist. It creates the admin account only if one does not already exist.

3. Start the API in one terminal:

   ```powershell
   npm run dev
   ```

4. In a second terminal, start the client:

   ```powershell
   cd client
   npm install
   npm run dev
   ```

   Open the local URL printed by Vite (normally `http://localhost:5173`). Vite proxies `/api` requests to the Express API at `http://localhost:4000`.

## Production

Build the frontend with `cd client; npm run build`. Set `CLIENT_ORIGIN` to the deployed frontend origin, set `NODE_ENV=production`, and provide `MONGODB_URI` and a private `JWT_SECRET` to the API. The frontend can be hosted separately; set `VITE_API_URL` to the deployed API's `/api` base URL if it is not served from the same origin.

The API uses an HTTP-only session cookie. Serve the production frontend and API over HTTPS, and configure CORS to allow only the frontend origin.
