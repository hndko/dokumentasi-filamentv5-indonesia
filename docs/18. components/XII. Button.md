# XII. Button 🔘

> **Sumber:** [https://filamentphp.com/docs/5.x/components/button](https://filamentphp.com/docs/5.x/components/button)

---

## 🤔 Apa itu Button?

Blade component untuk tombol.

---

## 🚀 Penggunaan

```blade
<x-filament::button>
    Klik Saya
</x-filament::button>
```

---

## 🔗 Anchor Link

```blade
<x-filament::button href="/posts">
    Lihat Posts
</x-filament::button>

{{-- New tab --}}
<x-filament::button href="/posts" target="_blank">
    Buka di Tab Baru
</x-filament::button>
```

---

## 📏 Size

```blade
<x-filament::button size="xs">Extra Small</x-filament::button>
<x-filament::button size="sm">Small</x-filament::button>
<x-filament::button size="md">Medium</x-filament::button>
<x-filament::button size="lg">Large</x-filament::button>
<x-filament::button size="xl">Extra Large</x-filament::button>
```

---

## 🎨 Color

```blade
<x-filament::button color="primary">Primary</x-filament::button>
<x-filament::button color="success">Success</x-filament::button>
<x-filament::button color="warning">Warning</x-filament::button>
<x-filament::button color="danger">Danger</x-filament::button>
<x-filament::button color="info">Info</x-filament::button>
<x-filament::button color="gray">Gray</x-filament::button>
```

---

## 🎯 Icon

```blade
<x-filament::button icon="heroicon-o-plus">
    Tambah
</x-filament::button>

{{-- Icon di kanan --}}
<x-filament::button icon="heroicon-o-arrow-right" icon-position="after">
    Lanjut
</x-filament::button>
```

---

## 📝 Outlined

```blade
<x-filament::button outlined>
    Outlined Button
</x-filament::button>
```

---

## 💬 Tooltip

```blade
<x-filament::button tooltip="Klik untuk menyimpan">
    Simpan
</x-filament::button>
```

---

## 🔢 Badge

```blade
<x-filament::button :badge="5">
    Notifikasi
</x-filament::button>
```
