# Security Policy

## Supported Versions

| Version | Supported          |
|---------|--------------------|
| 1.x     | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability in Gemini Commerce, please do **not** open a public issue.

Instead, send a private report to the maintainer via email or open a [GitHub Security Advisory](https://github.com/your-username/gemini-commerce/security/advisories).

Please include:

- A description of the vulnerability
- Steps to reproduce it
- The version(s) affected
- Any potential impact

You should receive a response within 48 hours. If the issue is confirmed, we will:

1. Acknowledge receipt of the report
2. Investigate and develop a fix
3. Release a security patch as soon as possible
4. Credit the reporter (if desired)

## Best Practices

- Keep PHP and all dependencies up to date
- Rotate `APP_KEY` before deploying to production
- Set `APP_DEBUG=false` in production environments
- Use HTTPS in production
- Regularly update `composer.lock` and `package-lock.json`
- Run `php artisan security:check` (if using Laravel Envoyer or similar)

## Dependencies

- [Laravel Security](https://laravel.com/docs/12.x/security) — framework security documentation
- [Filament Security](https://filamentphp.com/docs/3.x/support/security) — admin panel security
