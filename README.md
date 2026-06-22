# The Subscription Tracker & Renewal Dashboard

[cite_start]Developed for the **Quantiphi Vibe Coding Round** on the **Unstop** assessment platform[cite: 6, 8, 34, 35]. [cite_start]This application is a modular personal finance dashboard that aggregates a user's recurring SaaS applications and streaming subscriptions, tracks their upcoming renewal dates, and monitors monthly cash-flow burn rates[cite: 10].

## 🏗️ Clean, Scalable Architecture
Following strict enterprise guidelines, this system features a complete decoupling of responsibilities:
* [cite_start]**Server-Side Computation Engine:** All business logic, cost calculations, interval normalization, and date evaluations are computed entirely on the server side to maintain computational integrity[cite: 51].
* [cite_start]**Presentation Layer:** The frontend handles user interactions and visual presentation, relying entirely on the server's data schemas[cite: 52].

---

## 🧠 Satisfying the Problem Statement Criteria

### 1. Cost Uniformity Engine (Backend Logic)
[cite_start]Because subscriptions have varying billing cycles (Monthly vs. Yearly), the backend engine parses form submissions and dynamically normalizes annual subscription data down to a monthly rate[cite: 12, 18]. [cite_start]This guarantees that the top **Total Monthly Burn Rate** metric remains completely precise regardless of input structure[cite: 13, 18].

### 2. Date Intersect Calculator (Backend Logic)
[cite_start]The system evaluates input dates against a fixed current calendar time to determine the exact number of days remaining until the next billing event occurs[cite: 19]. [cite_start]If an active subscription's renewal falls within 7 days, the server flags it, triggering an amber **"Renewing Soon"** caution badge on the grid and incrementing the **Upcoming Renewals Alert Count** card[cite: 13, 15, 19].

### 3. The Vibe Check (State Management & Real-Time Simulation)
[cite_start]Clicking a row's interactive "Active / Paused" Toggle Switch updates the database state instantly without deleting the item from the records[cite: 16, 21]. Switching an item to "Paused":
* [cite_start]Visually greys out that table row instantly on the frontend[cite: 22].
* [cite_start]Triggers a backend state change that completely excludes that specific cost from the top Monthly Burn Rate metric, providing a real-time savings simulation[cite: 22].

---

## 🛠️ Tech Stack
* **Frontend:** HTML5, Tailwind CSS (via ultra-low latency CDN execution), JavaScript (Fetch API)
* **Backend:** Node.js, Express.js, CORS
* **Database Layer:** MySQL Workbench (PostgreSQL/Supabase ready schema included)

---

## 🚀 Rapid Local Setup & Testing

### 1. Database Setup (MySQL)
Execute the following query in your MySQL Workbench environment to initialize the schema:
```sql
CREATE DATABASE IF NOT EXISTS sub_dashboard;
USE sub_dashboard;

CREATE TABLE subscriptions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    service_name VARCHAR(255) NOT NULL,
    cost DECIMAL(10, 2) NOT NULL,
    billing_cycle ENUM('Monthly', 'Yearly') NOT NULL,
    next_renewal_date DATE NOT NULL,
    is_active BOOLEAN DEFAULT TRUE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);