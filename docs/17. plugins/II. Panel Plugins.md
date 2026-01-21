# II. Panel Plugins 🎛️

> **Sumber:** [https://filamentphp.com/docs/5.x/plugins/panel-plugins](https://filamentphp.com/docs/5.x/plugins/panel-plugins)

---

## 🤔 Apa itu Panel Plugin?

**Panel Plugin** menambahkan fitur ke panel Filament (resources, pages, widgets, dll).

---

## 🏗️ Plugin Class

```php
namespace Vendor\MyPlugin;

use Filament\Contracts\Plugin;
use Filament\Panel;

class MyPlugin implements Plugin
{
    protected bool $featureEnabled = true;

    public function getId(): string
    {
        return 'my-plugin';
    }

    public function register(Panel $panel): void
    {
        $panel
            ->resources([
                Resources\MyResource::class,
            ])
            ->pages([
                Pages\MyPage::class,
            ])
            ->widgets([
                Widgets\MyWidget::class,
            ]);
    }

    public function boot(Panel $panel): void
    {
        //
    }

    // Fluent config
    public function enableFeature(bool $condition = true): static
    {
        $this->featureEnabled = $condition;
        return $this;
    }
}
```

---

## 🔧 Fluent Instantiation

```php
class MyPlugin implements Plugin
{
    public static function make(): static
    {
        return app(static::class);
    }

    public static function get(): static
    {
        return filament('my-plugin');
    }
}
```

### Usage

```php
$panel->plugin(MyPlugin::make()->enableFeature())
```

---

## ⚙️ Per-Panel Configuration

```php
public function register(Panel $panel): void
{
    if ($panel->getId() === 'admin') {
        $panel->resources([
            AdminResource::class,
        ]);
    }

    if ($panel->getId() === 'app') {
        $panel->resources([
            AppResource::class,
        ]);
    }
}
```

---

## 📦 Distributing a Panel

```php
use Filament\PanelProvider;

class MyPanelProvider extends PanelProvider
{
    public function panel(Panel $panel): Panel
    {
        return $panel
            ->id('my-panel')
            ->path('my-panel')
            ->resources([...])
            ->pages([...]);
    }
}
```

---

## 🎯 Latihan Mandiri

Buat panel plugin dengan:

- Custom resource
- Custom page
- Fluent configuration
