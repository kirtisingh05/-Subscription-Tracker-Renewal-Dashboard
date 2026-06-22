# SaaSify - Subscription Tracker & Renewal Dashboard

## Overview

SaaSify is a full-stack Subscription Tracker & Renewal Dashboard that helps users manage recurring SaaS products and streaming subscriptions in one place.

The application allows users to:

* Add and manage subscriptions
* Track renewal dates
* Monitor monthly spending (Burn Rate)
* Identify upcoming renewals
* Pause subscriptions to simulate savings
* View subscription insights through a dashboard

---

## Features

### Subscription Management

* Add new subscriptions
* Edit subscription details
* Delete subscriptions
* Track monthly and yearly plans
* Manage subscription status (Active / Paused)

### Monthly Burn Rate

The dashboard automatically calculates the total monthly spending across all active subscriptions.

For yearly subscriptions:

Monthly Cost = Annual Cost / 12

This provides a normalized monthly burn rate across all billing cycles.

### Upcoming Renewal Alerts

The system continuously evaluates renewal dates and highlights subscriptions renewing within the next 7 days.

### Active / Paused Toggle

Users can pause subscriptions without deleting them.

When a subscription is paused:

* The subscription remains visible
* The row is visually greyed out
* The subscription is excluded from Monthly Burn Rate calculations

This provides a real-time savings simulation.

### Renewing Soon Badge

Subscriptions with renewal dates within 7 days are automatically marked with a:

**Renewing Soon** badge.

---

## Tech Stack

### Frontend

* Next.js
* TypeScript
* Tailwind CSS
* React

### Backend

* Node.js
* Express.js
* TypeScript

### Database

* SQLite

---

## Project Structure

```text
frontend/
│
├── src/
│   ├── app/
│   │   └── dashboard/
│   ├── components/
│   ├── lib/
│   └── types/
│
backend/
│
├── src/
│   ├── routes/
│   ├── services/
│   └── index.ts
```

---

## Business Logic

### Monthly Burn Rate

```text
Monthly Subscription:
Monthly Cost = Cost

Yearly Subscription:
Monthly Cost = Cost / 12
```

Only Active subscriptions contribute to the Burn Rate.

---

### Upcoming Renewals

```text
Days Remaining =
Renewal Date - Current Date
```

If:

```text
Days Remaining <= 7
```

The subscription is flagged as:

```text
Renewing Soon
```

---

### Pause Subscription

When a user pauses a subscription:

```text
Status:
ACTIVE → PAUSED
```

Effects:

* Subscription remains in the dashboard
* UI is greyed out
* Burn Rate updates immediately
* Savings are reflected in real time

---

## Installation

### Clone Repository

```bash
git clone <repository-url>
```

### Frontend

```bash
cd frontend

npm install

npm run dev
```

Frontend runs on:

```text
http://localhost:3000
```

### Backend

```bash
cd backend

npm install

npm run dev
```

Backend runs on:

```text
http://localhost:5000
```

---

## API Endpoints

### Get Dashboard Metrics

```http
GET /api/dashboard
```

Response:

```json
{
  "monthlyBurnRate": 2450.50,
  "upcomingRenewals": 3
}
```

### Get Subscriptions

```http
GET /api/subscriptions
```

### Create Subscription

```http
POST /api/subscriptions
```

### Toggle Subscription Status

```http
PATCH /api/subscriptions/:id/status
```

---

## Future Improvements

* Authentication & Authorization
* Email Renewal Notifications
* Multi-Currency Support
* Recurring Payment Analytics
* Category-Based Insights
* Subscription Export Reports

---

## Assessment Requirements Covered

✅ Service Name, Cost, Billing Cycle, Renewal Date

✅ Monthly Burn Rate Calculation

✅ Upcoming Renewals Alert Count

✅ Renewing Soon Badge

✅ Active / Paused Toggle

✅ Real-Time Savings Simulation

✅ Renewal Date Tracking

✅ Subscription Dashboard

✅ Full-Stack Architecture

---

## Author

Kirti Singh

BE Information Technology | University of Mumbai

Graduating 2026
