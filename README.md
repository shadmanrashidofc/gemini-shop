# Gemini Commerce

A modern, scalable e-commerce platform built on **Laravel 12** with a **Filament 3** administrative panel. Designed for extensibility, developer experience, and production readiness.

> **Note:** This project provides the foundational authentication layer, admin panel, and application shell. E-commerce features (products, categories, cart, checkout, payments) are ready to be built on top of this solid base.

## Features

- **User Authentication** — Full registration, login, password reset, and email verification via Laravel Breeze (Blade + Alpine.js stack)
- **Profile Management** — Update name, email, and password; delete account
- **Admin Panel** — Filament 3 dashboard with role-based access at `/shadman`
- **Queue & Job Processing** — Pre-configured database queue driver for background jobs
- **Testing Suite** — Pest + PHPUnit with authentication tests out of the box
- **Modern Frontend** — Tailwind CSS, Alpine.js, and Vite hot-reload for rapid development
- **Dark Mode** — Built-in dark mode support via Tailwind
- **Responsive Design** — Mobile-first layout across all views

## Screenshots

> Screenshots coming soon.

| Page | Preview |
|------|---------|
| Welcome | `resources/views/welcome.blade.php` |
| Login | `resources/views/auth/login.blade.php` |
| Dashboard | `resources/views/dashboard.blade.php` |
| Admin Panel | Filament panel at `/shadman` |

## Technologies

| Layer | Technology |
|-------|-----------|
| **Backend** | PHP 8.2+, Laravel 12.x |
| **Admin Panel** | Filament 3.x |
| **Auth** | Laravel Breeze 2.x (Blade + Alpine) |
| **Frontend** | Blade, Alpine.js 3.x, Tailwind CSS 3.x |
| **Build** | Vite 7.x, Laravel Vite Plugin |
| **Database** | SQLite (dev) / MySQL / PostgreSQL / MariaDB |
| **Testing** | Pest 4.x, PHPUnit 11.x |
| **Queue** | Database-driven queue driver |
| **Cache** | Database-driven cache store |

## Installation

### Prerequisites

- PHP 8.2 or higher
- Composer 2.x
- Node.js 18+ and npm
- Database (SQLite for development, MySQL/PostgreSQL for production)

### Setup

```bash
# Clone the repository
git clone https://github.com/your-username/gemini-commerce.git
cd gemini-commerce

# Install PHP dependencies
composer install

# Install frontend dependencies
npm install

# Environment configuration
cp .env.example .env
php artisan key:generate

# Configure your database in .env, then run migrations
php artisan migrate

# Build frontend assets
npm run build

# Create storage symlink (for file uploads)
php artisan storage:link
```

### Quick Setup

```bash
composer run setup
```

This runs: `composer install`, copies `.env.example` → `.env`, generates an app key, runs migrations, installs npm packages, and builds assets.

### Development Server

```bash
composer run dev
```

Starts the PHP development server, queue listener, log watcher, and Vite dev server concurrently.

## Configuration

### Environment Variables

Key environment variables in `.env`:

| Variable | Default | Description |
|----------|---------|-------------|
| `APP_NAME` | `Laravel` | Application name |
| `APP_ENV` | `local` | Environment (`local`, `production`, `testing`) |
| `APP_DEBUG` | `true` | Enable/disable debug mode |
| `APP_URL` | `http://localhost` | Application URL |
| `DB_CONNECTION` | `sqlite` | Database driver |
| `SESSION_DRIVER` | `database` | Session storage driver |
| `QUEUE_CONNECTION` | `database` | Queue driver |
| `CACHE_STORE` | `database` | Cache store |

### Database

Default configuration uses **SQLite** for local development. To use MySQL:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=gemini_commerce
DB_USERNAME=root
DB_PASSWORD=
```

### Admin Panel

The Filament admin panel is available at `/shadman` after logging in as a registered user.

Panel configuration is in `app/Providers/Filament/ShadmanPanelProvider.php`. You can customize the path, colors, widgets, and resources.

## Usage

### User Routes

| Method | URI | Description |
|--------|-----|-------------|
| GET | `/` | Welcome page |
| GET | `/dashboard` | User dashboard (auth) |
| GET/POST | `/login` | Login |
| GET/POST | `/register` | Register |
| GET/POST | `/forgot-password` | Password reset request |
| GET/POST | `/reset-password/{token}` | Password reset |
| GET | `/profile` | Edit profile (auth) |
| PATCH | `/profile` | Update profile (auth) |
| DELETE | `/profile` | Delete account (auth) |

### Admin Routes

| URI | Description |
|-----|-------------|
| `/shadman` | Filament admin dashboard |
| `/shadman/login` | Admin login |

### Artisan Commands

```bash
php artisan inspire          # Display an inspiring quote
php artisan queue:work       # Process queued jobs
php artisan pail             # Tail log files (Laravel Pail)
```

### Testing

```bash
composer run test
# Or directly:
php artisan test
```

The test suite includes:
- Authentication tests (login, registration, password reset, email verification)
- Profile management tests
- Unit tests for application logic

## Folder Structure

```
gemini-commerce/
├── app/
│   ├── Http/
│   │   ├── Controllers/      # Application controllers
│   │   │   └── Auth/         # Authentication controllers
│   │   └── Requests/         # Form request validation
│   ├── Models/               # Eloquent models
│   ├── Providers/
│   │   ├── Filament/         # Filament panel provider
│   │   └── AppServiceProvider.php
│   └── View/
│       └── Components/       # Blade components
├── bootstrap/                # Framework bootstrap files
├── config/                   # Application configuration
├── database/
│   ├── factories/            # Model factories
│   ├── migrations/           # Database migrations
│   └── seeders/              # Database seeders
├── public/                   # Web server document root
├── resources/
│   ├── css/                  # Global styles
│   ├── js/                   # JavaScript entry points
│   └── views/                # Blade templates
│       ├── auth/             # Auth views
│       ├── components/       # UI components
│       ├── layouts/          # Layout templates
│       └── profile/          # Profile views
├── routes/
│   ├── auth.php              # Auth route definitions
│   ├── console.php           # Artisan commands
│   └── web.php               # Web routes
├── storage/                  # Logs, cache, sessions
├── tests/                    # Pest/PHPUnit tests
│   ├── Feature/              # Feature tests
│   └── Unit/                 # Unit tests
├── composer.json
├── package.json
├── tailwind.config.js
└── vite.config.js
```

## Future Improvements

- [ ] **Product Management** — CRUD for products with categories, variants, and pricing
- [ ] **Shopping Cart** — Guest and authenticated cart with session persistence
- [ ] **Checkout Flow** — Multi-step checkout with address management
- [ ] **Payment Integration** — Stripe, PayPal, or other payment gateway
- [ ] **Order Management** — Order processing, status tracking, and history
- [ ] **Inventory** — Stock management with low-stock alerts
- [ ] **Customer Reviews** — Ratings and reviews for products
- [ ] **Search** — Full-text product search with filters
- [ ] **API** — REST or GraphQL API for headless/omnichannel usage
- [ ] **Multi-language** — Localization support for multiple languages
- [ ] **Shipping** — Shipping rate calculation and tracking
- [ ] **Coupons & Discounts** — Promotional code system
- [ ] **Analytics Dashboard** — Sales, traffic, and conversion metrics
- [ ] **CI/CD Pipeline** — Automated testing and deployment via GitHub Actions

## License

This project is open-sourced software licensed under the [MIT license](LICENSE).
