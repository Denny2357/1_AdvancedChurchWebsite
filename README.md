# Advanced Church Website

A modern, full-featured church website built with Laravel, React, and Inertia.js. Designed to provide a professional online presence for churches with member management, event scheduling, and content management capabilities.

## Features

- **Modern Stack**: Laravel 12 backend with React frontend and Inertia.js for seamless integration
- **Authentication**: Built-in user authentication with Laravel Fortify
- **Responsive Design**: Tailwind CSS for beautiful, mobile-first UI
- **Type Safe**: Full TypeScript support throughout the application
- **Real-time Development**: Hot module replacement with Vite
- **Testing**: Comprehensive testing setup with Pest PHP
- **Queue System**: Laravel queue support for background jobs

## Tech Stack

### Backend
- **Laravel 12** - Modern PHP framework
- **Laravel Fortify** - Authentication scaffolding
- **Laravel Wayfinder** - Navigation management
- **PHP 8.2+** - Latest PHP features

### Frontend
- **React 19** - UI library
- **Inertia.js** - Server-driven UI components
- **TypeScript** - Type-safe JavaScript
- **Tailwind CSS 4** - Utility-first CSS framework
- **Radix UI** - Accessible component library
- **Vite** - Next generation build tool

### Testing & Development
- **Pest PHP** - Modern PHP testing framework
- **ESLint** - JavaScript linting
- **Prettier** - Code formatter
- **Laravel Pint** - PHP code style fixer

## Prerequisites

- PHP 8.2 or higher
- Node.js 18+ and npm
- SQLite or another supported database
- Composer

## Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd 1_AdvancedChurchWebsite
   ```

2. **Run the setup script**
   ```bash
   composer setup
   ```

   This will automatically:
   - Install PHP dependencies via Composer
   - Copy `.env.example` to `.env`
   - Generate the application key
   - Run database migrations
   - Install Node dependencies
   - Build frontend assets

3. **Manual setup (if needed)**
   ```bash
   # Install dependencies
   composer install
   npm install

   # Setup environment
   cp .env.example .env
   php artisan key:generate

   # Setup database
   php artisan migrate

   # Build assets
   npm run build
   ```

## Development

### Start the Development Server

Run all services concurrently with:
```bash
composer run dev
```

This starts:
- Laravel development server (port 8000)
- Queue listener
- Vite dev server with HMR
- Pail log viewer

Or run services individually:

```bash
# Terminal 1 - Laravel Server
php artisan serve

# Terminal 2 - Vite Dev Server (HMR)
npm run dev

# Terminal 3 - Queue Listener
php artisan queue:listen --tries=1 --timeout=0

# Terminal 4 - View Logs
php artisan pail --timeout=0
```

### With Server-Side Rendering (SSR)

```bash
composer run dev:ssr
```

This also starts the Inertia SSR server for server-side rendering.

## Build

### Development Build
```bash
npm run build
```

### Production Build with SSR
```bash
npm run build:ssr
```

## Code Quality

### Linting & Formatting

```bash
# Lint and fix code
composer run lint

# Check lint without fixing
composer run lint:check

# Format code
npm run format

# Check format
npm run format:check

# Check types
npm run types:check
```

### Testing

Run all tests:
```bash
composer run test
```

Run specific test:
```bash
php artisan test tests/Feature/YourTest.php
```

Run CI checks (lint, format, types, tests):
```bash
composer run ci:check
```

## Project Structure

```
.
├── app/                    # Application code
│   ├── Models/            # Eloquent models
│   ├── Http/              # Controllers, requests, middleware
│   ├── Jobs/              # Queued jobs
│   └── Services/          # Business logic
├── database/              # Migrations, seeders, factories
├── resources/             # Frontend assets
│   ├── js/                # React components
│   ├── css/               # Stylesheets
│   └── views/             # Blade templates
├── routes/                # Route definitions
├── config/                # Configuration files
├── tests/                 # Test files
├── public/                # Publicly accessible files
└── storage/               # Application storage
```

## Environment Configuration

Copy `.env.example` to `.env` and update:

```env
APP_NAME="Advanced Church Website"
APP_ENV=local
APP_DEBUG=true
APP_URL=http://localhost:8000

DB_CONNECTION=sqlite
# or use MySQL:
# DB_CONNECTION=mysql
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=church_website
# DB_USERNAME=root
# DB_PASSWORD=
```

## Database

### Run Migrations
```bash
php artisan migrate
```

### Seed Database
```bash
php artisan db:seed
```

### Reset Database
```bash
php artisan migrate:fresh --seed
```

## Available Commands

```bash
# Laravel Artisan commands
php artisan make:controller ControllerName
php artisan make:model ModelName -m
php artisan make:migration migration_name
php artisan make:test TestName

# Composer scripts
composer setup              # Full setup
composer dev                # Start dev server
composer dev:ssr            # Start with SSR
composer lint               # Fix code style
composer lint:check         # Check code style
composer test               # Run tests
composer ci:check           # Full CI check
```

## Deployment

### Production Build
```bash
npm run build
composer install --no-dev --optimize-autoloader
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

### Environment Setup
```bash
php artisan key:generate
php artisan migrate --force
```

## Troubleshooting

### Port Already in Use
Change the port when running the development server:
```bash
php artisan serve --port=8001
```

### Node Modules Issues
```bash
rm -rf node_modules package-lock.json
npm install
```

### Database Issues
```bash
# Reset everything
php artisan migrate:fresh --seed

# Check migrations status
php artisan migrate:status
```

### Build Issues
```bash
# Clear cache
php artisan cache:clear
php artisan config:clear
php artisan view:clear

# Rebuild assets
npm run build
```

## Contributing

1. Create a feature branch: `git checkout -b feature/amazing-feature`
2. Commit changes: `git commit -m 'Add amazing feature'`
3. Push to branch: `git push origin feature/amazing-feature`
4. Open a pull request

## License

This project is open-source software licensed under the MIT license.

## Support

For issues and questions, please open an issue on the repository.

---

Made with ❤️ for the church community
