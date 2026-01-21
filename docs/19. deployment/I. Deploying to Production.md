# I. Deploying to Production 🚀

> **Sumber:** [https://filamentphp.com/docs/5.x/deployment](https://filamentphp.com/docs/5.x/deployment)

---

## 🔒 Pastikan User Terotorisasi

Sebelum deploy, pastikan hanya user yang berwenang yang bisa akses panel.

```php
// Di User model
use Filament\Panel;

public function canAccessPanel(Panel $panel): bool
{
    if ($panel->getId() === 'admin') {
        return $this->is_admin && $this->hasVerifiedEmail();
    }

    return true;
}
```

---

## ⚡ Optimizing Filament

### 1. Cache Filament Components

```bash
php artisan filament:cache-components
```

### 2. Cache Icons

```bash
php artisan icons:cache
```

### 3. Clear Cache saat Deploy

```bash
php artisan filament:clear-cached-components
```

---

## 🔧 Enable OPcache

Tambahkan ke `php.ini`:

```ini
opcache.enable=1
opcache.memory_consumption=256
opcache.max_accelerated_files=20000
opcache.validate_timestamps=0
```

> ⚠️ `validate_timestamps=0` artinya harus clear cache setelah deploy!

---

## ⚡ Optimizing Laravel

```bash
# Cache config
php artisan config:cache

# Cache routes
php artisan route:cache

# Cache views
php artisan view:cache

# Cache events
php artisan event:cache

# Optimize autoloader
composer install --optimize-autoloader --no-dev
```

---

## 📦 Update Assets

Saat deploy, pastikan assets Filament ter-publish:

```bash
php artisan filament:assets
```

### Auto Publish di Deployment Script

```bash
#!/bin/bash
composer install --optimize-autoloader --no-dev
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan filament:cache-components
php artisan icons:cache
php artisan filament:assets
```

---

## 📋 Deployment Checklist

- [ ] `canAccessPanel()` sudah dikonfigurasi
- [ ] Environment variables sudah benar
- [ ] `APP_DEBUG=false`
- [ ] `APP_ENV=production`
- [ ] OPcache enabled
- [ ] Cache commands dijalankan
- [ ] Assets ter-publish
- [ ] Database sudah migrate

---

## 🔄 Contoh Deploy Script (Laravel Forge)

```bash
cd /home/forge/myapp.com
git pull origin main

composer install --no-interaction --prefer-dist --optimize-autoloader --no-dev

php artisan migrate --force
php artisan config:cache
php artisan route:cache
php artisan view:cache
php artisan filament:cache-components
php artisan icons:cache
php artisan filament:assets

php artisan queue:restart
```
