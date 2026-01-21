# I. Render Hooks 🪝

> **Sumber:** [https://filamentphp.com/docs/5.x/advanced/render-hooks](https://filamentphp.com/docs/5.x/advanced/render-hooks)

---

## 🤔 Apa itu Render Hooks?

**Render Hooks** adalah titik di mana Anda bisa menyisipkan HTML/view custom tanpa publish views.

---

## 📝 Registering Render Hooks

```php
// Di AppServiceProvider atau PanelProvider
use Filament\Support\Facades\FilamentView;
use Illuminate\Support\Facades\Blade;

FilamentView::registerRenderHook(
    'panels::body.start',
    fn () => Blade::render('<livewire:announcement-banner />'),
);
```

---

## 📋 Available Render Hooks

### Panel Builder

| Hook                        | Lokasi            |
| --------------------------- | ----------------- |
| `panels::body.start`        | Awal body         |
| `panels::body.end`          | Akhir body        |
| `panels::content.start`     | Awal content      |
| `panels::content.end`       | Akhir content     |
| `panels::footer`            | Footer            |
| `panels::head.start`        | Awal head         |
| `panels::head.end`          | Akhir head        |
| `panels::sidebar.nav.start` | Awal sidebar nav  |
| `panels::sidebar.nav.end`   | Akhir sidebar nav |
| `panels::sidebar.footer`    | Footer sidebar    |
| `panels::topbar.start`      | Awal topbar       |
| `panels::topbar.end`        | Akhir topbar      |
| `panels::scripts.before`    | Sebelum scripts   |
| `panels::scripts.after`     | Setelah scripts   |
| `panels::styles.before`     | Sebelum styles    |
| `panels::styles.after`      | Setelah styles    |

### Table Builder

| Hook                            | Lokasi         |
| ------------------------------- | -------------- |
| `tables::toolbar.search.before` | Sebelum search |
| `tables::toolbar.search.after`  | Setelah search |

---

## 🎯 Scoping Render Hooks

```php
FilamentView::registerRenderHook(
    'panels::body.start',
    fn () => view('announcement'),
    scope: UserResource::class,  // Hanya di UserResource
);
```

### Multiple Scopes

```php
FilamentView::registerRenderHook(
    'panels::body.start',
    fn () => view('announcement'),
    scope: [UserResource::class, PostResource::class],
);
```

---

## 📦 Pass Data

```php
FilamentView::registerRenderHook(
    'panels::body.start',
    fn () => view('announcement', ['message' => 'Hello!']),
);
```

---

## 🎨 Rendering Hooks in Views

```blade
{{ \Filament\Support\Facades\FilamentView::renderHook('custom-hook-name') }}
```

---

## 🎯 Latihan Mandiri

Buat render hooks untuk:

- Banner di atas content
- Custom script di akhir body
- Footer tambahan di sidebar
