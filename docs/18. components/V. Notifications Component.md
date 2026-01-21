# V. Notifications Component 🔔

> **Sumber:** [https://filamentphp.com/docs/5.x/components/notifications](https://filamentphp.com/docs/5.x/components/notifications)

---

## 🤔 Rendering Notifications di Luar Panel

Gunakan notifications di aplikasi Laravel biasa (tanpa Filament panel).

---

## 🚀 Setup

Tambahkan Livewire component di layout:

```blade
<!DOCTYPE html>
<html>
<head>
    @filamentStyles
    @vite('resources/css/app.css')
</head>
<body>
    {{ $slot }}

    @livewire('notifications')

    @filamentScripts
    @vite('resources/js/app.js')
</body>
</html>
```

---

## 📤 Sending Notifications

```php
use Filament\Notifications\Notification;

Notification::make()
    ->title('Data berhasil disimpan')
    ->success()
    ->send();
```

---

## 📦 Di Controller

```php
class PostController extends Controller
{
    public function store(Request $request)
    {
        Post::create($request->validated());

        Notification::make()
            ->title('Post dibuat')
            ->success()
            ->send();

        return redirect()->route('posts.index');
    }
}
```
