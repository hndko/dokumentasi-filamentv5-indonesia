# XX. Link 🔗

> **Sumber:** [https://filamentphp.com/docs/5.x/components/link](https://filamentphp.com/docs/5.x/components/link)

---

## 🤔 Apa itu Link?

Text link component dengan styling.

---

## 🚀 Penggunaan

```blade
<x-filament::link href="/posts">
    Lihat semua posts
</x-filament::link>
```

---

## 🔘 Sebagai Button

```blade
<x-filament::link tag="button" wire:click="doSomething">
    Klik saya
</x-filament::link>
```

---

## 📏 Size

```blade
<x-filament::link size="sm">Small</x-filament::link>
<x-filament::link size="md">Medium</x-filament::link>
<x-filament::link size="lg">Large</x-filament::link>
```

---

## 🔤 Font Weight

```blade
<x-filament::link weight="normal">Normal</x-filament::link>
<x-filament::link weight="medium">Medium</x-filament::link>
<x-filament::link weight="semibold">Semibold</x-filament::link>
<x-filament::link weight="bold">Bold</x-filament::link>
```

---

## 🎨 Color

```blade
<x-filament::link color="primary">Primary</x-filament::link>
<x-filament::link color="success">Success</x-filament::link>
<x-filament::link color="danger">Danger</x-filament::link>
```

---

## 🎯 Icon

```blade
<x-filament::link icon="heroicon-o-arrow-right">
    Selanjutnya
</x-filament::link>

<x-filament::link icon="heroicon-o-arrow-left" icon-position="before">
    Kembali
</x-filament::link>
```

---

## 💬 Tooltip

```blade
<x-filament::link tooltip="Lihat detail">
    Info
</x-filament::link>
```

---

## 🔢 Badge

```blade
<x-filament::link :badge="5">
    Notifikasi
</x-filament::link>
```
