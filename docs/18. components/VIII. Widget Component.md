# VIII. Widget Component 📊

> **Sumber:** [https://filamentphp.com/docs/5.x/components/widget](https://filamentphp.com/docs/5.x/components/widget)

---

## 🤔 Rendering Widget di Blade

Gunakan widget Filament di halaman custom.

---

## 🚀 Membuat Widget

```bash
php artisan make:filament-widget StatsWidget
```

```php
namespace App\Livewire\Widgets;

use Filament\Widgets\StatsOverviewWidget;
use Filament\Widgets\StatsOverviewWidget\Stat;

class StatsWidget extends StatsOverviewWidget
{
    protected function getStats(): array
    {
        return [
            Stat::make('Total Posts', Post::count()),
        ];
    }
}
```

---

## 🎨 Render di Blade

```blade
<div>
    @livewire(\App\Livewire\Widgets\StatsWidget::class)
</div>
```

Atau dengan tag:

```blade
<livewire:app.livewire.widgets.stats-widget />
```

---

## 📦 Passing Properties

```php
// Di Widget
public ?int $userId = null;

protected function getStats(): array
{
    return [
        Stat::make('Posts', Post::where('user_id', $this->userId)->count()),
    ];
}
```

```blade
@livewire(\App\Livewire\Widgets\StatsWidget::class, ['userId' => $user->id])
```
