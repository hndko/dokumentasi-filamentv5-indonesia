# IX. Avatar 👤

> **Sumber:** [https://filamentphp.com/docs/5.x/components/avatar](https://filamentphp.com/docs/5.x/components/avatar)

---

## 🤔 Apa itu Avatar?

Blade component untuk menampilkan gambar profil.

---

## 🚀 Penggunaan

```blade
<x-filament::avatar
    src="https://example.com/avatar.jpg"
    alt="John Doe"
/>
```

---

## 🔲 Rounding

```blade
{{-- Bulat (default) --}}
<x-filament::avatar
    src="..."
    circular
/>

{{-- Kotak rounded --}}
<x-filament::avatar
    src="..."
/>
```

---

## 📏 Size

```blade
<x-filament::avatar
    src="..."
    size="sm"
/>

{{-- sm, md, lg, atau custom --}}
<x-filament::avatar
    src="..."
    :size="64"
/>
```
