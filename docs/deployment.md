# Deployment

## Production Checklist

### 1. Environment Configuration

```bash
APP_ENV=production
APP_DEBUG=false
APP_URL=https://your-domain.com
```

### 2. Generate a Secure APP_KEY

```bash
php artisan key:generate
```

### 3. Database

Configure your production database in `.env`:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=gemini_commerce
DB_USERNAME=your_user
DB_PASSWORD=your_password
```

### 4. Optimize Laravel

```bash
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan event:cache
```

### 5. Build Frontend Assets

```bash
npm ci --production
npm run build
```

### 6. Storage Permissions

```bash
php artisan storage:link
chmod -R 775 storage bootstrap/cache
```

### 7. Queue Worker

Run a queue worker in production (use Supervisor for persistence):

```bash
php artisan queue:work --queue=high,default --sleep=3 --tries=3
```

### 8. Scheduler

Add the following cron entry:

```
* * * * * cd /path-to-project && php artisan schedule:run >> /dev/null 2>&1
```

## Server Requirements

| Requirement | Minimum |
|-------------|---------|
| PHP | 8.2+ |
| Composer | 2.x |
| Database | MySQL 8.0+ / MariaDB 10.3+ / PostgreSQL 14+ |
| Web Server | Nginx / Apache |
| Node.js | 18+ (for build only) |
| Extensions | BCMath, Ctype, Fileinfo, JSON, Mbstring, OpenSSL, PDO, Tokenizer, XML |

## Web Server Configuration

### Nginx

```nginx
server {
    listen 80;
    server_name your-domain.com;
    root /var/www/gemini-commerce/public;

    add_header X-Frame-Options "SAMEORIGIN";
    add_header X-Content-Type-Options "nosniff";

    index index.php;

    charset utf-8;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }

    error_page 404 /index.php;

    location ~ \.php$ {
        fastcgi_pass unix:/var/run/php/php8.2-fpm.sock;
        fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
        include fastcgi_params;
    }

    location ~ /\.(?!well-known).* {
        deny all;
    }
}
```
