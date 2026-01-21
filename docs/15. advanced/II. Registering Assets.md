# II. Registering Assets 📦

> **Sumber:** [https://filamentphp.com/docs/5.x/advanced/assets](https://filamentphp.com/docs/5.x/advanced/assets)

---

## 🤔 Tentang Assets

Filament menyediakan cara untuk mendaftarkan CSS dan JavaScript custom.

---

## 📋 FilamentAsset Facade

```php
use Filament\Support\Facades\FilamentAsset;
use Filament\Support\Assets\Css;
use Filament\Support\Assets\Js;

// Di AppServiceProvider boot()
FilamentAsset::register([
    Css::make('custom-styles', resource_path('css/custom.css')),
    Js::make('custom-scripts', resource_path('js/custom.js')),
]);
```

---

## 🎨 Registering CSS

### Basic CSS

```php
Css::make('custom-styles', resource_path('css/custom.css'))
```

### CSS dari URL

```php
Css::make('google-fonts', 'https://fonts.googleapis.com/css2?family=Inter')
```

### Lazy Loading CSS

```php
Css::make('heavy-styles', resource_path('css/heavy.css'))
    ->loadedOnRequest()
```

---

## 📜 Registering JavaScript

### Basic JS

```php
Js::make('custom-scripts', resource_path('js/custom.js'))
```

### JS dari URL

```php
Js::make('alpine-plugins', 'https://cdn.example.com/alpine-plugin.js')
```

### Lazy Loading JS

```php
Js::make('chart-lib', resource_path('js/chart.js'))
    ->loadedOnRequest()
```

---

## 📦 Script Data

```php
use Filament\Support\Facades\FilamentAsset;

FilamentAsset::registerScriptData([
    'apiUrl' => config('app.api_url'),
    'userId' => auth()->id(),
]);
```

### Akses di JavaScript

```js
const apiUrl = window.filamentData.apiUrl;
```

---

## 🔌 Assets untuk Plugin

```php
FilamentAsset::register([
    Css::make('my-plugin-styles', __DIR__ . '/../../resources/css/plugin.css'),
], package: 'vendor/my-plugin');
```

---

## 🎯 Latihan Mandiri

Register assets untuk:

- Custom CSS file
- JavaScript library dari CDN
- Script data untuk API config
