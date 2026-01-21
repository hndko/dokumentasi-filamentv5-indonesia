# I. Plugins - Getting Started 🔌

> **Sumber:** [https://filamentphp.com/docs/5.x/plugins/getting-started](https://filamentphp.com/docs/5.x/plugins/getting-started)

---

## 🤔 Apa itu Plugins?

**Plugins** adalah package yang extend fungsionalitas Filament. Ada 2 jenis:

1. **Panel Plugins** - Menambah fitur ke panel (resources, pages, widgets)
2. **Standalone Plugins** - Component yang bisa dipakai di mana saja

---

## 📦 Important Concepts

### Plugin Object

```php
use Filament\Contracts\Plugin;

class MyPlugin implements Plugin
{
    public function getId(): string
    {
        return 'my-plugin';
    }

    public function register(Panel $panel): void
    {
        // Register resources, pages, widgets
    }

    public function boot(Panel $panel): void
    {
        // Boot logic
    }
}
```

### Registering Assets

```php
use Filament\Support\Facades\FilamentAsset;

FilamentAsset::register([
    Css::make('my-plugin', __DIR__ . '/../resources/css/plugin.css'),
    Js::make('my-plugin', __DIR__ . '/../resources/js/plugin.js'),
], package: 'vendor/my-plugin');
```

---

## 🚀 Creating a Plugin

Gunakan skeleton:

```bash
composer create-project filament/plugin-skeleton my-plugin
```

---

## 📋 Plugin Usage

```php
// Di AdminPanelProvider
$panel->plugin(\Vendor\MyPlugin\MyPlugin::make())
```

---

## 🔄 Upgrading Plugins

Untuk upgrade dari v4 ke v5:

- Check breaking changes di upgrade guide
- Update service provider
- Test semua functionality

---

## 🔗 Helpful Links

- [Filament Plugins Directory](https://filamentphp.com/plugins)
- [Plugin Skeleton](https://github.com/filament/plugin-skeleton)

---

## 🎯 Latihan Mandiri

Explorasi:

- Install plugin dari direktori
- Lihat source code plugin populer
- Setup plugin skeleton
