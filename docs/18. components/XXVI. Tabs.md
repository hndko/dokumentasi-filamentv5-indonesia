# XXVI. Tabs 📑

> **Sumber:** [https://filamentphp.com/docs/5.x/components/tabs](https://filamentphp.com/docs/5.x/components/tabs)

---

## 🤔 Apa itu Tabs?

Tab navigation component.

---

## 🚀 Penggunaan

```blade
<x-filament::tabs>
    <x-filament::tabs.item active>Tab 1</x-filament::tabs.item>
    <x-filament::tabs.item>Tab 2</x-filament::tabs.item>
    <x-filament::tabs.item>Tab 3</x-filament::tabs.item>
</x-filament::tabs>
```

---

## ✅ Active State

```blade
<x-filament::tabs.item :active="$activeTab === 'tab1'">
    Tab 1
</x-filament::tabs.item>
```

---

## 🎯 Icon

```blade
<x-filament::tabs.item icon="heroicon-o-home">
    Home
</x-filament::tabs.item>

<x-filament::tabs.item icon="heroicon-o-cog" icon-position="after">
    Settings
</x-filament::tabs.item>
```

---

## 🔢 Badge

```blade
<x-filament::tabs.item :badge="5">
    Notifikasi
</x-filament::tabs.item>
```

---

## 🔗 Anchor Link

```blade
<x-filament::tabs.item href="/posts">
    Posts
</x-filament::tabs.item>
```

---

## 📍 Vertical Tabs

```blade
<x-filament::tabs vertical>
    <x-filament::tabs.item>Tab 1</x-filament::tabs.item>
    <x-filament::tabs.item>Tab 2</x-filament::tabs.item>
</x-filament::tabs>
```
