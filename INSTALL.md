# Installation Guide

This document describes how to generate a deployable version of the Directory Lister PHP framework from these source files.

## Prerequisites

Before you begin, ensure you have the following installed:

- **PHP** >= 8.2
  - The [Zip](https://www.php.net/manual/en/book.zip.php) extension (required for zip downloads)
  - The [DOM](https://www.php.net/manual/en/book.dom.php) extension (required for README rendering)
  - The [Fileinfo](https://www.php.net/manual/en/book.fileinfo.php) extension (required for README rendering)
- **Composer** - PHP dependency manager
- **Node.js** and **npm** - For building front-end assets

## Development Setup

To set up a development environment:

```bash
make dev
```

This will:
1. Install PHP dependencies via Composer
2. Install Node.js dependencies via npm

## Building for Production

To build the application for production deployment:

```bash
make prod
```

This will:
1. Install PHP dependencies (production only, optimized autoloader)
2. Install Node.js dependencies, build assets with Vite, and prune development dependencies

## Generating Release Artifacts

To generate distributable release packages:

```bash
make artifacts
```

This will:
1. Clear compiled assets
2. Build the application for production
3. Generate a tarball (`.tar.gz`) in the `artifacts/` directory
4. Generate a zip file (`.zip`) in the `artifacts/` directory

You can also generate individual artifact types:

```bash
make tar    # Generate tarball only
make zip    # Generate zip file only
```

## Manual Deployment

If you prefer to deploy manually:

1. Run the production build:
   ```bash
   make prod
   ```

2. Copy the following files/directories to your web server:
   - `app/` (excluding `app/cache/*` and `app/resources/`)
   - `.env.example`
   - `directory-lister.svg`
   - `index.php`
   - `LICENSE`
   - `README.md`

3. On your server, copy `.env.example` to `.env` and configure as needed.

4. Ensure your web server's document root points to the directory containing `index.php`.

## Additional Commands

| Command | Description |
|---------|-------------|
| `make update` | Update all dependencies |
| `make clear-assets` | Clear compiled assets |
| `make clear-cache` | Clear the application cache |
| `make test` | Run the test suite |
| `make cs` | Check coding standards |
| `make static-analysis` | Run static analysis |
| `make suite` | Run all checks (coding standards, static analysis, tests) |
