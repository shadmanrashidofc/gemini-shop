# Architecture

## Overview

Gemini Commerce follows the standard **Laravel MVC** architecture with a **Filament 3** admin panel overlay. The application is structured into three conceptual layers:

```
HTTP Layer       → Controllers, Middleware, Form Requests
Business Layer   → Models, Services (future), Actions (future)
Data Layer       → Migrations, Factories, Seeders, Database
```

## Request Lifecycle

```
Browser
  → public/index.php
    → bootstrap/app.php
      → Service Providers (AppServiceProvider, ShadmanPanelProvider)
        → Route Middleware (auth, verified, guest)
          → Controllers
            → Models / Database
              → Blade Views / Filament Pages
```

## Key Components

### Authentication

Laravel Breeze provides the authentication scaffolding. All auth logic lives in:

- `app/Http/Controllers/Auth/` — Auth controllers (login, register, password reset, email verification)
- `app/Http/Requests/Auth/LoginRequest.php` — Login validation
- `resources/views/auth/` — Auth Blade templates
- `routes/auth.php` — Auth route definitions

### Admin Panel

Filament 3 is configured via a custom panel provider:

- `app/Providers/Filament/ShadmanPanelProvider.php` — Panel configuration (ID, path, colors, middleware)

The panel auto-discovers resources, pages, and widgets from:
- `app/Filament/Resources/`
- `app/Filament/Pages/`
- `app/Filament/Widgets/`

### User Profile

The standard Breeze profile management flow:

- `app/Http/Controllers/ProfileController.php` — Edit, update, and delete profile
- `app/Http/Requests/ProfileUpdateRequest.php` — Profile validation
- `resources/views/profile/` — Profile Blade templates

## Database

Default driver: SQLite (for development)

Supported drivers (via config):
- SQLite
- MySQL / MariaDB
- PostgreSQL
- SQL Server

### Schema

| Table | Purpose |
|-------|---------|
| `users` | Application users |
| `password_reset_tokens` | Password reset tokens |
| `sessions` | Session storage |
| `cache` | Cache store |
| `jobs` | Queue job storage |
| `job_batches` | Batch job tracking |
| `failed_jobs` | Failed job records |

## Frontend

- **Blade** — Server-side templating
- **Alpine.js 3** — Client-side interactivity
- **Tailwind CSS 3** — Utility-first styling
- **Vite** — Asset bundling with HMR

## Testing

- **Pest 4** — Testing framework
- **PHPUnit 11** — Underlying test runner
- **In-memory SQLite** — Test database isolation

## Queues & Jobs

Configured to use the `database` queue driver by default. The `jobs`, `job_batches`, and `failed_jobs` tables are included in the migrations.

## Configuration Files

| File | Purpose |
|------|---------|
| `.env` | Environment-specific configuration |
| `config/app.php` | Application settings (name, URL, timezone) |
| `config/database.php` | Database connections |
| `config/session.php` | Session driver and lifetime |
| `config/cache.php` | Cache store configuration |
| `config/queue.php` | Queue connection settings |
| `config/mail.php` | Mail driver and SMTP settings |
| `config/filesystems.php` | Filesystem disks |
| `config/services.php` | Third-party service credentials |
| `config/auth.php` | Authentication guards and providers |
| `config/logging.php` | Log channels and levels |
