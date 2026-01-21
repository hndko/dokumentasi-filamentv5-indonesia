# XI. Breadcrumbs 🍞

> **Sumber:** [https://filamentphp.com/docs/5.x/components/breadcrumbs](https://filamentphp.com/docs/5.x/components/breadcrumbs)

---

## 🤔 Apa itu Breadcrumbs?

Blade component untuk navigasi path.

---

## 🚀 Penggunaan

```blade
<x-filament::breadcrumbs :breadcrumbs="[
    '/' => 'Home',
    '/posts' => 'Posts',
    '' => 'Create', {{-- Current page --}}
]" />
```

---

## 📋 Dengan Array Variable

```php
// Di controller/component
$breadcrumbs = [
    route('home') => 'Home',
    route('posts.index') => 'Posts',
    '' => $post->title,
];
```

```blade
<x-filament::breadcrumbs :breadcrumbs="$breadcrumbs" />
```
