# XVII. Icon Button 🔘

> **Sumber:** [https://filamentphp.com/docs/5.x/components/icon-button](https://filamentphp.com/docs/5.x/components/icon-button)

---

## 🤔 Apa itu Icon Button?

Tombol yang hanya menampilkan icon.

---

## 🚀 Penggunaan

```blade
<x-filament::icon-button
    icon="heroicon-o-pencil"
    label="Edit"
/>
```

---

## 🔗 Anchor Link

```blade
<x-filament::icon-button
    icon="heroicon-o-arrow-right"
    href="/next"
/>
```

---

## 📏 Size

```blade
<x-filament::icon-button size="sm" icon="heroicon-o-plus" />
<x-filament::icon-button size="md" icon="heroicon-o-plus" />
<x-filament::icon-button size="lg" icon="heroicon-o-plus" />
```

---

## 🎨 Color

```blade
<x-filament::icon-button icon="heroicon-o-trash" color="danger" />
<x-filament::icon-button icon="heroicon-o-check" color="success" />
```

---

## 💬 Tooltip

```blade
<x-filament::icon-button
    icon="heroicon-o-trash"
    tooltip="Hapus item"
/>
```

---

## 🔢 Badge

```blade
<x-filament::icon-button
    icon="heroicon-o-bell"
    :badge="3"
/>
```
