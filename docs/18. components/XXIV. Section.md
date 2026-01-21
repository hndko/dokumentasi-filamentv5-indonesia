# XXIV. Section 📦

> **Sumber:** [https://filamentphp.com/docs/5.x/components/section](https://filamentphp.com/docs/5.x/components/section)

---

## 🤔 Apa itu Section?

Container dengan heading dan styling.

---

## 🚀 Penggunaan

```blade
<x-filament::section heading="Informasi Dasar">
    Konten di sini...
</x-filament::section>
```

---

## 📝 Description

```blade
<x-filament::section
    heading="Pengaturan"
    description="Kelola pengaturan akun Anda."
>
    ...
</x-filament::section>
```

---

## 🎯 Icon

```blade
<x-filament::section
    heading="Keamanan"
    icon="heroicon-o-shield-check"
>
    ...
</x-filament::section>
```

### Icon Color & Size

```blade
<x-filament::section
    icon="heroicon-o-cog"
    icon-color="primary"
    icon-size="lg"
>
    ...
</x-filament::section>
```

---

## 📦 Header End Content

```blade
<x-filament::section heading="Posts">
    <x-slot name="headerEnd">
        <x-filament::button size="sm">
            Tambah
        </x-filament::button>
    </x-slot>

    ...
</x-filament::section>
```

---

## 📂 Collapsible

```blade
<x-filament::section heading="Detail" collapsible>
    ...
</x-filament::section>

{{-- Collapsed by default --}}
<x-filament::section heading="Detail" collapsible collapsed>
    ...
</x-filament::section>
```

### Persist State

```blade
<x-filament::section
    heading="Detail"
    collapsible
    persist-collapsed
    id="detail-section"
>
    ...
</x-filament::section>
```

---

## 📍 Aside Layout

```blade
<x-filament::section heading="Info" aside>
    ...
</x-filament::section>

{{-- Content before header --}}
<x-filament::section heading="Info" aside content-before>
    ...
</x-filament::section>
```
