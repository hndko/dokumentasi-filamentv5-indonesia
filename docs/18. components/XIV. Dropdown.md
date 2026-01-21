# XIV. Dropdown 📋

> **Sumber:** [https://filamentphp.com/docs/5.x/components/dropdown](https://filamentphp.com/docs/5.x/components/dropdown)

---

## 🤔 Apa itu Dropdown?

Blade component untuk dropdown menu.

---

## 🚀 Penggunaan

```blade
<x-filament::dropdown>
    <x-slot name="trigger">
        <x-filament::button>
            Menu
        </x-filament::button>
    </x-slot>

    <x-filament::dropdown.list>
        <x-filament::dropdown.item>
            Item 1
        </x-filament::dropdown.item>
        <x-filament::dropdown.item>
            Item 2
        </x-filament::dropdown.item>
    </x-filament::dropdown.list>
</x-filament::dropdown>
```

---

## 🔗 Anchor Link

```blade
<x-filament::dropdown.item href="/profile">
    Profil
</x-filament::dropdown.item>
```

---

## 🎨 Color

```blade
<x-filament::dropdown.item color="danger">
    Hapus
</x-filament::dropdown.item>
```

---

## 🎯 Icon

```blade
<x-filament::dropdown.item icon="heroicon-o-pencil">
    Edit
</x-filament::dropdown.item>

<x-filament::dropdown.item icon="heroicon-o-trash" icon-color="danger">
    Hapus
</x-filament::dropdown.item>
```

---

## 🖼️ Image

```blade
<x-filament::dropdown.item
    :image="$user->avatar_url"
>
    {{ $user->name }}
</x-filament::dropdown.item>
```

---

## 🔢 Badge

```blade
<x-filament::dropdown.item :badge="5">
    Notifikasi
</x-filament::dropdown.item>
```

---

## 📍 Placement

```blade
<x-filament::dropdown placement="bottom-end">
    ...
</x-filament::dropdown>
```

---

## 📏 Width

```blade
<x-filament::dropdown width="md">
    ...
</x-filament::dropdown>

{{-- xs, sm, md, lg, xl, 2xl, ... --}}
```

---

## 📏 Max Height

```blade
<x-filament::dropdown max-height="300px">
    ...
</x-filament::dropdown>
```
