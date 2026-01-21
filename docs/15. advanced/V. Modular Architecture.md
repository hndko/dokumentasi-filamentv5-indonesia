# V. Modular Architecture (DDD) 🏗️

> **Sumber:** [https://filamentphp.com/docs/5.x/advanced/modular-architecture](https://filamentphp.com/docs/5.x/advanced/modular-architecture)

---

## 🤔 Apa itu Modular Architecture?

Struktur modular/DDD membagi aplikasi menjadi modul-modul terpisah untuk maintainability lebih baik.

---

## 📦 Setup InterNACHI/Modular

```bash
composer require internachi/modular
php artisan modules:install
```

---

## 📁 Module Structure

```
app-modules/
└── shop/
    ├── composer.json
    ├── src/
    │   ├── Providers/
    │   │   └── ShopServiceProvider.php
    │   ├── Models/
    │   │   └── Product.php
    │   ├── Filament/
    │   │   ├── Resources/
    │   │   │   └── ProductResource.php
    │   │   └── Plugins/
    │   │       └── ShopPlugin.php
    │   └── ...
    └── resources/
        └── views/
```

---

## 🔌 Creating Plugin for Module

```php
namespace Modules\Shop\Filament\Plugins;

use Filament\Contracts\Plugin;
use Filament\Panel;

class ShopPlugin implements Plugin
{
    public function getId(): string
    {
        return 'shop';
    }

    public function register(Panel $panel): void
    {
        $panel->resources([
            ProductResource::class,
            OrderResource::class,
        ]);

        $panel->pages([
            DashboardPage::class,
        ]);
    }

    public function boot(Panel $panel): void
    {
        //
    }
}
```

---

## 📋 Register Plugin

```php
// Di AdminPanelProvider
$panel->plugin(new \Modules\Shop\Filament\Plugins\ShopPlugin())
```

---

## 🎯 Conditional Registration

```php
public function register(Panel $panel): void
{
    if ($panel->getId() === 'admin') {
        $panel->resources([
            AdminProductResource::class,
        ]);
    }

    if ($panel->getId() === 'customer') {
        $panel->pages([
            CatalogPage::class,
        ]);
    }
}
```

### Match Statement

```php
$resources = match ($panel->getId()) {
    'admin' => [AdminProductResource::class],
    'vendor' => [VendorProductResource::class],
    default => [],
};

$panel->resources($resources);
```

---

## 🔗 Sharing Resources

```php
// Di Shared module
namespace Modules\Shared\Filament\Resources;

class BaseProductResource extends Resource
{
    // Base implementation
}

// Di Admin module
class AdminProductResource extends BaseProductResource
{
    // Admin-specific overrides
}
```

---

## 📦 Register Livewire Components

```php
// Di ModuleServiceProvider
use Livewire\Livewire;

public function boot(): void
{
    Livewire::component('shop::product-card', ProductCard::class);
}
```

---

## 🎯 Latihan Mandiri

Buat modular structure untuk:

- Blog module dengan PostResource
- Shop module dengan ProductResource
- Shared module untuk base classes
