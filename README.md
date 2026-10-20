# Hoop House — PHP + MySQL MVP

## Requirements
- PHP 8.1+ with PDO MySQL extension
- MySQL 8+ or MariaDB
- Local PHP server (XAMPP or PHP CLI)

## Setup
1. In MySQL Workbench, open `database/schema.sql` and run it (creates `hoop_house` and tables). It is safe to run more than once, but does not reset existing records.
2. Set your local MySQL credentials in `config/db.php`, or environment variables `DB_HOST`, `DB_NAME`, `DB_USER`, `DB_PASS`.
3. Open a terminal in this project directory and run `php -S localhost:8000` (or copy folder to XAMPP `htdocs` and start Apache).
4. Open http://localhost:8000 (or http://localhost/hoop-house-mvp/ in XAMPP).
5. Create a customer account in the browser.
6. To make a staff account, use MySQL Workbench to update **your own test account**: `UPDATE users SET role='staff' WHERE email='YOUR_TEST_EMAIL';` Log out and log back in.
7. Staff can add gym sessions, add equipment, issue and return equipment. Customers can register for gym, create teams, request team membership, and request equipment.

## Important MVP limitations
- Prototype for local class demonstration; not production ready.
- Team recommendations are a basic recruiting-team listing, not personalized ranking.
- Leagues and league team tables exist but do not yet have user interface screens.
- No registration cancellation, staff registration list, damaged-item return handling, or overdue tracking yet.
- The schema uses 10 tables; it is an initial simplified version of the ERD.
- For a public deployment, add secure staff provisioning, HTTPS, rate limiting, stronger validation, audit logging, and additional authorization checks.
- Bootstrap is loaded from CDN and is an open-source third-party library; credit Bootstrap in your report.
