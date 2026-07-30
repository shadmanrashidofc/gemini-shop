# Contributing

Thank you for considering contributing to Gemini Commerce.

## Code of Conduct

This project adheres to a [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code.

## How to Contribute

### Reporting Bugs

1. Open a [GitHub Issue](https://github.com/your-username/gemini-commerce/issues/new)
2. Use a clear and descriptive title
3. Describe the exact steps to reproduce the problem
4. Provide the expected and actual behavior
5. Include screenshots if applicable
6. Specify your environment (OS, PHP version, browser, etc.)

### Suggesting Features

1. Open a [GitHub Issue](https://github.com/your-username/gemini-commerce/issues/new)
2. Explain the feature in detail and the problem it solves
3. Describe how the feature should work
4. Include any relevant examples or mockups

### Pull Requests

1. Fork the repository
2. Create a new branch from `main`:

   ```bash
   git checkout -b feature/my-feature
   ```

3. Make your changes following our coding standards
4. Write or update tests for your changes
5. Run the test suite to ensure nothing breaks:

   ```bash
   composer run test
   ```

6. Run Laravel Pint for code style:

   ```bash
   ./vendor/bin/pint
   ```

7. Commit your changes with a descriptive message
8. Push to your fork and submit a pull request against `main`

## Development Setup

```bash
composer install
npm install
cp .env.example .env
php artisan key:generate
php artisan migrate
npm run build
```

## Coding Standards

- Follow [PSR-12](https://www.php-fig.org/psr/psr-12/) coding style
- Use Laravel Pint for automatic formatting
- Write descriptive variable and method names
- Add type hints to all function signatures
- Document public methods with PHPDoc blocks where helpful
- Keep controllers thin — move business logic to dedicated classes

## Testing

All contributions must include tests covering the new functionality.

```bash
# Run the full test suite
composer run test

# Run a specific test file
php artisan test --filter=SomeTest
```

## Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat: add product search endpoint
fix: resolve cart total calculation overflow
docs: update installation instructions
test: add checkout validation tests
```

## Versioning

This project follows [Semantic Versioning 2.0.0](https://semver.org/).
