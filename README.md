# Hoop House — Basketball Facility Management

Hoop House is a PHP and MySQL basketball facility management MVP. Customers can register for open gym, create and join teams, and request equipment. Staff can manage gym sessions, equipment, and checkouts.

## Requirements

- PHP 8.1 or newer, with the PDO MySQL extension enabled
- MySQL 8+ or MariaDB
- MySQL Workbench (recommended for importing the schema), or another MySQL client
- A local PHP server (PHP CLI or XAMPP)

## Run Hoop House locally

### 1. Clone the repository

```bash
git clone https://github.com/xjtrail-code/hoop-house.git
cd hoop-house
```

### 2. Set up the database

Start your local MySQL server. In MySQL Workbench, connect to your local MySQL instance, open `database/schema.sql`, and execute the script.

This creates the `hoop_house` database and its tables, plus sample equipment records. The script is designed to be rerunnable without resetting existing records.

### 3. Configure your local database connection

Copy the example configuration into a new file named `config/db.php`.

**Windows PowerShell:**
```powershell
Copy-Item config/db.example.php config/db.php
```

**macOS / Linux:**
```bash
cp config/db.example.php config/db.php
```

Open `config/db.php` and enter the MySQL credentials **for your own computer**:

```php
$host = '127.0.0.1';
$dbname = 'hoop_house';
$username = 'root';
$password = 'YOUR_LOCAL_MYSQL_PASSWORD';
```

Replace the placeholder with your actual local MySQL password (or an empty string if your local account has no password). If your MySQL username or host differs, update those too.

**Never commit `config/db.php` or real passwords.** The file is excluded by `.gitignore`. Only `config/db.example.php` is shared on GitHub.

### 4. Start the application

From the repository's root directory, run:

```bash
php -S localhost:8000
```

Open **http://localhost:8000** in your browser.

Alternatively, use XAMPP: put the project folder in `htdocs`, start Apache and MySQL, and visit `http://localhost/hoop-house/` (assuming the folder is named `hoop-house`).

### 5. Create and test an account

Register a customer account in the browser. To test staff functionality locally, update **your own test account** in MySQL Workbench:

```sql
USE hoop_house;
UPDATE users SET role = 'staff' WHERE email = 'YOUR_TEST_EMAIL';
```

Log out and log back in. Do not use this manual staff-provisioning method for a public deployment.

## Features

- **Customers:** Create accounts, register for open gym, create teams, request team membership, and request equipment.
- **Staff:** Add gym sessions, manage equipment, and issue and return equipment.
- **Database:** MySQL tables for users, sessions, registrations, teams, leagues, equipment, and checkouts.

## Troubleshooting

- **Database connection failed:** Confirm MySQL is running, `hoop_house` exists, and the username/password in your local `config/db.php` are correct.
- **Missing tables:** Re-run `database/schema.sql` in MySQL Workbench.
- **`could not find driver`:** Enable/install PHP's `pdo_mysql` extension.
- **`php` command not found:** Install PHP or use XAMPP, and make sure PHP is available on your PATH.

## Current MVP limitations

- Intended for local demonstration and learning; **not production ready**.
- Team recommendations are a basic recruiting-team listing, not personalized rankings.
- League tables exist, but league-management UI screens are not implemented.
- Registration cancellation, staff registration lists, damaged-item return handling, and overdue tracking are not implemented.
- The initial schema has 10 tables and is a simplified version of the ERD.
- Before public deployment, implement secure staff provisioning, HTTPS, rate limiting, stronger input validation, audit logging, and additional authorization checks.
- The interface uses the open-source Bootstrap library loaded from a CDN.

## Project status

The local PHP/MySQL MVP is available for cloning and setup. A publicly hosted version is not yet deployed.
