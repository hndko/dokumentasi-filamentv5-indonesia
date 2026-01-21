# XV. Empty State 📭

> **Sumber:** [https://filamentphp.com/docs/5.x/components/empty-state](https://filamentphp.com/docs/5.x/components/empty-state)

---

## 🤔 Apa itu Empty State?

Placeholder saat tidak ada data.

---

## 🚀 Penggunaan

```blade
<x-filament::empty-state heading="Tidak ada data">
    Belum ada post yang dibuat.
</x-filament::empty-state>
```

---

## 📝 Description

```blade
<x-filament::empty-state
    heading="Tidak ada post"
    description="Mulai dengan membuat post pertama Anda."
/>
```

---

## 🎯 Icon

```blade
<x-filament::empty-state
    heading="Tidak ada pesan"
    icon="heroicon-o-inbox"
/>
```

### Icon Color

```blade
<x-filament::empty-state
    icon="heroicon-o-inbox"
    icon-color="primary"
/>
```

### Icon Size

```blade
<x-filament::empty-state
    icon-size="lg"
/>
```

---

## ⚡ Actions

```blade
<x-filament::empty-state
    heading="Tidak ada post"
>
    <x-slot name="actions">
        <x-filament::button href="/posts/create">
            Buat Post
        </x-filament::button>
    </x-slot>
</x-filament::empty-state>
```
