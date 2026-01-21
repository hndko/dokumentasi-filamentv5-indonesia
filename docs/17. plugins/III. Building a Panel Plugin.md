# III. Building a Panel Plugin 🛠️

> **Sumber:** [https://filamentphp.com/docs/5.x/plugins/building-a-panel-plugin](https://filamentphp.com/docs/5.x/plugins/building-a-panel-plugin)

---

## 📋 Tutorial: Membuat Panel Plugin

Kita akan membuat plugin widget sederhana.

---

## Step 1: Create Plugin

```bash
composer create-project filament/plugin-skeleton my-widget-plugin
cd my-widget-plugin
```

---

## Step 2: Clean Up

Hapus file yang tidak diperlukan dan sesuaikan `composer.json`:

```json
{
  "name": "vendor/my-widget-plugin",
  "description": "My Filament Widget Plugin",
  "require": {
    "php": "^8.1",
    "filament/filament": "^5.0",
    "spatie/laravel-package-tools": "^1.9"
  },
  "autoload": {
    "psr-4": {
      "Vendor\\MyWidgetPlugin\\": "src/"
    }
  }
}
```

---

## Step 3: Setup Provider

```php
// src/MyWidgetPluginServiceProvider.php

namespace Vendor\MyWidgetPlugin;

use Spatie\LaravelPackageTools\Package;
use Spatie\LaravelPackageTools\PackageServiceProvider;
use Filament\Support\Facades\FilamentAsset;
use Filament\Support\Assets\Css;

class MyWidgetPluginServiceProvider extends PackageServiceProvider
{
    public static string $name = 'my-widget-plugin';

    public function configurePackage(Package $package): void
    {
        $package
            ->name(static::$name)
            ->hasViews();
    }

    public function packageBooted(): void
    {
        FilamentAsset::register([
            Css::make('my-widget-plugin', __DIR__ . '/../resources/css/plugin.css'),
        ], package: 'vendor/my-widget-plugin');
    }
}
```

---

## Step 4: Create Widget

```php
// src/Widgets/StatsWidget.php

namespace Vendor\MyWidgetPlugin\Widgets;

use Filament\Widgets\StatsOverviewWidget;
use Filament\Widgets\StatsOverviewWidget\Stat;

class StatsWidget extends StatsOverviewWidget
{
    protected function getStats(): array
    {
        return [
            Stat::make('Custom Stat', '100'),
        ];
    }
}
```

---

## Step 5: Create Plugin Class

```php
// src/MyWidgetPlugin.php

namespace Vendor\MyWidgetPlugin;

use Filament\Contracts\Plugin;
use Filament\Panel;

class MyWidgetPlugin implements Plugin
{
    public static function make(): static
    {
        return app(static::class);
    }

    public function getId(): string
    {
        return 'my-widget-plugin';
    }

    public function register(Panel $panel): void
    {
        $panel->widgets([
            Widgets\StatsWidget::class,
        ]);
    }

    public function boot(Panel $panel): void
    {
        //
    }
}
```

---

## Step 6: Update README

Dokumentasikan cara install dan gunakan plugin.

```markdown
# My Widget Plugin

## Installation

composer require vendor/my-widget-plugin

## Usage

$panel->plugin(MyWidgetPlugin::make())
```

---

## 🎯 Latihan Mandiri

Buat panel plugin yang berisi:

- Custom stats widget
- Custom chart widget
- Configuration options
