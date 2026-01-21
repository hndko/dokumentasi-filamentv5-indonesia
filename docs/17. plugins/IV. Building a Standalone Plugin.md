# IV. Building a Standalone Plugin 📦

> **Sumber:** [https://filamentphp.com/docs/5.x/plugins/building-a-standalone-plugin](https://filamentphp.com/docs/5.x/plugins/building-a-standalone-plugin)

---

## 📋 Tutorial: Membuat Standalone Plugin

Standalone plugin adalah component yang bisa dipakai di mana saja (forms, tables, dll).

---

## Step 1: Create Plugin

```bash
composer create-project filament/plugin-skeleton my-component-plugin
cd my-component-plugin
```

---

## Step 2: Clean Up

Struktur folder:

```
my-component-plugin/
├── composer.json
├── src/
│   ├── MyComponentPluginServiceProvider.php
│   └── Forms/
│       └── Components/
│           └── RatingInput.php
└── resources/
    └── views/
        └── forms/
            └── components/
                └── rating-input.blade.php
```

---

## Step 3: Setup Provider

```php
// src/MyComponentPluginServiceProvider.php

namespace Vendor\MyComponentPlugin;

use Spatie\LaravelPackageTools\Package;
use Spatie\LaravelPackageTools\PackageServiceProvider;
use Filament\Support\Facades\FilamentAsset;
use Filament\Support\Assets\Css;
use Filament\Support\Assets\AlpineComponent;

class MyComponentPluginServiceProvider extends PackageServiceProvider
{
    public static string $name = 'my-component-plugin';

    public function configurePackage(Package $package): void
    {
        $package
            ->name(static::$name)
            ->hasViews();
    }

    public function packageBooted(): void
    {
        FilamentAsset::register([
            Css::make('rating-input', __DIR__ . '/../resources/css/rating-input.css'),
            AlpineComponent::make('rating-input', __DIR__ . '/../resources/js/rating-input.js'),
        ], package: 'vendor/my-component-plugin');
    }
}
```

---

## Step 4: Create Component

```php
// src/Forms/Components/RatingInput.php

namespace Vendor\MyComponentPlugin\Forms\Components;

use Filament\Forms\Components\Field;

class RatingInput extends Field
{
    protected string $view = 'my-component-plugin::forms.components.rating-input';

    protected int $maxStars = 5;

    public function maxStars(int $max): static
    {
        $this->maxStars = $max;
        return $this;
    }

    public function getMaxStars(): int
    {
        return $this->maxStars;
    }
}
```

---

## Step 5: Create View

```blade
{{-- resources/views/forms/components/rating-input.blade.php --}}
<x-dynamic-component
    :component="$getFieldWrapperView()"
    :field="$field"
>
    <div
        x-data="{ rating: @entangle($getStatePath()) }"
        class="flex gap-1"
    >
        @for ($i = 1; $i <= $getMaxStars(); $i++)
            <button
                type="button"
                @click="rating = {{ $i }}"
                :class="rating >= {{ $i }} ? 'text-yellow-400' : 'text-gray-300'"
            >
                <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 20 20">
                    <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
                </svg>
            </button>
        @endfor
    </div>
</x-dynamic-component>
```

---

## Step 6: Add Styles

```css
/* resources/css/rating-input.css */
.rating-input button:hover {
  transform: scale(1.1);
  transition: transform 0.1s;
}
```

---

## Step 7: Usage

```php
use Vendor\MyComponentPlugin\Forms\Components\RatingInput;

RatingInput::make('rating')
    ->maxStars(5)
    ->label('Rating')
```

---

## 🎯 Latihan Mandiri

Buat standalone plugin untuk:

- Custom color picker
- Money input dengan format
- Phone number input dengan mask
