# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Laravel 12 application skeleton with Breeze authentication (Blade + Alpine.js)
- Filament 3 admin panel with custom `ShadmanPanelProvider`
- User registration, login, password reset, and email verification
- Profile management (edit name/email, update password, delete account)
- Database-driven queue, cache, and session configuration
- Pest + PHPUnit test suite with authentication and profile tests
- Tailwind CSS styling with dark mode support
- Vite build pipeline with HMR for development
- SQLite default database for zero-config local development
- MIT License

### Infrastructure

- Composer dependency management with `laravel/framework ^12.0`
- NPM dependency management with `vite ^7.0.7` and `tailwindcss ^3.1.0`
- PostCSS with Autoprefixer and Tailwind CSS forms plugin
- Laravel Pail for local log tailing
- Laravel Pint for automated code style fixes
