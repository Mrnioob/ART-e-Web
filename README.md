## ARTE Website

A portfolio/inquiry website built with **Laravel 12**, including an inquiry form and user authentication (login, register, profile, dashboard).

---

## Tech Stack

- **PHP**: ^8.2  
- **Framework**: Laravel 12  
- **Frontend**: Blade, Tailwind CSS, Vite  
- **Auth**: Laravel Breeze  
- **Queues**: Laravel queues (database driver by default)

---

## Features

- **Public pages**
  - Home page (`/`)
  - Inquiry page (`/inquire`) with form submission

- **Authentication**
  - User registration & login
  - Email verification (if enabled)
  - Dashboard for logged-in users (`/dashboard`)
  - Profile management (`/profile`)

- **Backend**
  - Structured routes in `routes/web.php` and `routes/auth.php`
  - Controllers under `app/Http/Controllers`
  - Configurable queue system in `config/queue.php`

---

## Getting Started (Local Development)

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

### 2. Install PHP dependencies

```bash
composer install
```

### 3. Environment file

```bash
cp .env.example .env
```

Edit `.env` and set:

- Database connection (`DB_*` values)
- `APP_NAME`, `APP_URL`
- Mail settings (optional)

Then generate the app key:

```bash
php artisan key:generate
```

### 4. Run migrations

Make sure your database exists, then:

```bash
php artisan migrate
```

### 5. Install JS dependencies & build assets

```bash
npm install
npm run dev   # for development (hot reloading)
# or
npm run build # for production build
```

### 6. Run the development server

```bash
php artisan serve
```

The app will be available at:

```text
http://localhost:8000
```

---

## Using Queues (Optional)

By default, the queue connection is:

```php
'default' => env('QUEUE_CONNECTION', 'database');
```

To use queues:

1. Ensure you have run the migrations for `jobs` and `failed_jobs`.
2. In `.env`, set:

   ```env
   QUEUE_CONNECTION=database
   ```

3. Run a queue worker:

   ```bash
   php artisan queue:work
   ```

If you dont need queues in development, you can set:

```env
QUEUE_CONNECTION=sync
```

---

## Running Tests

```bash
php artisan test
```

---

## Deployment Notes

For production, make sure to:

- Set in `.env`:
  - `APP_ENV=production`
  - `APP_DEBUG=false`
  - `APP_URL=https://your-domain.com`
- Run:

  ```bash
  composer install --no-dev --optimize-autoloader
  php artisan migrate --force
  npm install
  npm run build
  php artisan config:cache
  php artisan route:cache
  php artisan view:cache
  ```

- Configure your web server (Nginx/Apache) to serve the `public/` directory.

---

## License

This project is open-sourced under the [MIT license](https://opensource.org/licenses/MIT).
